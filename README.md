# Awesome-Claude-Bill-Optimizer

## Top Claude Bill Optimizer Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Token Compression, Context Management & Cost Reduction for AI Coding Agents*  

**Last updated: March 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Claude Bill Optimization**. These tools reduce token consumption across Claude Code, Codex, Cursor, and other AI coding agents—through output compression, context management, command output filtering, and persistent memory systems.



**Examples** include RTK (Rust Token Killer), Caveman Claude, Headroom, Token Savior, Repomix, Code2prompt, Omniroot, claude-token-efficient, MindStudio Agent Skills Plugin, and Graphify (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, local compression, and open token optimization—ideal for developers, teams, and organizations seeking transparent, vendor-independent cost reduction.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Omniroot](https://github.com/diegosouzapw/OmniRoute)**  

  Free AI gateway providing access to 90+ free API providers for Claude Code and other agent harnesses. Features automatic fallback when providers rate-limit, model switching without manual intervention, and integration with compression tools like RTK and Caveman. Works with FreeClaude Code (open-source Claude Code harness) to provide free AI coding without subscription. **Note**: Requires community-maintained provider list—availability varies by region and provider status .



- **[MindStudio Agent Skills Plugin](https://www.mindstudio.ai/)**  

  Routes tasks to the right model programmatically without rebuilding infrastructure. For teams building complex agentic systems where Claude Code orchestrates MindStudio agents as capabilities. **Note**: Commercial SaaS platform—not open-source .



- **[Headroom Cloud](https://www.npmjs.com/package/headroom-ai)**  

  Hosted compression API for LLM context. Available as cloud service (API key required) or self-hosted proxy. SDKs for TypeScript/JavaScript with Vercel AI middleware, OpenAI wrapper, and Anthropic wrapper. **Free tier** available; cloud pricing beyond free tier not specified in search results .



## Open-Source GitHub Projects



- **[RTK (Rust Token Killer)](https://github.com/rtk-ai/rtk)**  

  CLI proxy that filters command output before it reaches Claude's context, reducing token consumption by **60-90%** across coding sessions . **The most mature command-output compression tool for Claude Code**. Uses **PreToolUse hook** that transparently rewrites commands (e.g., `git status` → `rtk git status`) before shell execution—100% adoption rate vs 60-70% for CLAUDE.md instructions, with only 10 tokens context overhead vs 2000 . **Does not break prompt cache**—filters output once at execution time, filtered result written to conversation history and never changes . `rtk gain` shows token savings dashboard; `rtk cc-economics` shows cache write/read volumes. **Critical**: Two unrelated projects share the name `rtk`—verify `rtk gain` works to confirm correct installation (Rust Token Killer, not Rust Type Kit) . Windows users need WSL for full hook support—native Windows falls back to CLAUDE.md injection without auto-rewrite .



- **[Caveman](https://github.com/JuliusBrussee/caveman)**  

  Skill/plugin for AI coding agents (Claude Code, Cursor, Codex, Gemini) that compresses **prose output** to reduce token usage by up to **65%** while maintaining 100% technical accuracy for code and commands . **The most viral token-saving tool**—gained **4,100 GitHub stars in 3 days**, then surpassed **20,000 stars** . Instructs agents to "speak like caveman"—drop articles, filler, pleasantries, hedging; keep technical terms, code blocks, error strings exact . **Three compression levels**: lite (remove filler), full (standard caveman, fragments allowed), ultra (maximum compression) . **Auto-clarity rule**: automatically reverts to normal prose for security warnings, irreversible-action confirmations, and complex multi-step sequences to prevent ambiguity . **Measured on real Claude API**: 22–87% savings across 10 tasks, average 65% . Includes `/caveman-compress` for memory file compression (reduces input tokens by ~45%) and `/caveman-stats` for session savings tracking . **Zero telemetry, zero network calls after installation** . **Rule of thumb**: Enable if normal replies exceed ~1.5-2k output tokens; disable if shorter or paying per-request .



- **[Token Savior](https://github.com/Mibayy/token-savior)**  

  MCP server that indexes codebase by symbol (functions, classes, imports, call graph) so the model navigates by pointer instead of `cat`—**97% fewer chars injected** across 170+ real sessions . Includes persistent memory engine storing decisions, bugfixes, conventions in SQLite WAL + FTS5 with vector embeddings, ranked by Bayesian validity and ROI . **v4.3 adds Bash output compactors and PreToolUse rewriter**—shrinks command before it runs, not just output after . **Measured**: 96-task tsbench shows 80% reduction (17,221 → 3,395 active tokens/task); 7-day Bash bench saves ~20.4K tokens/week . **Profiles**: optimized (15 tools, ~1.5K manifest tokens, recommended default), compact-only (1 tool, bash compaction only), tiny (6 tools), full (68 tools) . **Composes with other tools**: disable TS_BASH_COMPACT=0 if already running RTK; run compact-only if Serena is your navigator . Install via pip or `uvx token-savior-recall` .



- **[Headroom](https://github.com/headroomlabs-ai/headroom)**  

  One-function compression API for LLM context (open-source). Compresses messages before sending to any LLM client—works with OpenAI, Anthropic, Vercel AI SDK . **Compression pipeline**: Kompress (ML text compression, configurable target ratio), SmartCrusher (JSON array dedup), CacheAligner . `min_tokens_to_compress` default 250—shorter messages unchanged . **Savings profiles** for agent workflows (e.g., 'agent-90' for Codex/Claude/Cursor) . Requires running Headroom proxy (`headroom proxy`) or cloud API key. **Fallback mode**: returns uncompressed if proxy is down (default) .



- **[Graphify](https://github.com/dreamtree-org/graphify)**  

  Turns a folder of code into a queryable, persistent knowledge graph—then answers task-shaped queries (working set, blast radius, minimal tests) within a token budget . **No LLM API key required**—extraction is tree-sitter AST parsing, deterministic and offline . **Measured**: up to **~8x token reduction** on ~100-file repos with deep cross-file structure; closer to **~1.5x on small libraries** . On a mixed corpus (Karpathy repos + papers + images, 52 files), **71.5x fewer tokens per query** vs reading raw files . **Install**: `npm install -g @dreamtree-org/graphify`—automatically wires up Claude Code skill, MCP server, and hooks . **Supports TypeScript/JavaScript, Python, Go, Rust, Java, C#, Ruby, plus MySQL schemas** .



- **[Paritok](https://pypi.org/project/paritok/)**  

  Local proxy that compresses prompts and stubs tool schemas before forwarding to any OpenAI-compatible upstream (Groq, Gemini, OpenRouter) or Anthropic . **Point Claude Code at proxy** via `ANTHROPIC_BASE_URL=http://127.0.0.1:8080`—compressed prompts go upstream, original responses return unchanged . **Codex CLI support**: writes `~/.codex/config.toml` automatically . **`/stats` endpoint** reports cumulative savings with cache-aware pricing: compressed content priced at full rate, frozen tool block priced as prompt-cache hit after turn one . **SDK mode** available for programmatic use .



- **[Tok Protocol](https://pypi.org/project/tok-protocol/)**  

  Local bridge proxy for Claude Code that compresses context via wire protocol and memory architecture (open-source, 0.1.x alpha) . **Wire protocol**: BPE-aligned sigils (`t:`, `g:`, `f:`) minimize token cost—structured state encodes context efficiently . **Memory architecture**: hot/durable buckets with different decay rates; bounded rolling state (constant-time updates, ~600 hot + ~2000 durable entries) . **Macro system** (experimental): repeated command sequences learned automatically with cross-session persistence . **Fail-open safety**: automatic fallback to baseline if compression risks fidelity . Install: `pip install tok-protocol`; run `tok bridge start` then `ANTHROPIC_BASE_URL=http://localhost:9090 claude` .



- **[claude-token-efficient](https://github.com/topics/claude-token-efficient)**  

  Community projects and configurations for reducing Claude token consumption. Includes settings templates, hook configurations, and compression integrations.



- **[Semantic Cache MCP](https://pypi.org/project/semantic-cache-mcp/)**  

  MCP server providing semantic caching, batch file reading with token budgets, and edit modes for maximum token savings . **Batch read**: token budget stops reading once `max_total_tokens` reached; unchanged files suppressed with zero tokens . **Line replace mode**: replace entire range without `old_string` needed—maximum token savings when line numbers known . **Semantic search**: embedding-based search across cached files—finds meaning, not keywords . Uses FastEmbed with `BAAI/bge-small-en-v1.5` (33M params) running locally via ONNX—no API keys, no network calls during search .



### Additional Strong Open-Source Options



- **[Repomix](https://github.com/yamadashy/repomix)** — Packs repository into AI-friendly format with token counting and compression options.

- **[Code2prompt](https://github.com/mattpocock/code2prompt)** — Generates optimized prompts from codebases with token-aware file selection.

- **Claude Code `/compact` and `/clear`** — Native context management commands; `/compact` summarizes history, `/clear` resets context .

- **Claude Effort Levels** — Platform-level control (`low`, `medium`, `high`, `xhigh`, `max`) trading intelligence, latency, and cost. Start with `high` (default); step down to `medium` or `low` for routine work once evals show quality holds .

- Community **n8n** workflows for token usage alerting and cost monitoring.



**Frameworks for building custom systems**: Combine **RTK** for command-output compression with **Caveman** for prose compression, **Token Savior** for symbol-based navigation and persistent memory, **Graphify** for knowledge graph queries, and **Paritok** for prompt compression—creating a fully self-hosted, multi-layer Claude bill optimization stack.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Token optimization tools must be validated against your specific workload. Savings vary by task type, output length, and repository structure.

- **Command-output compression (RTK) and prose compression (Caveman) are complementary.** RTK filters what commands produce before Claude sees it; Caveman compresses what Claude writes back. Running both is recommended for maximum savings .

- **Overlap requires opt-out configuration.** Token Savior and RTK both compress Bash output—disable Token Savior's `TS_BASH_COMPACT` if running RTK . Running both without configuration may cause conflicts.

- **Savings claims are workload-dependent.** Caveman's 65% average comes from 10 real Claude API tasks (22–87% range) . Graphify's 71.5x comes from a 52-file mixed corpus—on small, tightly-organized libraries it drops to ~1.5x, and on trivial questions in tiny repos, reading directly can be cheaper . **Always benchmark on your own workload before quoting numbers.**

- **Net vs gross savings matters.** Caveman's statusline shows gross savings, but `/caveman-stats` provides the net picture accounting for input token overhead of running compression rules. In one 47-turn session, estimated net was **negative** (caveman cost more than it saved) .

- **Prompt cache safety**: RTK explicitly does not break prompt caching—it filters output once at execution time, and the filtered result never changes .

- Self-hosted open-source solutions require proper security hardening, local proxy management, and ongoing maintenance. Verify tool compatibility with your specific Claude Code version and agent configuration before production deployment.



---



**Made for developers, platform engineers, and teams building transparent token optimization solutions.**  

Let's make Claude Bill Optimization more open, data-driven, and cost-effective.
