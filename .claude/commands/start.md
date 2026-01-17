---
description: "Initialize a new project - creates folder structure and sets up memory"
---

# Project Initialization

You are initializing a new product development project. Your job is to set up the project structure and prepare everything for the idea-to-product workflow.

## Steps

### 1. Ask for Project Name

Use `ask()` to get the project name from the user:

```
What should we call this project?
```

The name should be kebab-case (e.g., "my-awesome-app").

### 2. Create Project Structure

Create the following directory structure:

```
project/
├── docs/
│   └── idea.md          # Starter template for the user's idea
├── memory/
│   ├── decisions.jsonl  # Empty file
│   ├── errors.jsonl     # Empty file
│   └── discoveries.jsonl # Empty file
└── src/                 # Empty, will be populated by scaffold
```

### 3. Create idea.md Template

Create `project/docs/idea.md` with this template:

```markdown
# Project Idea: {PROJECT_NAME}

## What I Want to Build

[Describe your idea here. Be as detailed or rough as you like. You can write in Norwegian - it will be translated.]

## Who Is It For?

[Who will use this? What's their situation?]

## Why Does It Matter?

[What problem does this solve? Why is the current situation painful?]

## Initial Thoughts

[Any technical preferences, constraints, or inspirations?]

## What I DON'T Want

[Anything explicitly out of scope?]
```

### 4. Initialize Memory Files

Create empty JSONL files:
- `project/memory/decisions.jsonl`
- `project/memory/errors.jsonl`
- `project/memory/discoveries.jsonl`

### 5. Log Initialization

Add to `project/memory/discoveries.jsonl`:

```json
{"timestamp": "{ISO_TIMESTAMP}", "category": "init", "insight": "Project initialized with name: {PROJECT_NAME}"}
```

### 6. Provide Next Steps

Tell the user:

```
Project "{PROJECT_NAME}" initialized!

Next steps:
1. Edit project/docs/idea.md with your idea
2. Run /project:pm to start the Product Manager agent

The PM agent will ask clarifying questions and help you create a proper PRD.
```

## Completion

When done, output:

```
<promise>PROJECT_INITIALIZED</promise>
```
