# cortex-agent-toolkit

A Cortex Code CLI plugin for the full Snowflake Cortex Agent lifecycle.

## Install

```bash
cortex plugin install https://gitlab.com/joey.foley/cortex-agent-toolkit.git
```

## Skills

| Skill | Description | Use When |
|---|---|---|
| `cortex-agent-toolkit:cortex-agent-ddl` | Create/edit agents via SQL DDL | Building a new agent from scratch |
| `cortex-agent-toolkit:agent-evaluation` | Native Snowflake agent evaluations | Measuring agent quality |
| `cortex-agent-toolkit:agent-flag-tester` | 3-variant flag comparison | Testing EnableAgenticAnalyst/FastPath flags |
| `cortex-agent-toolkit:cortex-agent-optimization` | Iterative dev/test optimization loop | Improving an existing agent |
| `cortex-agent-toolkit:cortex-agent-flags` | Experimental flags reference | Looking up flag names/behavior |
| `cortex-agent-toolkit:query-cortex-agent` | Query via DATA_AGENT_RUN | Quick agent invocation from SQL |
| `cortex-agent-toolkit:agent-architect` | Multi-agent project framework | Building complex multi-agent systems |

## Recommended Workflow

```
cortex-agent-ddl (create agent)
  └── writes handoff.json
       ├── agent-flag-tester (compare flag variants)
       │   └── writes flag_sweep_baseline.json
       └── cortex-agent-optimization (iterative improvement)
            └── uses flag_sweep_baseline.json as starting point
```

## Cross-Plugin Reference

The `ontology-demo` plugin's cortex-accelerator skill routes its terminal step to `cortex-agent-toolkit:cortex-agent-optimization`. Both plugins work independently but compose well together.

## Configuration

### GitHub Org (for agent-architect)

Set the `GH_ORG` environment variable for agent-architect's repo creation:

```bash
export GH_ORG=sfc-gh-yourname
```

## Prerequisites

See [PREREQUISITES.md](./PREREQUISITES.md).
