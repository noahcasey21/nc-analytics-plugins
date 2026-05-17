# Spec-Driven Development

This repo uses spec-driven development via `.ai-dev/` knowledge files. These files are platform-agnostic and work with any AI agent system (Claude, GPT, Copilot, Gemini, etc.).

## `.ai-dev/` Files

- `ARCHITECTURE.md` — Technology choices, database selection, API conventions, testing strategy, observability patterns. Read this before making architecture decisions.
- `SECURITY.md` — Data classification, encryption, access controls, secrets management, AI/ML security policies. Read this before handling customer data or adding new storage.
- `LEGAL.md` — Data residency, retention policies, AI model constraints, third-party service requirements. Read this before changing data flows or adding vendors.
- `PLAN.md` — Spec template for implementation plans. All plans follow this structure.
- `SYSTEM_PROMPT.md` — Planning methodology and research guidelines. Contains the workflow and instructions for agents.

## Using Spec-Driven Development

### With Claude

Use the Claude integration example from this skill's `integration/claude/` directory:

```bash
# Option 1: Using the plan.sh wrapper
cp integration/claude/plan.sh bin/plan
chmod +x bin/plan
bin/plan "description of feature to plan"

# Option 2: Load .ai-dev/ files manually in Claude
# Paste .ai-dev/SYSTEM_PROMPT.md as your system prompt
# Include ARCHITECTURE.md, SECURITY.md, LEGAL.md in your context
```

### With GPT

Use the GPT integration example from this skill's `integration/gpt/` directory:

```bash
# Use OpenAI API with .ai-dev/ files as context
# See integration/gpt/README.md for examples
```

### With Copilot

Use the Copilot integration example from this skill's `integration/copilot/` directory:

```
@workspace .ai-dev/

Use .ai-dev/SYSTEM_PROMPT.md as methodology for planning...
```

### With Other AI Platforms

The `.ai-dev/` files are portable. Load them as context in any AI agent system:

1. Provide `.ai-dev/SYSTEM_PROMPT.md` as the planning methodology
2. Include `.ai-dev/ARCHITECTURE.md`, `SECURITY.md`, `LEGAL.md` as context
3. Use `.ai-dev/PLAN.md` as the output template

## Creating Implementation Plans

1. Load the relevant `.ai-dev/` files into your AI agent (see platform-specific examples above)
2. Describe the feature or change you want to plan
3. The agent will use SYSTEM_PROMPT.md methodology to research, analyze, and plan
4. Output follows the PLAN.md template

## Plan Review

The `.agents/` directory contains agent definitions for validating plans:

- `plan-review-agent.md` — Reviews plans against `.ai-dev/` standards. Run this after plan generation to validate.

## Further Reading

- See `integration/` directory for platform-specific setup guides
- See individual `.ai-dev/` files for specific conventions and policies
