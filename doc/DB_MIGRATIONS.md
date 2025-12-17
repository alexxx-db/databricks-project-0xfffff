# Database migrations (SQLite + Alembic)

This project uses **Alembic** migrations for the SQLite database (`workshop.db`).

SQLite can’t perform many `ALTER TABLE` operations directly, so Alembic is configured to use **batch mode** (“move and copy”) when needed; see the Alembic docs: https://alembic.sqlalchemy.org/en/latest/batch.html

## Config files

- `alembic.ini`: minimal file required by Alembic’s CLI (must contain an `[alembic]` section).
- `pyproject.toml`: contains project-level tooling config; Alembic itself still needs `alembic.ini` for CLI config discovery.

## Commands (recommended via `just`)

- Apply migrations / create DB if missing:
  - `just db-bootstrap`

- Apply pending migrations:
  - `just db-upgrade`

- One-time: mark an existing pre-Alembic DB as up-to-date (baseline):
  - `just db-stamp`

- Create a new migration after editing models in `server/database.py`:
  - `just db-revision message="describe change"`

## Development

`just api-dev`, `just api`, and `just dev` automatically run `just db-bootstrap` before starting the server, so the schema is always current during development.

## Deploy

Use `just deploy` to run DB bootstrap, build the UI, and then call `./deploy.sh`.


