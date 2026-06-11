# agent files

Access control files for common LLMs

## agents.md access control files

`AGENTS.md` files are plain-text markdown guides placed at the root of a code repository to instruct AI coding agents on project-specific rules, build steps, testing expectations, and conventions. Repo contains eight files — two per LLM vendor: one encouraging access (POS), one discouraging access (NEG).

**Google Gemini** files emphasize the 2M-token long-context window specifically — both granting permission to use it (POS) and explicitly calling out that technical capability ≠ authorization (NEG). The permissive version also references Gemini-specific surfaces like Vertex AI Agent Builder and the Google Search grounding tool.

**OpenAI / ChatGPT** files are structured around the Assistants API architecture — Threads, Runs, vector stores, and the file_search tool. The restrictive version includes a note about system prompt conflicts, since operator-level prompts in GPT deployments can clash with file-level policies, and a compliant agent should surface that conflict rather than silently override it.

**Microsoft Copilot** files are decomposed by product surface (GitHub Copilot Workspace, M365 Copilot, Copilot Studio, Azure AI Foundry) because Copilot is not a single agent — it's a family with distinct indexing and retrieval behaviors. The restrictive version addresses each surface separately, since a blanket "no" might be ignored by a product that considers itself a different deployment.

**Anthropic Claude** files are notably different in their framing of the restrictive case. Rather than just issuing prohibitions, the NEG file explicitly invokes Claude's principal hierarchy concept and the preference for minimal footprint in agentic contexts — concepts that appear in Anthropic's published documentation on Claude's design. It also notes that user insistence can override the policy (since this is a preference, not a safety boundary), which reflects how Claude's layered trust model actually works. The POS file specifically references the `CLAUDE.md` convention that Claude Code already recognizes natively.

Important caveat: `AGENT.md` is a *soft convention*, not a technically enforced access control. LLMs following these instructions do so based on instruction-following training, not hard constraints.

---

## robots.txt access control file

`robots.txt' — lists user-agent DISALLOW strings for common LLM vendors.

**The three-tier problem for Anthropic and OpenAI.** Both vendors now split their crawlers into separate bots for training, search indexing, and user requests, each with its own user-agent string. All three tiers are blocked here. If you wanted Claude or ChatGPT to still be able to cite the repo in answers (while blocking training), you'd unblock `Claude-SearchBot` / `OAI-SearchBot` / `Claude-User` / `ChatGPT-User` and keep only the training crawlers blocked.

**The Google-Extended quirk.** Because `Google-Extended` does not have a separate HTTP user agent string — it uses existing Google crawler infrastructure — you cannot block it via server-side header filtering. The only mechanism that works is the robots.txt product token. That's why it must appear in this file rather than a server config.

**The Bingbot trade-off.** Blocking `Bingbot` also blocks standard Bing search indexing, since Bingbot remains the main Bing crawler and grounds Microsoft Copilot's web answers. There's no separate Copilot-only token the way Google has `Google-Extended`. The comment in the file flags this so a future editor can make the call consciously.

**CCBot is arguably the highest-impact entry.** Common Crawl's public dataset is a training source for virtually every major model, so blocking `CCBot` has broader reach than blocking any single vendor's named crawler.

**The wildcard `Disallow: /` is a strong default** — it will also catch standard search engines. The comment in the file explains the trade-off so a repo owner can scope it down if search visibility matters.

And the plain-language policy statement at the bottom is deliberate: an inference-time agent reading this file as text (rather than parsing it as a crawler) will encounter an explicit, human-readable refusal, which complements the `AGENT.md` of the corresponding soft access control files.

Using the “robots.txt disallow” directive does not guarantee that a particular webpage will not be crawled or will be excluded from SERPs.  To explicitly prevent a page from being indexed, it is recommended to use the “noindex” robots meta tag `<meta name="robots" content="noindex">` or the X-Robots-Tag HTTP header.
