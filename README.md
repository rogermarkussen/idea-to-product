# Idea to Product

A starter kit for transforming raw ideas into production-ready code using AI-assisted development with Claude Code.

## The Ralph Wiggum Loop

<img src="https://upload.wikimedia.org/wikipedia/en/1/1f/Ralph_Wiggum.png" alt="Ralph Wiggum" width="150" align="right" />

This project uses the **Ralph Wiggum Loop** technique for autonomous AI development - named after the Simpsons character who famously says *"I'm helping!"*

The philosophy: Start with human oversight (HITL), let the AI make predictable mistakes, learn from them via persistent memory, and gradually transition to autonomous operation.

> "Deterministically bad" - Errors are predictable and informative. Use them to tune prompts.

**Key principles:**
- Fresh context per iteration (no context window bloat)
- State persisted in files and git (not AI memory)
- Verification via tests and linting (not trust)
- HITL early, autonomous later

## What This Does

This repository provides a structured workflow that takes you from a rough idea to an autonomous development loop:

1. **Idea** → Write your raw concept (in any language)
2. **PRD** → AI helps you clarify and structure it into a proper Product Requirements Document
3. **Technical Spec** → AI guides you through architecture decisions
4. **Scaffold** → Generate minimal project structure for your chosen stack
5. **Loop** → Set up autonomous development with human oversight that gradually fades

## Quick Start

```bash
# 1. Clone this repo
git clone https://github.com/rogermarkussen/idea-to-product.git my-new-product
cd my-new-product

# 2. Start Claude Code
claude

# 3. Initialize your project
/project:start

# 4. Write your idea in project/docs/idea.md, then:
/project:pm

# 5. Continue through the workflow...
/project:architect
/project:scaffold
/project:loop
```

## Commands

| Command | Description |
|---------|-------------|
| `/project:start` | Initialize project structure, set project name |
| `/project:pm` | Run Product Manager agent - turns idea into PRD |
| `/project:architect` | Run Architect agent - creates technical specification |
| `/project:scaffold` | Generate minimal code structure based on tech choices |
| `/project:loop` | Set up autonomous development loop |

## Workflow Details

### Phase 1: Initialization (`/project:start`)
- Creates the `project/` directory structure
- Sets up memory files for learning across iterations
- Prompts you for a project name

### Phase 2: Product Definition (`/project:pm`)
- Reads your raw idea from `project/docs/idea.md`
- Asks 3-5 clarifying questions to understand the problem
- Produces a structured PRD in `project/docs/prd.md`
- You can write in Norwegian - output will be in English

### Phase 3: Technical Architecture (`/project:architect`)
- Reads the PRD
- Asks about technology choices (stack, database, auth, etc.)
- Produces technical specification in `project/docs/technical-spec.md`
- All decisions are logged to `project/memory/decisions.jsonl`

### Phase 4: Code Scaffolding (`/project:scaffold`)
- Generates minimal project structure based on your tech choices
- Supports TypeScript and Python
- Creates only config files and folder structure - no boilerplate code

### Phase 5: Development Loop (`/project:loop`)
- Sets up an autonomous development loop
- First 2-3 iterations have full human oversight (HITL)
- Gradually transitions to autonomous operation
- Loop learns from errors via the memory system

## Project Structure After Setup

```
my-new-product/
├── project/
│   ├── docs/
│   │   ├── idea.md              # Your raw idea
│   │   ├── prd.md               # Generated PRD
│   │   └── technical-spec.md    # Generated tech spec
│   ├── memory/
│   │   ├── decisions.jsonl      # Architecture decisions
│   │   ├── errors.jsonl         # Errors and fixes
│   │   └── discoveries.jsonl    # Learnings
│   └── src/                     # Your scaffolded code
├── templates/                   # (You can delete after scaffolding)
├── .claude/
└── ...
```

## Supported Stacks

### TypeScript
- **Web App**: React/Next.js frontend + Express/Fastify backend
- **API**: REST/GraphQL backend only
- **CLI**: Command-line tool

### Python
- **Web App**: FastAPI/Flask backend + optional frontend
- **API**: REST/GraphQL backend only
- **CLI**: Command-line tool

## Memory System

The AI learns across iterations via JSONL files:

```jsonl
// decisions.jsonl
{"timestamp": "2024-01-15T10:00:00Z", "domain": "database", "decision": "PostgreSQL", "reasoning": "Need relational queries and ACID compliance"}

// errors.jsonl
{"timestamp": "2024-01-15T11:30:00Z", "error": "Connection timeout", "fix": "Added retry logic", "resolved": true}

// discoveries.jsonl
{"timestamp": "2024-01-15T12:00:00Z", "category": "performance", "insight": "Batch inserts 10x faster than individual"}
```

## Tips

- **Be specific in your idea**: The more context you provide, the better the PRD
- **Answer questions thoughtfully**: The PM agent's questions help shape the product
- **Review the Review Guides**: Each agent tells you what to look for before approving
- **Trust but verify**: Check the first few loop iterations carefully

## License

MIT
