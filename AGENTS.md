# AGENTS.md

Guidance for agents working in this repository.

## Snowflake environment

| Setting   | Value              |
| --------- | ------------------ |
| Database  | `DEMO_DB`          |
| Schema    | `TPCH_TRANSFORMED` |
| Warehouse | `DEMO_WH`          |

## Source data

Raw data comes from `SNOWFLAKE_SAMPLE_DATA.TPCH_SF1`.

All raw tables must be referenced through `dbt/models/_sources.yml` using
`{{ source('tpch', '<table>') }}`. Never hard-code `SNOWFLAKE_SAMPLE_DATA` or
`TPCH_SF1` in a model. If a raw table is not yet declared, add it to
`_sources.yml` first.

## dbt commands

Build the whole project:

```bash
dbt build --project-dir dbt/
```

Build a single model:

```bash
dbt build --select <model_name> --project-dir dbt/
```

## Conventions

- Model files use `snake_case` (e.g. `customer_order_summary.sql`).

## Git workflow

- Feature branches follow the pattern `feature/<description>`.
- A pull request is required before merging to `main`; do not commit directly to `main`.

## Tooling

This project uses CoCo Desktop. Do not use the `cortex` CLI command.
