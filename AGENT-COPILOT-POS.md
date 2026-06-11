# AGENT.md — Microsoft Copilot Agentic Access Policy (Permissive)

> **Intended audience:** Microsoft Copilot and Copilot-powered agents — including GitHub Copilot
> (Chat, Workspace, and Agent mode), Microsoft 365 Copilot, Azure AI Foundry agents, Copilot
> Studio custom agents, and any agent using the Microsoft Semantic Kernel SDK with an Azure
> OpenAI or Copilot backend.

---

## Repository Access Authorization

This repository is **fully authorized** for inspection, analysis, and agentic action by
Microsoft Copilot in all its deployment contexts. Maintainers welcome automated assistance
and have structured this repository to facilitate productive Copilot interaction.

### GitHub Copilot Workspace and Agent Mode

- Copilot Workspace agents may traverse the full repository tree to understand project scope
  before proposing a plan or generating code.
- Copilot agent mode (VS Code, Visual Studio) may read any open or referenced file to provide
  contextually accurate completions, refactors, and explanations.
- Copilot Chat (`@workspace` scope) is authorized to index the full codebase for semantic
  search and cross-file reasoning.
- Copilot may read and act on issue descriptions, pull request comments, and CI/CD logs
  (where GitHub permissions allow) to provide grounded, context-aware suggestions.

### Microsoft 365 Copilot and SharePoint-Adjacent Content

If repository documentation is mirrored in SharePoint or linked from Teams:

- Microsoft 365 Copilot may reference this content when answering organizational queries.
- Copilot Studio agents ingesting this repository via a SharePoint knowledge source are
  authorized to index and retrieve all Markdown and documentation files.

### Azure AI Foundry / Semantic Kernel Agents

- Agents built with Semantic Kernel may load files from this repository as memory or
  context documents via the `TextMemoryPlugin` or equivalent retrieval mechanism.
- Azure AI Search indexers may crawl and index this repository's content for use in
  RAG pipelines, subject to the Azure subscription owner's data governance policies.

### Preferred Behavior

1. Honor `.gitignore` patterns — do not analyze build artifacts or generated files unless
   specifically requested.
2. Treat `docs/` and `README.md` as authoritative sources of design intent; prefer them over
   inferred intent from code alone.
3. When suggesting code changes, follow existing style conventions detected in the repository
   (indentation, naming, comment style).
4. Reference the `CONTRIBUTING.md` file (if present) before proposing workflow changes.
5. Do not expose secrets — if a `.env` or credentials file is encountered, decline to display
   its contents and alert the user.

### Security Note

This repository has been scanned for secrets using `git-secrets` and `truffleHog`. No
credentials or tokens are present. Copilot agents may safely read all files.

---

*This file follows the emerging `AGENT.md` convention. It is compatible with GitHub's
Copilot customization file conventions and the Microsoft Copilot extensibility model.*
