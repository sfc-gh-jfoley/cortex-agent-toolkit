# cortex-agent-toolkit

A Cortex Code CLI plugin for the full Snowflake Cortex Agent lifecycle.

## Install

```bash
cortex plugin install sfc-gh-jfoley/cortex-agent-toolkit
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

- The `ontology-demo` plugin's cortex-accelerator skill routes its terminal step to `cortex-agent-toolkit:cortex-agent-optimization`. Both plugins work independently but compose well together.
- For multi-agent project orchestration (building apps, demos, etc.), see the `cortex-architect-builder` plugin.

## Prerequisites

See [PREREQUISITES.md](./PREREQUISITES.md).
