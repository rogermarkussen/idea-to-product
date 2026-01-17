# Python Scaffold Templates

The `/project:scaffold` command generates minimal Python project structures.

## Web App / API

```
project/src/
├── pyproject.toml
├── requirements.txt
├── .gitignore
├── .env.example
├── src/
│   └── {project_name}/
│       ├── __init__.py
│       ├── main.py
│       ├── routes/
│       ├── models/
│       ├── services/
│       └── utils/
└── tests/
```

## CLI

```
project/src/
├── pyproject.toml
├── requirements.txt
├── .gitignore
├── src/
│   └── {project_name}/
│       ├── __init__.py
│       ├── __main__.py
│       ├── commands/
│       └── utils/
└── tests/
```

## Default Dependencies

```toml
[project]
requires-python = ">=3.11"
dependencies = []

[project.optional-dependencies]
dev = [
    "pytest>=7.0.0",
    "ruff>=0.1.0",
]
```
