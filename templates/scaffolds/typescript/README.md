# TypeScript Scaffold Templates

The `/project:scaffold` command generates minimal TypeScript project structures.

## Web App

```
project/src/
├── package.json
├── tsconfig.json
├── .gitignore
├── .env.example
├── src/
│   ├── app/              # Frontend
│   ├── server/
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── services/
│   │   └── models/
│   └── shared/
└── tests/
```

## API Only

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

## CLI

```
project/src/
├── package.json
├── tsconfig.json
├── .gitignore
├── src/
│   ├── commands/
│   ├── utils/
│   └── index.ts
└── tests/
```

## Default Dependencies

```json
{
  "devDependencies": {
    "typescript": "^5.0.0",
    "tsx": "^4.0.0",
    "vitest": "^1.0.0",
    "@types/node": "^20.0.0"
  }
}
```
