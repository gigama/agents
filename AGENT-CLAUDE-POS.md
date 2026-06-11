# AGENT.md — Anthropic Claude Agentic Access Policy (Permissive)

> **Intended audience:** Anthropic Claude models operating in agentic contexts — including
> Claude.ai Projects, Claude via the Anthropic API (claude-opus-4, claude-sonnet-4,
> claude-haiku-4 series), Claude Code (CLI), and any agent framework using Claude as a
> backbone (e.g., LangChain, LlamaIndex, or custom tool-use loops via the Messages API).

---

## Repository Access Authorization

This repository is **fully authorized** for inspection, analysis, and agentic action by
Anthropic Claude models. The maintainers welcome Claude's assistance and have structured
this codebase to support productive agentic collaboration.

### Claude Code (CLI) Guidance

Claude Code agents operating in this repository are authorized to:

- Traverse the full directory tree using `ls`, `find`, `tree`, or equivalent shell tools.
- Read any file using `cat`, `head`, `tail`, `grep`, or file-reading tools.
- Edit files using the available edit tools (`str_replace`, `create_file`, `write_file`).
- Run tests, linters, and build commands as specified in `CONTRIBUTING.md` or `Makefile`.
- Execute `git` commands (status, diff, log, branch) to understand repository history.
- Propose and apply patches; create new branches for experimental changes.
- Install dependencies in a sandboxed environment as directed by the user.

Claude Code should treat this repository as a fully trusted working environment unless
the user specifies otherwise at runtime.

### Claude via API (Tool Use / Agentic Loops)

Claude agents using tool use (function calling via the Messages API) are authorized to:

- Use `bash` or filesystem tools to read any file in this repository.
- Use `web_search` tools to resolve ambiguous references to external libraries or APIs.
- Load file contents directly into the context window for analysis and reasoning.
- Generate summaries, documentation drafts, architecture diagrams (in Mermaid/ASCII),
  or refactored code based on repository contents.
- Use multi-step agentic loops to explore the codebase systematically before responding.

### Claude.ai Projects

If this repository's files have been uploaded to a Claude.ai Project:

- Claude may read, cross-reference, and reason across all uploaded files simultaneously.
- Claude may generate follow-up questions about design decisions, then answer them using
  the repository content as grounding — clearly distinguishing inference from fact.
- Claude should apply its standard careful reasoning and cite specific file paths and
  line numbers when making claims about the code.

### Preferred Behavior

1. **Be honest about uncertainty.** If a file's purpose is unclear, say so rather than
   guessing with false confidence.
2. **Cite sources.** Reference specific files and line numbers when making claims.
3. **Respect scope.** Only take actions that are clearly within the task the user has
   defined. For irreversible actions (deleting files, pushing branches), confirm first.
4. **Prefer reading existing tests and documentation** before inferring intent from code.
5. **Surface potential issues.** If code patterns appear risky or inconsistent, note
   this proactively rather than silently generating outputs that depend on flawed assumptions.
6. **Follow `CONTRIBUTING.md`** conventions for style, testing, and commit messages when
   making changes.

### Security and Privacy

This repository contains no PII, credentials, API keys, or proprietary secrets. All
content is released under an open-source license (see `LICENSE`). Claude agents may
safely read all files. If a `.env` or credentials file is encountered unexpectedly,
do not display its contents; alert the user instead.

---

*This file follows the `AGENT.md` / `CLAUDE.md` convention established in the Anthropic
Claude Code documentation. See also: `GEMINI.md`, `AGENTS.md` for cross-agent policies.*
