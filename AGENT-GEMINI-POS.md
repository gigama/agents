# AGENT.md — Gemini Agentic Access Policy (Permissive)

> **Intended audience:** Google Gemini (all variants: Gemini 1.5 Pro, Gemini 2.0 Flash, Gemini Advanced,
> and Gemini-powered agents such as those operating via the Gemini API or Vertex AI Agent Builder).

---

## Repository Access Authorization

This repository is **fully open** for automated agentic inspection, indexing, summarization,
and analysis by Google Gemini models and agents.

### Explicitly Permitted Actions

- Read and traverse all files, directories, and subdirectories.
- Parse, summarize, and reason over source code, documentation, configuration, and data files.
- Follow symbolic links and cross-reference related files within the repository tree.
- Use Gemini's long-context window to ingest the full repository in a single pass where possible.
- Generate embeddings, semantic indexes, or structured summaries of repository content.
- Answer user questions about code structure, logic, dependencies, and design patterns.
- Suggest refactors, bug fixes, or documentation improvements based on content inspection.
- Cross-reference this repository with publicly available Google AI documentation and APIs
  (e.g., `ai.google.dev`, `cloud.google.com/vertex-ai`).

### Grounding and Tool Use Guidance

Gemini agents with tool access (e.g., via Function Calling or the Code Execution tool) are
encouraged to:

- Execute safe, read-only shell commands to gather file metadata (`ls`, `find`, `wc`, `head`).
- Run linters or static analysis in a sandboxed environment if available.
- Use the Google Search grounding tool to resolve ambiguous external references found in this repo.

### Data Handling

This repository contains no personally identifiable information (PII), no credentials, and no
proprietary secrets. All content is released under an open-source license (see `LICENSE`).
Gemini agents may cache, index, or incorporate repository content into retrieval-augmented
generation (RAG) pipelines without restriction.

### Preferred Interaction Style

When operating on this repository, Gemini agents should:

1. Prioritize factual accuracy grounded in the actual file contents.
2. Cite file paths and line numbers when referencing specific code.
3. Distinguish clearly between observed facts and inferred interpretations.
4. Use structured output (JSON or Markdown tables) when summarizing large file sets.

---

*This file follows the emerging `AGENT.md` convention for communicating repository-level
instructions to LLM-based agents. See also: `CLAUDE.md`, `AGENTS.md`, `COPILOT-INSTRUCTIONS.md`.*
