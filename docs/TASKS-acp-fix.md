# Tasks — ACP Fix v0.0.1

| id | status | description | issue | repo | branch | depends_on | blocks | agent | started_at | completed_at | estimate | used | notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ACP-001 | not-started | Trace ACP completion path: acpx runtime.ts → session manager → announce flow | TASKS:P1 | openclaw-fork | fix/acp-completion | | ACP-002 | | | | 15K | | |
| ACP-002 | not-started | Identify root cause and write minimal failing test reproducing #37869 | TASKS:P1 | openclaw-fork | fix/acp-completion | ACP-001 | ACP-003 | | | | 15K | | |
| ACP-003 | not-started | Implement fix in acpx runtime and/or session delivery bridge | TASKS:P1 | openclaw-fork | fix/acp-completion | ACP-002 | ACP-004 | | | | 20K | | |
| ACP-004 | not-started | Ensure all existing ACP tests pass + new test green, pnpm build clean | TASKS:P1 | openclaw-fork | fix/acp-completion | ACP-003 | ACP-005 | | | | 10K | | |
| ACP-005 | not-started | Push branch + open PR to openclaw/openclaw with issue reference | TASKS:P1 | openclaw-fork | fix/acp-completion | ACP-004 | | | | | 5K | | |
