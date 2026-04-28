# Beads Schema and Lifecycle

The hackathon project used [beads_rust](https://github.com/Dicklesworthstone/beads_rust)
(`br` CLI) as its task-tracking layer. This file documents the record
format and lifecycle conventions actually used during the case study, so
that the beads JSONL shipped in `../data/beads-jsonl.gz` is interpretable
without reading the upstream tool's documentation.

## File on disk

```
.beads/
├── beads.db          (sqlite — local index; not committed)
├── issues.jsonl      (authoritative state — committed to git)
├── config.yaml       (project config: prefix, defaults)
└── metadata.json     (project metadata)
```

Only `issues.jsonl` is part of the artifact bundle (gzipped). Each line
is one issue (one bead) as a single JSON object.

## Record format

```json
{
  "id": "bd-37n",
  "title": "Implement Infactory API client methods",
  "description": "Wrap the Infactory archive endpoints (...). Handle auth via X-API-Key. Surface a typed search() and getArticleContent() interface.",
  "status": "closed",
  "priority": 1,
  "issue_type": "task",
  "assignee": "ubuntu",
  "labels": ["api"],
  "created_at": "2026-01-31T19:41:39Z",
  "updated_at": "2026-01-31T20:00:08Z",
  "closed_at": "2026-01-31T20:00:08Z",
  "dependencies": [
    {"depends_on_id": "bd-2ab", "type": "blocks"}
  ],
  "acceptance_criteria": "- search(query, top_k) returns typed results\n- getArticleContent(id) returns full article\n- error states surface to UI",
  "notes": "Polled API twice during build — went down briefly at 19:50 and again at 21:55. Retry logic added.",
  "design": "",
  "external_ref": "",
  "compaction_level": 0
}
```

Field semantics:

| Field | Used for | Notes |
|---|---|---|
| `id` | Stable identifier | Format: `<prefix>-<3 chars>`. Hackathon used prefix `bd`; the paper repository uses `mp` (mise en place). |
| `title` | One-line subject | Convention: `<scope>: <action>` (e.g., `api: implement search`). |
| `description` | The "what + why" | Markdown body. The handoff to the next agent. |
| `status` | Lifecycle state | `open`, `in_progress`, `closed`, `deferred`. |
| `priority` | Numeric priority | `0` (critical) → `4` (backlog). P1 dominated the hackathon (38/68 = 56%). |
| `issue_type` | Kind | `task`, `feature`, `bug`, `epic`, `spec`, `decision`, `note`. |
| `dependencies[]` | Edges in the dep graph | `type` is `blocks` (this bead is blocked by `depends_on_id`) or `parent-child` (epic relationship). |
| `acceptance_criteria` | Pass/fail bullets | Used by the next agent (or future-self) to verify a close was warranted. |
| `notes` | Append-only working log | Investigation, partial findings, links. |
| `created_at` / `closed_at` | Timing | UTC ISO-8601. The paper's "median 5.9 min" closure metric is `closed_at - created_at` aggregated across hackathon-day beads. |

## Lifecycle states

```
                 ┌──────────────────────────────────┐
                 │                                  │
                 │                                  ▼
   br create →  open ─── br update --status ──→ in_progress ─── br close ──→ closed
                 │                                  ▲
                 │                                  │
                 └─── br defer ──→ deferred ────────┘
                                    (by br undefer)
```

- **`open`** — created but not yet started; visible to `br ready` if
  dependencies are satisfied.
- **`in_progress`** — claimed by an agent (atomic via `br update --claim`,
  which sets assignee + status in one operation).
- **`deferred`** — explicitly punted to a later cycle; hidden from
  `br ready`.
- **`closed`** — terminal. No reopens; create a successor bead instead.

The hackathon used `closed` as both "completed" and "superseded" — three
beads (bd-1bt, bd-1rb, bd-20d) closed as superseded with better-scoped
replacement beads created in the same minute. This is visible in the
shipped JSONL as a closure timestamp paired with another bead's creation.

## Dependency model

Beads form a DAG. Two relationship types:

- **`blocks`** — execution dependency. `br ready` filters out any bead
  whose `blocks` predecessors are not closed.
- **`parent-child`** — composition / epic relationship. A child can be
  worked even when the parent is open; closing all children makes the
  parent close-eligible.

The hackathon graph was deliberately shallow: maximum dependency depth
1, only three beads with explicit edges. This was a tradeoff. Deeper
chains capture more structure but require more upfront design work; in
a 3-hour build window the practitioner front-loaded structure into the
specification documents (in `../prompts/plans/`) instead of into the
bead graph.

## Why the JSONL format matters for agentic coding

The bead format has three properties that make it agent-friendly:

1. **Append-only-friendly.** New issues append a line; updates rewrite
   the line in place but the file is small enough (≈47 KB for 68 beads)
   that this is fine. Git diffs cleanly.
2. **No schema migrations.** New fields are added to the record as
   needed; old beads simply lack them. Any JSON parser can read any
   version.
3. **Greppable.** `grep '"status":"open"' issues.jsonl` works. Agents
   can answer "what's open?" without invoking a CLI or hitting an API.

This last property is the one that matters most: **the bead store is
directly readable by an agent that has filesystem access**, which means
the agent can self-orient on the project's state without an extra
toolchain.

## Hackathon-day usage stats (from the shipped JSONL)

| Metric | Value |
|---|---:|
| Total beads | 68 |
| Closed (hackathon-day) | 43 / 64 (67.2%) |
| Bug beads | 6 (all closed within 1.5 min on average) |
| Feature beads | 10 (9 closed) |
| Task beads | 52 (28 closed; rest were stretch goals) |
| Median time-to-close | 5.9 min |
| Largest parallel batch | 10 beads closed within 21 sec |
| Bead creation waves | 12 distinct waves over 3h 4m |

The full breakdown is in `../data/beads-metrics.md` and
`../data/bead-timestamps.md`.

## Reading the shipped JSONL

```bash
# Decompress
gunzip -c artifact/data/beads-jsonl.gz > /tmp/issues.jsonl

# Count beads by status
jq -r '.status' /tmp/issues.jsonl | sort | uniq -c

# Show all closed bugs
jq 'select(.issue_type == "bug" and .status == "closed") | {id, title, closed_at}' /tmp/issues.jsonl

# Show the dependency graph
jq -r '.dependencies[]? | "\(.depends_on_id) -> [parent of \($parent)]"' /tmp/issues.jsonl
```

## See also

- `workflow.md` for how beads fit into the three-phase methodology
- `../prompts/claude-md.md` for the project's full beads workflow
  documentation (committed to the hackathon repo as part of the agent
  contract)
- Upstream tool: <https://github.com/Dicklesworthstone/beads_rust>
