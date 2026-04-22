# Claude package — Senior UXUI/Product Design (Figma review)

## Contents
- `senior-uxui-product-designer.md`: subagent system prompt (Senior UXUI/Product Design) — output tiếng Việt.
- `rm-sale-crm-uiux-checklist.md`: UI/UX checklist (machine-readable) for Sale & CRM (RM banking).
- `rm-sale-crm-uiux-review-process.md`: review process (2 rounds, triage).
- `rm-sale-crm-uiux-issue-log-template.csv`: issue log template (CSV).

## How to use quickly (suggested)
1) In Claude (or any LLM), paste the content of:
   - `senior-uxui-product-designer.md`
   - plus `rm-sale-crm-uiux-checklist.md`
2) Then provide a Figma URL with `node-id` and say:
   - Scope: Section/Flow/Screen
   - Mode: Quick / Full / Section Audit
   - Persona/platform/environment (optional — if missing, the agent should ask).

## Notes
- This package assumes you can access Figma via MCP tools (or similar). If tools are unavailable, use Heuristic Mode and provide screenshots.
- Token/Style Debt can be audited via Figma Variables/Styles even without a token JSON source.

