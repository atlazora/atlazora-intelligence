# Atlazora Intelligence

`atlazora-intelligence` is the Python intelligence foundation for Atlazora.

## Boundary

The Go/PostgreSQL Core remains the authoritative transactional system.
Python in this repository must not own Core transactional truth.
Derived intelligence outputs must remain distinguishable from authoritative transactional data.
Shared executable API and event contracts remain owned by `atlazora-contracts` and must not be duplicated here.

W00-WU06 introduces no business intelligence feature, recommendation, ranking, scoring, fraud, analytics, production ML model, ML platform, orchestration platform, event broker, vector database, feature store, model registry, or CI/CD platform.

## Runtime and project layout

The foundation targets the Python 3.14 release series.
The locally verified W00-WU06 runtime is Python 3.14.4.

The repository uses:

- standard-library `venv`;
- `pip` inside the repository-local virtual environment;
- `pyproject.toml` for Python project metadata and tool configuration;
- a `src` package layout under `src/atlazora_intelligence`;
- `pytest` for tests;
- Ruff for lint/static-quality verification;
- mypy for Python type analysis.

Development dependencies are intentionally not exact-version pinned by W00-WU06.

## Local setup

From the repository root in PowerShell:

```powershell
py -3.14 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -e ".[dev]"
```

## Foundation verification

Verify the package import:

```powershell
python -c "import atlazora_intelligence; print(atlazora_intelligence.__name__)"
```

Expected output:

```text
atlazora_intelligence
```

This is the current foundation-level runtime verification path.
W00-WU06 introduces no long-running service, worker, CLI, or business-process entry point.

## Tests

```powershell
python -m pytest -q
```

## Ruff

```powershell
ruff check --no-cache src tests
```

## mypy

```powershell
python -m mypy src tests
```

The W00-WU06 mypy configuration intentionally remains minimal and targets Python 3.14.
Strict mode, plugins, and additional strictness options are not selected by this foundation.

## Configuration and secrets

W00-WU06 introduces no runtime configuration inputs, external-service credentials, database credentials, production credentials, application secrets, `.env` schema, configuration loader, or secret provider.

Therefore no configuration failure path is applicable to the current foundation.

Secrets and production credentials must not be committed.
Future configuration and credentials must be introduced and reviewed by the Work Unit that requires them.

## Logging and error handling

The current foundation has no long-running process, service, worker, external I/O integration, or business operation.

A logging framework and application error-handling layer are therefore not applicable to W00-WU06.
They become applicable when a later governed Work Unit introduces runtime behavior that requires them.

## Data and permissions

The current foundation reads no transactional data, connects to no production service or datastore, and requires no external permissions.

Future intelligence workloads must receive only the data and permissions required for their approved purpose.

## Generated local artifacts

Local generated artifacts excluded from Git include `.venv/`, Python bytecode and `__pycache__/`, `.pytest_cache/`, `.ruff_cache/`, `.mypy_cache/`, and `*.egg-info/`.
