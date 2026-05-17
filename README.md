# AI Tooling

Platform-agnostic AI skills and tools. These skills work with Claude, GPT, Copilot, Gemini, and other AI agent systems via the [Agent Skills](https://agentskills.io) standard.

Previously: Claude Code plugins by Abnormal AI.

## Plugins

### spec-tool

**Platform-agnostic** bootstrap tool for spec-driven development. Works with Claude, GPT, Copilot, and other AI agents.

Generates `.ai-dev/` knowledge files (ARCHITECTURE.md, SECURITY.md, LEGAL.md, PLAN.md) and a plan review agent. These files work with any AI system:

```
/build-spec-tool
```

This tool will:
1. Explore your codebase to understand tech stack, architecture, and conventions
2. Optionally interview you about security policies, compliance, and process
3. Generate customized `.ai-dev/` files reflecting your actual patterns
4. Create a plan review agent that validates plans against your standards
5. Provide platform-specific integration guidance for your AI tool

**See [plugins/spec-tool/skills/build-spec-tool/integration/](./plugins/spec-tool/skills/build-spec-tool/integration/) for platform-specific setup guides:**

- **Claude** — Use with Claude CLI or Copilot Chat
- **GPT** — Use with OpenAI API
- **Copilot** — Use with GitHub Copilot
- **Other** — Add your platform!
