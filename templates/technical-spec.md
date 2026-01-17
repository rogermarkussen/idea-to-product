# Technical Specification: {Project Name}

**Created:** {date}
**Based on:** project/docs/prd.md
**Version:** 1.0
**Status:** Draft

---

## System Architecture

### High-Level Diagram

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│    Frontend     │────▶│     Backend     │────▶│    Database     │
│   {tech}        │     │    {tech}       │     │    {tech}       │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                               │
                               ▼
                        ┌─────────────────┐
                        │ External APIs   │
                        └─────────────────┘
```

### Component Overview

| Component | Technology | Responsibility |
|-----------|------------|----------------|
| Frontend | {tech} | {responsibility} |
| Backend | {tech} | {responsibility} |
| Database | {tech} | {responsibility} |
| Auth | {tech} | {responsibility} |

---

## Tech Stack

### Decisions Made

```
✅ Language:     {choice}
✅ Framework:    {choice}
✅ Database:     {choice}
✅ Auth:         {choice}
✅ Deployment:   {choice}
```

All decisions logged in: `project/memory/decisions.jsonl`

### Dependencies

```json
{
  "core": [
    "{dependency 1}",
    "{dependency 2}"
  ],
  "dev": [
    "{dev dependency 1}",
    "{dev dependency 2}"
  ]
}
```

---

## Data Model

### Entity Relationship

```
User ||--o{ Entity : owns
Entity ||--|{ SubEntity : contains
```

### Entities

```typescript
interface User {
  id: string;
  email: string;
  created_at: Date;
  updated_at: Date;
}

interface Entity {
  id: string;
  user_id: string;
  name: string;
  // ...
}
```

### Database Schema

```sql
-- Users
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

-- Entities
CREATE TABLE entities (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id),
  name VARCHAR(255) NOT NULL
);
```

---

## API Design

### Authentication

```
Authorization: Bearer <token>
```

### Endpoints

| Method | Path | Auth | Description |
|--------|------|------|-------------|
| POST | /api/auth/register | No | Register user |
| POST | /api/auth/login | No | Login |
| GET | /api/entities | Yes | List entities |
| POST | /api/entities | Yes | Create entity |
| GET | /api/entities/:id | Yes | Get entity |
| PUT | /api/entities/:id | Yes | Update entity |
| DELETE | /api/entities/:id | Yes | Delete entity |

### Error Responses

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Human-readable message",
    "details": {}
  }
}
```

---

## Security

### Authentication
- Method: {JWT / Session / OAuth}
- Token lifetime: {duration}
- Refresh strategy: {strategy}

### Data Protection
- [ ] Passwords hashed with bcrypt (cost 12)
- [ ] Sensitive data encrypted at rest
- [ ] HTTPS only
- [ ] CORS limited to {domains}

### Input Validation
- All inputs validated server-side
- Parameterized queries (no SQL injection)
- Output encoding (no XSS)

---

## File Structure

```
project/src/
├── src/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── models/
│   ├── utils/
│   └── config/
├── tests/
│   ├── unit/
│   └── integration/
├── package.json
└── tsconfig.json
```

---

## Testing Strategy

### Test Pyramid

```
      /\
     /e2e\          ← Few critical user flows
    /──────\
   /integration\    ← API endpoints, DB queries
  /──────────────\
 /   unit tests   \ ← Business logic, utils
/────────────────────\
```

### Tools
- Unit: {test framework}
- Integration: {test framework}
- Coverage target: {percentage}%

---

## Deployment

### Environments

| Environment | URL | Purpose |
|-------------|-----|---------|
| Development | localhost:{port} | Local dev |
| Staging | {url} | Pre-prod testing |
| Production | {url} | Live |

### CI/CD

```yaml
on: push
jobs:
  test:    # Lint, unit tests, integration
  build:   # Build artifacts
  deploy:  # Deploy to environment
```

---

## Implementation Order

Based on dependencies and risk:

1. **Foundation** - Project setup, database, base models
2. **Auth** - User registration, login, middleware
3. **Core CRUD** - Main entity operations
4. **API** - REST endpoints
5. **Tests** - Unit and integration tests
6. **Polish** - Error handling, validation, edge cases

---

## References

- PRD: `project/docs/prd.md`
- Decisions: `project/memory/decisions.jsonl`

---

**Next Step:** Scaffold project with /project:scaffold
