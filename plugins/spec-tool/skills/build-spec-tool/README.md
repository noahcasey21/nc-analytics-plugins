# Build Spec Tool

[![Platform Agnostic](https://img.shields.io/badge/platform-agnostic-brightgreen)](./integration/)
[![Agent Skills](https://img.shields.io/badge/agent%20skills-compatible-blue)](https://agentskills.io)

Bootstrap any monorepo with spec-driven development infrastructure. Generate platform-agnostic knowledge files (`.ai-dev/`) that work with any AI agent system: Claude, GPT, Copilot, Gemini, and more.

## What It Does

This skill generates a complete spec-driven development setup:

```
.ai-dev/
├── ARCHITECTURE.md      # Tech stack, database choices, API patterns, testing strategy
├── SECURITY.md          # Data classification, encryption, secrets management, auth patterns
├── LEGAL.md             # Data residency, retention policies, compliance requirements
├── PLAN.md              # Template for creating implementation plans
└── SYSTEM_PROMPT.md     # Planning methodology and research guidelines

.agents/
└── plan-review-agent.md # Validates plans against standards

README.md               # Updated with spec-driven development guidance
```

## Key Features

✅ **Platform Agnostic** — Works with Claude, GPT, Copilot, Gemini, and any AI agent system  
✅ **Portable** — Generate once, use everywhere  
✅ **Structured** — Comprehensive discovery, interview, and generation workflow  
✅ **Validated** — Built-in plan review agent for quality assurance  
✅ **Well Documented** — Templates and guidelines for your entire team  

## Quick Start

### 1. Run the Skill

Invoke the skill in your agent:

```
/build-spec-tool

# Or with a specific description:
/build-spec-tool "Initialize spec-driven development for our API platform"
```

### 2. Follow the Workflow

The skill guides you through a 5-phase process:

1. **Discovery** — Analyze your codebase (tech stack, architecture, conventions)
2. **Interview** — Answer questions about your architecture, security, and legal requirements
3. **Generation** — Create customized `.ai-dev/` files reflecting your actual patterns
4. **Integration** — Get platform-specific guidance for your AI tool
5. **Validation** — Review and refine the generated files

### 3. Use With Your AI Platform

See [integration/](./integration/) for platform-specific guides:

- **Claude**: [integration/claude/](./integration/claude/) — Use with Claude CLI or Copilot Chat
- **GPT**: [integration/gpt/](./integration/gpt/) — Use with OpenAI API
- **Copilot**: [integration/copilot/](./integration/copilot/) — Use with GitHub Copilot
- **Other platforms**: [integration/README.md](./integration/README.md) — Add your platform!

## What You Get

### Spec-Driven Knowledge Base

All generated `.ai-dev/` files are **platform-agnostic**. Load them into any AI agent:

```
# Example: Planning a feature with Claude
claude --append-system-prompt "$(cat .ai-dev/SYSTEM_PROMPT.md .ai-dev/ARCHITECTURE.md .ai-dev/SECURITY.md .ai-dev/LEGAL.md)" \
  --user "Plan: add user authentication"
```

### Reusable Templates

- **PLAN.md** — Standardized template for all implementation plans
- **ARCHITECTURE.md** — Guidelines for tech decisions and patterns
- **SECURITY.md** — Data classification and security policies
- **LEGAL.md** — Compliance and legal requirements

### Plan Review Agent

The generated `.agents/plan-review-agent.md` validates plans against your standards:

1. Checks architecture compliance
2. Validates security considerations
3. Ensures legal/compliance requirements are met
4. Verifies feasibility (files exist, patterns match)

## Workflow Details

### Phase 1: Discovery (Parallel)

The skill analyzes your codebase:

- **Tech stack**: Languages, frameworks, build systems, CI/CD
- **Architecture**: Services, databases, APIs, event systems
- **Conventions**: Testing patterns, linting, PR templates, code ownership

Also collects existing documentation you want to incorporate.

### Phase 2: Interview (Optional)

5 focused rounds if you want to fill gaps:

1. **Architecture** — Language choices, databases, services, deployment
2. **Data & Multi-tenancy** — Tenant identification, residency, retention
3. **Security** — Data classification, auth patterns, secrets, encryption
4. **Legal/Compliance** — Regulated industries, AI/ML constraints, third-party requirements
5. **Process** — PR review, testing, deployment, feature flags

Each round shows draft content for feedback and iteration.

### Phase 3: Generation

Creates each `.ai-dev/` file:

1. **ARCHITECTURE.md** — Filled with your actual tech stack and patterns
2. **SECURITY.md** — Populated with your security policies and practices
3. **LEGAL.md** — Compiled from your legal/compliance requirements
4. **PLAN.md** — Customized with your test/lint/build commands
5. **SYSTEM_PROMPT.md** — Copied with your doc patterns and issue tracker

### Phase 4: Platform Integration

Provides guidance for using `.ai-dev/` with your AI platform:

- Links to platform-specific integration guides
- Instructions for loading `.ai-dev/` files as context
- Examples for starting planning sessions

### Phase 5: Review Agent Setup

Creates `.agents/plan-review-agent.md` for plan validation.

## After Bootstrap

Your repo now has spec-driven development set up:

```bash
# Review and refine the generated files
cat .ai-dev/ARCHITECTURE.md
cat .ai-dev/SECURITY.md
cat .ai-dev/LEGAL.md

# Commit everything
git add .ai-dev/ .agents/ README.md
git commit -m "Add spec-driven development infrastructure"

# Start planning with your AI agent
# See integration/ for platform-specific commands
```

## Platform Integration Examples

### Claude

```bash
# Option 1: Using provided script
cp integration/claude/plan.sh bin/plan
chmod +x bin/plan
bin/plan "add user authentication"

# Option 2: Manual (paste .ai-dev/SYSTEM_PROMPT.md as system prompt)
```

### GPT

```python
# Load .ai-dev/ files and pass to OpenAI API
client = OpenAI()
response = client.chat.completions.create(
    model="gpt-4",
    system_prompt=open(".ai-dev/SYSTEM_PROMPT.md").read(),
    messages=[{"role": "user", "content": "Plan: add user auth"}]
)
```

### Copilot

```
@workspace .ai-dev/SYSTEM_PROMPT.md

Plan: add user authentication
```

## Important Notes

### Accuracy Matters

The `.ai-dev/` files become your source of truth for all future planning. Only include:

- Content from **codebase analysis** (what we discovered)
- Content from **user-provided documentation** (what you gave us)
- Content from **your interview answers** (what you told us)

Never guess at security policies, compliance, or architecture details!

### No Overwriting

If `.ai-dev/` files already exist, the skill will show you a diff and ask how to merge.

### Customization Flexibility

- Edit any generated `.ai-dev/` file after generation
- Update VERIFICATION section in PLAN.md with your actual build commands
- Add platform-specific guidance to README.md
- Customize interview questions by editing this skill

## Project Structure

```
build-spec-tool/
├── SKILL.md                          # This skill definition (platform-agnostic)
├── README.md                         # This file
├── references/                       # Templates and examples
│   ├── architecture_template.md      # ARCHITECTURE.md template
│   ├── security_template.md          # SECURITY.md template
│   ├── legal_template.md             # LEGAL.md template
│   ├── plan_template.md              # PLAN.md template
│   ├── system_prompt.md              # Planning methodology
│   └── plan-review-agent.md          # Plan review agent template
├── assets/                           # Resources
│   ├── README_SNIPPET.md             # Snippet for generated repo README
│   └── claude_md_snippet.md          # Legacy: Claude-specific snippet
├── integration/                      # Platform-specific guides
│   ├── README.md                     # Integration overview
│   ├── claude/                       # Claude setup and scripts
│   ├── gpt/                          # GPT examples and guidance
│   └── copilot/                      # Copilot examples and guidance
└── scripts/                          # Utilities
    └── (None currently; integrations moved to integration/)
```

## Contributing

To add support for a new AI platform:

1. Create `integration/platform-name/README.md` with setup instructions
2. Add any platform-specific scripts or examples
3. Reference the skill's generated `.ai-dev/` files (they're platform-agnostic!)

See [integration/README.md](./integration/README.md) for details.

## FAQ

**Q: Can I use this with [my favorite AI tool]?**  
A: Yes! The `.ai-dev/` files are platform-agnostic. See [integration/README.md](./integration/README.md) to add your platform or submit a contribution.

**Q: What if I already have architecture/security/legal docs?**  
A: Tell the skill during Phase 1, and it will incorporate your existing docs.

**Q: Can I customize the templates?**  
A: Yes! Edit the reference templates in this skill, or edit generated files after creation. All `.ai-dev/` files are designed to be living documents.

**Q: How do I update `.ai-dev/` files as my project evolves?**  
A: Re-run the skill or manually edit the files. They're just markdown—version control them like any other docs.

**Q: Can multiple teams use this?**  
A: Absolutely. Generate `.ai-dev/` files for each team/service, or create one shared set for your entire org.

## License

This skill is open source and platform-agnostic. Use it with any AI agent system.

## Support

For issues, questions, or platform-specific guidance, see:
- Platform integration guides: [integration/](./integration/)
- Template references: [references/](./references/)
- Issue tracking: [GitHub Issues](https://github.com/)

---

**Ready to get started?** Run the skill in your agent and follow the workflow!
