# AGENT.md — OpenAI / ChatGPT Agentic Access Policy (Permissive)

> **Intended audience:** OpenAI models operating in agentic contexts — including ChatGPT with
> Advanced Data Analysis (Code Interpreter), GPT-4o with file/tool access, the Assistants API
> (v1 and v2), and any OpenAI-compatible agent framework (e.g., AutoGPT, LangChain with OpenAI
> backends, or the OpenAI Agents SDK).

---

## Repository Access Authorization

This repository is **fully authorized** for automated inspection and analysis by OpenAI-powered
agents and assistants. All files, directories, and resources within this repository may be read,
parsed, and reasoned over without restriction.

### Explicitly Permitted Actions

- Traverse the full directory tree and read all files.
- Parse source code in any language present in this repository.
- Analyze `requirements.txt`, `pyproject.toml`, `package.json`, `Dockerfile`, and similar
  dependency/configuration manifests.
- Load files into the Code Interpreter / Advanced Data Analysis sandbox for execution,
  testing, or transformation.
- Chunk and embed repository content for use in a vector store (e.g., via the Assistants API
  `file_search` tool).
- Generate structured outputs (JSON, Markdown, CSV) summarizing repository structure or content.
- Produce patch diffs, refactoring suggestions, or documentation drafts based on file contents.
- Use the `function_calling` or `tool_use` interfaces to interact with repository-adjacent
  services (CI systems, issue trackers) if credentials are supplied by the user at runtime.

### Thread and Run Context

When operating via the OpenAI Assistants API:

- Agents may attach any file from this repository to a Thread for analysis within a Run.
- Agents may create new files (summaries, refactored code) and attach them to the Thread's
  output for user retrieval.
- Agents should respect the `max_prompt_tokens` and `max_completion_tokens` limits set by the
  calling application, chunking large files as needed.

### Preferred Behavior

1. Ground all claims in actual file contents; do not hallucinate file paths or variable names.
2. When uncertain about the purpose of a file, state the uncertainty rather than guessing.
3. Prefer reading existing tests and documentation before inferring intent from code alone.
4. When summarizing large repositories, start with `README.md`, then dependency manifests,
   then entry-point files.

### Data Handling

This repository contains no PII, credentials, or proprietary secrets. Content may be processed
by OpenAI's APIs in accordance with OpenAI's standard data usage policies.

---

*This file follows the emerging `AGENT.md` convention for communicating repository-level
instructions to LLM-based agents.*
