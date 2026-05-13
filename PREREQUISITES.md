# Prerequisites

## Required

- **Cortex Code CLI** v1.0.70+
- **Snowflake connection** named `default` with:
  - Access to create/describe/alter agents
  - Access to SNOWFLAKE.CORTEX functions (DATA_AGENT_RUN, AGENT_RUN)
  - Ability to create evaluation datasets (SYSTEM$CREATE_EVALUATION_DATASET)
- **snow CLI** — used by agent-evaluation and agent-flag-tester for agent operations

## Optional

- **uv** (Python) — required by agent-evaluation scripts (invoke_agent.py, convert_eval_dataset.py)
- **gh CLI** (GitHub CLI) — required by agent-architect for repo creation
- **Glean MCP** — optional for cortex-agent-flags freshness checks (gracefully skipped if unavailable)

## Environment Variables

| Variable | Used By | Purpose |
|---|---|---|
| `GH_ORG` | agent-architect | GitHub org for `gh repo create` (default: prompts user) |
| `SNOWFLAKE_CONNECTION_NAME` | agent-evaluation | Connection for REST API calls |
