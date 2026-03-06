# PRD: ACP Session Completion Fix (Issue #37869)

**Version:** 0.0.1
**Status:** Approved
**Upstream Issue:** https://github.com/openclaw/openclaw/issues/37869

---

## Problem Statement

ACP sessions spawned via `sessions_spawn` with `runtime: "acp"` (specifically with `agentId: "opencode"`) are accepted but never close the loop:
- `sessions_spawn` returns `status: "accepted"` ✓
- Child `sessionKey` is created ✓
- `session_status` stays `running` forever ✗
- No completion callback / no announce to parent ✗
- `sessions_history` for child is empty ✗
- No `.acp-stream.jsonl` created ✗

## Investigation Scope

Focus areas based on issue report:
1. `extensions/acpx/src/runtime.ts` — the acpx runtime turn/close loop
2. `src/auto-reply/reply/session-delivery.ts` — the session delivery/announce path (recently changed per merge)
3. The bridge between acpx turn completion → OpenClaw session completion → parent announce

## Success Criteria

1. ACP sessions with `agentId: "opencode"` complete and announce to parent
2. `sessions_history` for child contains assistant output after completion
3. Stream log is created when applicable
4. Regression tests for ACP completion loop
5. PR submitted to `openclaw/openclaw` from `jetrich/openclaw`

## Constraints

- No behavior change for working agents (codex) unless clearly a bug
- Must work on Linux (primary) and macOS
- Branch from `upstream/main`, PR targets `openclaw/openclaw:main`
- ASSUMPTION: The bug may be in how acpx signals completion back to OpenClaw's session manager, or in how OpenClaw routes the completion event to the parent session's announce flow
