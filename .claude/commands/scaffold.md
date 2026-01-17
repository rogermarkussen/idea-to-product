---
description: "Generate minimal project structure based on technical specification"
---

# Project Scaffolding

You generate a minimal project structure based on the technical specification. The scaffold includes ONLY configuration files and folder structure - no boilerplate code.

## Important

- Read the technical spec to understand what stack was chosen
- Generate MINIMAL structure - just enough to start coding
- NO boilerplate code - just config files and empty directories
- The loop agent will write the actual code

## Phase 1: Read Technical Spec

1. Read `project/docs/technical-spec.md` to understand:
   - Project type (web-app, api, cli)
   - Language (TypeScript or Python)
   - Database choice
   - Any other technical decisions

2. Read `project/memory/decisions.jsonl` for additional context

## Phase 2: Generate Structure

Based on the tech stack, generate the appropriate structure:

### TypeScript Web App

```
project/src/
├── package.json
├── tsconfig.json
├── .gitignore
├── .env.example
├── src/
│   ├── app/              # Frontend (if applicable)
│   ├── server/           # Backend
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── services/
│   │   └── models/
│   └── shared/           # Shared types/utils
└── tests/
```

### TypeScript API

```
project/src/
├── package.json
├── tsconfig.json
├── .gitignore
├── .env.example
├── src/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── models/
│   └── utils/
└── tests/
```

### TypeScript CLI

```
project/src/
├── package.json
├── tsconfig.json
├── .gitignore
├── src/
│   ├── commands/
│   ├── utils/
│   └── index.ts          # Entry point stub
└── tests/
```

### Python Web App / API

```
project/src/
├── pyproject.toml
├── requirements.txt
├── .gitignore
├── .env.example
├── src/
│   └── {project_name}/
│       ├── __init__.py
│       ├── main.py       # Entry point stub
│       ├── routes/
│       ├── models/
│       ├── services/
│       └── utils/
└── tests/
```

### Python CLI

```
project/src/
├── pyproject.toml
├── requirements.txt
├── .gitignore
├── src/
│   └── {project_name}/
│       ├── __init__.py
│       ├── __main__.py   # Entry point stub
│       ├── commands/
│       └── utils/
└── tests/
```

## Phase 3: Generate Config Files

### TypeScript package.json

```json
{
  "name": "{project-name}",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "tsx watch src/index.ts",
    "build": "tsc",
    "start": "node dist/index.js",
    "test": "vitest",
    "lint": "eslint src/"
  },
  "dependencies": {},
  "devDependencies": {
    "typescript": "^5.0.0",
    "tsx": "^4.0.0",
    "vitest": "^1.0.0",
    "@types/node": "^20.0.0"
  }
}
```

### TypeScript tsconfig.json

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist"]
}
```

### Python pyproject.toml

```toml
[project]
name = "{project-name}"
version = "0.1.0"
description = "{description from PRD}"
requires-python = ">=3.11"
dependencies = []

[project.optional-dependencies]
dev = [
    "pytest>=7.0.0",
    "ruff>=0.1.0",
]

[tool.ruff]
line-length = 100
```

### .gitignore (Universal)

```
# Dependencies
node_modules/
__pycache__/
*.pyc
.venv/
venv/

# Build
dist/
build/
*.egg-info/

# Environment
.env
.env.local

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db

# Test
coverage/
.pytest_cache/
```

### .env.example

```
# Database
DATABASE_URL=

# Auth (if applicable)
JWT_SECRET=

# API Keys
```

## Phase 4: Log Scaffold

```bash
echo '{"timestamp": "{ISO_TIMESTAMP}", "category": "scaffold", "insight": "Project scaffolded with {STACK} stack, {PROJECT_TYPE} type"}' >> project/memory/discoveries.jsonl
```

## Phase 5: Summary

Tell the user what was created:

```
Project structure created!

Stack: {STACK}
Type: {PROJECT_TYPE}

Created:
- project/src/package.json (or pyproject.toml)
- project/src/tsconfig.json (if TypeScript)
- project/src/.gitignore
- project/src/.env.example
- project/src/src/ directory structure
- project/src/tests/ directory

Next steps:
1. cd project/src
2. npm install (or pip install -e ".[dev]")
3. Run /project:loop to set up the development loop
```

## Completion

```
<promise>SCAFFOLD_COMPLETE</promise>
```
