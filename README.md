# Awesome Jev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of resources, open-source clones, integrations, and engineering playbooks for **Jev** — TypeSafe AI's non-generative "System 1" decision model.

Jev doesn't generate text. Given a prompt and a set of typed candidates (a choice, a score, a yes/no), it returns a calibrated probability over the candidates in a single forward pass — no sampling, no JSON parsing, no hallucinated options. Since its release, a fast-moving ecosystem of integrations, open-source reproductions, and "System 1 / System 2" agent-architecture patterns has grown up around it. This list tracks it.

Every link below was resolved from its original source tweet/thread and verified to be a live, matching repository at the time it was added — see [CONTRIBUTING.md](CONTRIBUTING.md) for how entries are checked.

## Contents

- [About Jev](#about-jev)
- [Open-Source Reproductions & Clones](#open-source-reproductions--clones)
- [Coding Agents & Dev Tools](#coding-agents--dev-tools)
- [SDKs, Frameworks & Platform Integrations](#sdks-frameworks--platform-integrations)
- [Browser & Desktop Automation](#browser--desktop-automation)
- [Data & Retrieval](#data--retrieval)
- [Content, Media & Moderation](#content-media--moderation)
- [Simulation, Games & Hardware](#simulation-games--hardware)
- [Finance & Trading](#finance--trading)
- [Benchmarks & Evaluation](#benchmarks--evaluation)
- [Articles, Threads & Playbooks](#articles-threads--playbooks)
- [Contributing](#contributing)
- [License](#license)
- [Refix](https://refix.ai) - Growth: AI that helps your product grow faster on autopilot by running product experiments, SEO, content, and ads.

## About Jev

- [typesafe.ai](https://typesafe.ai) - TypeSafe AI's homepage.
- [typesafe.ai/Jev](https://typesafe.ai/Jev) - Product page for Jev.
- [Launch announcement](https://x.com/CompleteSkeptic/status/2099925682726002904) - Diogo Almeida (co-inventor of RLHF and InstructGPT at OpenAI) introduces Jev: a "System 1" model claimed to be 20-200x faster and 40-400x cheaper than generative frontier models for decision-shaped tasks. 32K context window; no image/audio input; cannot write code or prose by design.
- [typesafe-ai/skills](https://github.com/typesafe-ai/skills) - Official agent skills for building with the System One API. Install via `npx skills add typesafe-ai/skills --skill typesafe-ai`, or as a Claude Code plugin with `claude plugin marketplace add typesafe-ai/skills`.
- [typesafe-ai/system-one-adapter-python](https://github.com/typesafe-ai/system-one-adapter-python) - TypeSafe's own official drop-in adapter: swap `TypeSafeClient` for OpenAI/Anthropic/compatible backends to compare Jev against chat models using the same code.
- [typesafe.ai/blog/introducing-system-one-models-and-jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev) - TypeSafe's own announcement post for System One models and Jev.
- [docs.typesafe.ai](https://docs.typesafe.ai/introduction) - Official API docs for the System One / Jev endpoint.

## Open-Source Reproductions & Clones

- [bespokelabsai/nimble](https://github.com/bespokelabsai/nimble) - "Bespoke Nimble": a 9B open reproduction on Qwen3.5, built in a day from 2,676 examples via LoRA. Trained with "contrastive data curation" (near-identical question pairs with one flipped fact) to teach evidence-reading over explanation-generation. Scored 90.12% vs. Jev's 93.21% on the team's own eval.
- [NandhaKishorM/laya](https://github.com/NandhaKishorM/laya) - Laya, the upstream Apache-2.0 Jev alternative: an RLCD-trained decision engine shipped as a PyPI package, later ported to Apple Silicon as laya-mlx below.
- [convaiinnovations/laya](https://huggingface.co/convaiinnovations/laya) - Laya's model weights on Hugging Face.
- [mizorewww/laya-mlx](https://github.com/mizorewww/laya-mlx) - Laya (an Apache-2.0 Jev alternative) ported to Apple Silicon via MLX: 60 decisions/sec at under 1GB RAM, demoed playing Snake from raw probability classification.
- [Heman10x-NGU/Verdict-open-jev](https://github.com/Heman10x-NGU/Verdict-open-jev) - "Verdict": a 151M-parameter ModernBERT + GLiClass head model returning calibrated probabilities and an explicit "insufficient evidence" outcome in one forward pass. Weights on [Hugging Face](https://huggingface.co/heman10x/rlcd-modernbert-151m).
- [Heman10x-NGU/openJev-verdict-2.0](https://github.com/Heman10x-NGU/openJev-verdict-2.0) - v1.4 inference-engine fixes for the 151M Verdict model (calibrator auto-loading, NLI-style candidate templating, a 512-token context cap) that raised its public JevBench score from 66.2 to 74.9, plus a newer "Verdict 2.0" architecture and an in-browser WebGPU engine.
- [jaredpalmer/kev](https://github.com/jaredpalmer/kev) - A tiny Jev-like model built on Qwen2.5-0.5B, trainable and runnable locally on a MacBook.
- [TianyuCodings/NanoJev](https://github.com/TianyuCodings/NanoJev) - Independent implementation: a Qwen3-0.6B parallel judgment model with public weights and training code.
- [logan-markewich/jeff](https://github.com/logan-markewich/jeff) - A self-hosted drop-in replacement for Jev, powered by GliFormer.
- [hr98w/jev-visual](https://github.com/hr98w/jev-visual) - An educational Jev-like visual-inference experiment on Apple Silicon, adding image input which Jev lacks.
- [ikermoel/open-alternative-jev](https://github.com/ikermoel/open-alternative-jev) - An open-source System-One-style decision layer over any open-weights LLM, benchmarked against Jev.
- [kshetrajna12/reflex](https://github.com/kshetrajna12/reflex) - A small open decision model on Qwen3.5 re-creating the Jev/System One API with vision input.
- [ekzhang/openjev-sglang](https://github.com/ekzhang/openjev-sglang) - A Jev-compatible API endpoint built on open models via SGLang (prefill-only), for self-hosting on GPU servers.
- [githubnext/localjev](https://github.com/githubnext/localjev) - A local Jev-compatible `/v1/systemone` bridge backed by DiffusionGemma.
- [TheoLeeCJ/SemIf](https://github.com/TheoLeeCJ/SemIf) - "Semantic ifs" from open models running on a single 3090 at home. Independent research, not affiliated with Jev/TypeSafe.
- [vinnylarouge/jevlike](https://github.com/vinnylarouge/jevlike) - Independent research evaluating mixed-length candidate sets as a Jev-style research baseline, not a drop-in clone.
- [sabeel111/OpenSourceJev](https://github.com/sabeel111/OpenSourceJev) - Independent research and experiments on small decision models, inference optimization, and parallel sampling in the Jev style.
- [razorback16/openjev](https://github.com/razorback16/openjev) - An independent Jev-compatible System One decision server running DiffusionGemma via vLLM or on-device MLX.
- [abhishek085/open-spark-jev](https://github.com/abhishek085/open-spark-jev) - Open-source local decision models inspired by Jev/System One, built on Qwen3 and tuned for NVIDIA DGX Spark hardware.
- [fidecastro/jevify](https://github.com/fidecastro/jevify) - A pip-installable adapter that serves any OpenAI-compatible LLM (including local GGUFs) as a Jev-like typed-decision endpoint.
- [TimothyZhang7/open-decisions](https://github.com/TimothyZhang7/open-decisions) - An MIT Python SDK for typed decisions from local open models, benchmarked against Jev on an experimental Tetris demo.
- [vllm-project/vllm#57250](https://github.com/vllm-project/vllm/pull/57250) - A vLLM patch exposing Google's DiffusionGemma (26B MoE, 3.8B active) behind a Jev-compatible `/v1/systemone` endpoint, using parallel denoising instead of autoregressive generation and adding image input, which Jev lacks.
- [nokia-applied-research/AnyJev](https://github.com/nokia-applied-research/AnyJev) - A training-free calibration layer turning any open LLM's next-token logits into a Jev-style typed decision: zero-label recalibration cuts the answer-order-flip rate from 23% to 7.3%, and a few hundred labels bring calibration error from 0.240 to 0.095.
- [wnzn/semif-go](https://github.com/wnzn/semif-go) - A Jev-like decision API server over local llama.cpp models, answering choice/yes-no/score questions on text or images without generating JSON; built on the scorer from TheoLeeCJ/SemIf above.
- [Mapika/decider-2b](https://huggingface.co/Mapika/decider-2b) - An Apache-2.0 2B-parameter Jev-style decision model on Qwen3.5, with a vision variant and a GGUF quantization; over 130k combined downloads on Hugging Face.
- [wfzyx/von](https://github.com/wfzyx/von) - An Open-Source, Non-Autoregressive System One Decision Model. Calibrated discrete, probabilistic, and ordinal inference in sub-25ms.
- [Contrastive-LM/CLM](https://github.com/Contrastive-LM/CLM) - Contrastive Language Models: a System One model that embeds states and actions separately and matches them by similarity instead of answering typed questions, reporting on-par accuracy with Jev at up to 9x lower latency.
- [togethercomputer/tev1](https://github.com/togethercomputer/tev1) - Together AI's open-weight reproduction: Qwen3.5-4B fine-tuned via LoRA on ~38K examples to pick one answer letter from 2-24 options, released with the full data recipe and a $17 training-cost writeup.
- [fastino/GLiNER2.5-Decide](https://huggingface.co/fastino/GLiNER2.5-Decide) - Fastino Labs' 340M-parameter Apache-2.0 encoder decision model; scored 60.1% on their own Fast Decisions benchmark, ahead of Laya (46.6%) and a Jev-based baseline (57.5%).

## Coding Agents & Dev Tools

- [TheoOliveira/pi-jev](https://github.com/TheoOliveira/pi-jev) - Semantic tool routing for the Pi coding agent: before each step, Jev scores whether a tool is relevant and gates activation at a 0.65 probability threshold.
- [jkudish/jev-mcp](https://github.com/jkudish/jev-mcp) - Packages Jev's judgments as standard MCP tools (verify claims, rank candidates, screen content for prompt injection).
- [devagrawal09/jev-review](https://github.com/devagrawal09/jev-review) - A staged code-review workflow and local dashboard built on Jev.
- [devagrawal09/stanley-code](https://github.com/devagrawal09/stanley-code) *(originally `jev-code`)* - Bounded Jev-gated workflows for coding agents.
- [0xNatoshi/jev-codex-router](https://github.com/0xNatoshi/jev-codex-router) - Per-turn model and reasoning-depth routing for Codex, driven by Jev.
- [gargpratyush/jev-router](https://github.com/gargpratyush/jev-router) - Routes each Claude Code task to the cheapest sufficient model.
- [thruwire/foreman](https://github.com/thruwire/foreman) - A "software factory foreman" for Codex: Jev decides whether to continue, accept, or stop.
- [EliaAlberti/jev-rules](https://github.com/EliaAlberti/jev-rules) - Jev picks which of your rule files apply to the current prompt, so Claude only sees the relevant ones.
- [kitze/skillbox](https://github.com/kitze/skillbox) - Self-hosted, versioned Agent Skills library with optional Jev-driven recommendations for which skill to load per turn.
- [itsmostafa/typesafe-mcp](https://github.com/itsmostafa/typesafe-mcp) - An MCP connector giving any agent direct access to Jev.
- [DevMortimer/pi-warden](https://github.com/DevMortimer/pi-warden) - Guardrails for the Pi agent: Jev judges irreversible/off-task tool calls, detects stuck loops, and flags unverified "done" claims.
- [perixtar/jev-e2e](https://github.com/perixtar/jev-e2e) - Natural-language end-to-end web app tests, powered by Jev and Playwright.
- [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates/tree/main/cli-tool/components/mods/productivity) - See the `jev-model-router` and `jev-skill-suggestion` mods: per-turn model/effort routing and skill selection for Claude Code, installable with `npx claude-code-templates@latest --mod productivity/jev-model-router`.
- [tlangridge/Alloy](https://github.com/tlangridge/Alloy) - A local, multi-model panel for Claude Code that uses Jev to route tasks by complexity, model strength, and remaining subscription quota.
- [coldteadotai/abide](https://github.com/coldteadotai/abide) - Uses Jev to score every agent edit against project rules a linter can't express.
- [kbhuw/jev-sift](https://github.com/kbhuw/jev-sift) - Lets an agent use Jev to decide if a file, tool call, or page is worth reading before spending LLM tokens on it.
- [HexyeDEV/JevPR](https://github.com/HexyeDEV/JevPR) - An open-source GitHub PR review tool automated by Jev.
- [Braedennn/OpenJev](https://github.com/Braedennn/OpenJev) - A generic agent harness that routes every step through a Jev decision, pluggable with any LLM.
- [MagicBeansAI/jev-audit](https://github.com/MagicBeansAI/jev-audit) - Audits a codebase to find which existing LLM calls could be replaced by Jev.
- [kushals256/jevcache](https://github.com/kushals256/jevcache) - An OpenAI-compatible caching proxy that uses Jev to detect repeated same-intent requests and skip the billed call.
- [hqman/JevScout](https://github.com/hqman/JevScout) - A job-hunting skill: Jev finds a company's Careers pages and scores each role against a profile.
- [stas4000/jev-clerk](https://github.com/stas4000/jev-clerk) - A bookkeeping agent where Jev makes every step decision and a separate model periodically rewrites the playbook.
- [shantanugoel/ask-jev-skill](https://github.com/shantanugoel/ask-jev-skill) - A portable skill that lets any agent harness (demoed on Hermes) call Jev for a decision.
- [sutro-sh/jev-align](https://github.com/sutro-sh/jev-align) - An open-source CLI to calibrate Jev to custom decision criteria using GEPA.
- [caiovicentino/jev-align](https://github.com/caiovicentino/jev-align) - A separately built, differently-implemented calibrated alignment verifier for LLM responses/agent plans powered by Jev.
- [sumanmichael/jevlang](https://github.com/sumanmichael/jevlang) - A Python DSL for writing Jev-backed decision workflows as a natural-language "smart if".
- [vercel-labs/ai-cli](https://github.com/vercel-labs/ai-cli) - A terminal evaluation CLI defaulting to Jev, using its probability-weighted mean over an AI SDK schema.
- [dbreunig/building-with-jev-skill](https://github.com/dbreunig/building-with-jev-skill) - A skill for writing and improving programs that call Jev.
- [mizchi/jev-lint](https://github.com/mizchi/jev-lint) - A linter that scores code and prose across TypeScript, Rust, Python, Go, and Markdown with Jev, shipping 60+ slop-detection rules.
- [HarnessRouter/SystemOneHarness](https://github.com/HarnessRouter/SystemOneHarness) - An open-source agent harness built specifically for System One models like Jev, runnable entirely locally.
- [integrate-your-mind/jev-codex-plugin](https://github.com/integrate-your-mind/jev-codex-plugin) - A Codex plugin using Jev for tool/model/task routing, failure diagnosis, and evidence-based completion checks.
- [utk2103/jev-studio](https://github.com/utk2103/jev-studio) - An MCP-based playground for Jev's Choice/Noul/Score primitives, with prompt libraries and cookbook slash commands.
- [MatthewFeroz/docshound-jev](https://github.com/MatthewFeroz/docshound-jev) - Cross-repository issue/PR triage using Jev classification and evidence review inside LangGraph.
- [am-kul/jev-runtime-shield](https://github.com/am-kul/jev-runtime-shield) - A reference app for real-time behavioral threat detection where Jev makes the typed call and deterministic code enforces it.
- [rchandnaWUSTL/auto-guard](https://github.com/rchandnaWUSTL/auto-guard) - Asks for human approval, with a larger model's one-line reasoning, whenever Jev isn't confident in an agent's next action.
- [jackbarunz/jev-tool-router](https://github.com/jackbarunz/jev-tool-router) - Uses Jev to route among hundreds of connected MCP tools so Codex doesn't need every schema in context.
- [fstandhartinger/chat-seek-vscode](https://github.com/fstandhartinger/chat-seek-vscode) - A VS Code extension for local search across Claude Code/Codex/OpenCode chat history, reranked with Laya.
- [Towow-ai/jpp](https://github.com/Towow-ai/jpp) - "J++": an experimental programming language built around Jev, with its own syntax and a Rust parser/checker/interpreter for composing typed questions.
- [fajarhide/askgrep](https://github.com/fajarhide/askgrep) - A Rust CLI for semantic codebase search: describe what you're looking for in plain English and Jev scores every function against it instead of matching keywords.
- [tamaratran/fast-jev-compaction](https://github.com/tamaratran/fast-jev-compaction) - A Claude Code plugin that replaces the compaction summary with Jev decisions, scoring every tool call and result so stale ones are dropped or truncated while kept ones stay verbatim.
- [fatelei/jev-compact](https://github.com/fatelei/jev-compact) - The same Jev-scored compaction pattern as the entry above, targeting the OpenAI Codex CLI instead of Claude Code.
- [FrancoisChastel/jev-code](https://github.com/FrancoisChastel/jev-code) - Exposes Jev's classify/check/score/rank/ask primitives as a tool inside Claude Code, Codex, Pi, and OpenCode with one-command setup; an unrelated, separately-built project despite sharing a name with what devagrawal09/stanley-code above used to be called.
- [kerpopule/hermes-jev-skills](https://github.com/kerpopule/hermes-jev-skills) - A skill suite adding Jev-based model routing, retrieval filtering, memory selection, skill choice, compaction, and computer/browser use to Hermes, Claude Code, and Codex.
- [TheMarco/token-saver](https://github.com/TheMarco/token-saver) - Pairs Codex-to-Muse task delegation with "Jev Context," which ranks file and log excerpts by relevance before they enter the main model's context instead of dumping whole files in.
- [dealerdefi/Jevmind](https://github.com/dealerdefi/Jevmind) - A dashboard running 30 tasks across 4 parallel coding agents, where every agent action is gated by 12 typed questions (is_destructive, leaks_secret, needs_approval, model_tier, diff_risk, ...) before it's allowed to proceed.
- [danielgshea/jev-as-a-judge](https://github.com/danielgshea/jev-as-a-judge) - A LangChain/LangSmith harness using Jev as an agent-eval judge.
- [Dicklesworthstone/skillranker](https://github.com/Dicklesworthstone/skillranker) - A Rust CLI that uses Jev to rank which agent skill to load next from live session context, with Claude Code hooks and an abstain option.
- [Kevthetech143/super-jev](https://github.com/Kevthetech143/super-jev) - A small, extensible decision-to-action harness built on Jev.
- [libingzheren/Jev-Mem](https://github.com/libingzheren/Jev-Mem) - Research code for "System-One-Controlled Agentic Memory": using Jev-style typed decisions to gate what an agent writes to and retrieves from memory.
- [Avinash-jetwani/jevmem](https://github.com/Avinash-jetwani/jevmem) - Automatic project memory for Claude Code, Cursor, and Codex: Jev decides which decisions, constraints, bugs, and todos from a session are worth writing to `JEVMEM.md`.
- [monteduro/killmyidea](https://github.com/monteduro/killmyidea) - Describe a startup idea and Jev answers 10 typed questions in parallel (8 scored criteria plus category and clarity) to return a kill/fix/ship verdict.

## SDKs, Frameworks & Platform Integrations

- [danvega/jev-spring-boot-starter](https://github.com/danvega/jev-spring-boot-starter) - A Spring Boot 4 starter for Jev using RestClient and typed questions.
- [yusukebe/hono-jev-router](https://github.com/yusukebe/hono-jev-router) - Routes HTTP requests by meaning for the Hono framework, powered by Jev.
- [khmuhtadin/n8n-nodes-jev-classification](https://github.com/khmuhtadin/n8n-nodes-jev-classification) - An n8n community node for classifying and scoring text with Jev, with batching.
- [vercel-labs/jev-ai-sdk-form-router](https://github.com/vercel-labs/jev-ai-sdk-form-router) - Routes form submissions to the right destination using Jev and the Vercel AI SDK.
- [nandansrikrishna/jev-go](https://github.com/nandansrikrishna/jev-go) - A standalone Go CLI and MCP server for Jev with JSONL evaluation and resumable batches.
- [ainame/swift-typesafe](https://github.com/ainame/swift-typesafe) - An unofficial Swift SDK for TypeSafe's Jev API.
- [dannote/jev](https://github.com/dannote/jev) - An Elixir/OTP client: reply to Jev from a GenServer and pattern-match on its typed answer.
- [gilljon/typesafe-ai-rs](https://github.com/gilljon/typesafe-ai-rs) - An independent async/blocking Rust SDK for the TypeSafe System One API.
- [pydantic/pydantic-ai](https://github.com/pydantic/pydantic-ai/blob/main/docs/models/typesafe.md) - Pydantic AI's built-in TypeSafe/Jev model provider, usable as a structured-output model or as an LLM-judge evaluator.

## Browser & Desktop Automation

- [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) - Passes a typed DOM snapshot to Jev instead of a screenshot to a vision model; the heavy LLM only fires for actual text input. Completed a Zurich→London Google Flights search in 7.1s.
- [awlevin/typesafe-computer-use](https://github.com/awlevin/typesafe-computer-use) - macOS automation for about $0.0002/step: OCR the screen, classify the next action with Jev, click.
- [droidrun/mobile-jev](https://github.com/droidrun/mobile-jev) - Android automation on top of Mobilerun, driving real devices via CLI while watching screen state and logs.
- [moritzkremb/jev-voice-browser](https://github.com/moritzkremb/jev-voice-browser) - Voice-controlled browsing: Jev resolves intent and target element in ~300ms per spoken word, Playwright acts.
- [kitze/unclutter](https://github.com/kitze/unclutter) - A WXT browser extension that uses Jev to identify and hide ad banners/popups from the page.
- [Sac-Y/Jev-cu](https://github.com/Sac-Y/Jev-cu) - A Codex skill where Jev picks the next UI action for computer use while a local policy gate blocks sensitive clicks.
- [imohitmayank/jevfill](https://github.com/imohitmayank/jevfill) - A Chrome extension that autofills web forms from saved notes, using Jev to match fields.
- [chand45/JetDesk](https://github.com/chand45/JetDesk) - Native Windows desktop automation powered by Jev and Windows UI Automation.
- [vladzima/jev-x](https://github.com/vladzima/jev-x) - A browser extension scoring X/Twitter posts on firsthand experience, promo, bait, and depth with Jev.
- [nomanjack/smart-paste](https://github.com/nomanjack/smart-paste) - A Chrome extension that uses Jev choice/score/noul questions to match pasted text to form fields and paste only confident matches.
- [lahfir/agent-desktop](https://github.com/lahfir/agent-desktop) - Rust-based desktop automation that reads an app's real UI through OS accessibility trees instead of screenshots, with an optional Jev skill for selecting controls and actions without loading the whole UI tree into context.
- [shhivv/arc-cua](https://github.com/shhivv/arc-cua) - A desktop-automation action layer where Jev picks the next UI operation and target from a dynamically built action space limited to what the current screen actually exposes.

## Data & Retrieval

- [realZachi/pg-jev](https://github.com/realZachi/pg-jev) - A PostgreSQL extension for filtering, classifying, and sorting rows with natural language — no vector DB required.
- [superagents-lab/jev-search](https://github.com/superagents-lab/jev-search) - Web search built on Jev for source selection, query understanding, and relevance ranking.
- [kylemclaren/jevsearch](https://github.com/kylemclaren/jevsearch) - A shadcn/ui site-search block that shows keyword hits instantly, then re-ranks the top 20 with one Jev request (a Noul per page plus a Choice over all of them), distinct from superagents-lab/jev-search.
- [jexp/neo4jev](https://github.com/jexp/neo4jev) - Traverses a Neo4j graph by having Jev classify which neighboring relationship to follow next.
- [jerryjliu/docjev](https://github.com/jerryjliu/docjev) - OSS library that uses Jev plus LiteParse (and optional LlamaParse OCR) to classify documents and split multi-document packets by natural-language category rules; ~6x faster than GPT-5.6-luna at equivalent accuracy.
- [kylemclaren/jevpdf](https://github.com/kylemclaren/jevpdf) - Searches a PDF by meaning in the browser: pdf.js extracts each line locally and Jev answers one Noul per line, highlighting matches page by page ranked by probability.
- [pinecone-io/using-typesafe-and-pinecone](https://github.com/pinecone-io/using-typesafe-and-pinecone) - Pinecone's reference integration reranking retrieved candidates against natural-language criteria with Jev instead of a long-context LLM call; ~5x faster and ~43x cheaper than Claude Opus 5 on the same 200-candidate rerank in their benchmark.
- [mgaitan/sqlite-jev](https://github.com/mgaitan/sqlite-jev) - A loadable SQLite extension and Python wrapper for asking Jev typed questions from SQL.
- [hev/reranker](https://github.com/hev/reranker) - A 90-line calibrated reranker on Jev: one call, up to 30 documents, a probability per document.
- [AkashPriyadarshii/jev-seo](https://github.com/AkashPriyadarshii/jev-seo) - A Rust CLI/MCP server auditing SEO and AI-crawler accessibility with Jev.
- [socai-io/jev-social](https://github.com/socai-io/jev-social) - Jev-powered social research across Instagram, TikTok, and LinkedIn with cited, evidenced reports.
- [harshwasan/jev-retrieval-eval](https://github.com/harshwasan/jev-retrieval-eval) - Reproducible retrieval evaluations comparing Jev and GPT as a second-stage document filter, with cost estimates.
- [RenaGao/jev-dataops](https://github.com/RenaGao/jev-dataops) - An open-source Jev-powered workbench for streaming data selection, quality eval, and automatic LoRA training/eval.
- [seanebones-lang/evidencelens](https://github.com/seanebones-lang/evidencelens) - An open-source research build testing Jev for bounded semantic evidence review and human-review triage.
- [sedthh/xjevboost](https://github.com/sedthh/xjevboost) - Use larger tabular datasets with Jev by learning which rows and columns to include in each call, reducing token usage through adaptive ensembles.
- [kylemclaren/jevql](https://github.com/kylemclaren/jevql) - A psql-style CLI, MCP server, and Go/TypeScript/Python SDKs that add `jev()` predicates to queries against vanilla PostgreSQL, with no extension.
- [kyotofin/tax-doc-classifier](https://github.com/kyotofin/tax-doc-classifier) - A tax document page classifier built on Jev: one request per PDF page returns a probability over 261 IRS forms and 7 page kinds, with no model trained or hosted.
- [AkashPriyadarshii/jev-curate](https://github.com/AkashPriyadarshii/jev-curate) - A Rust/Python streaming pipeline that filters and scores Parquet/JSONL dataset rows through Jev's Choice/Score/Noul primitives for synthetic-data and pretraining-corpus cleanup.

## Content, Media & Moderation

- [trungdq88/youtube-sponsor-detection](https://github.com/trungdq88/youtube-sponsor-detection) - Detects YouTube sponsor segments from live audio and transcript, powered by Jev.
- [ChetasLua/jevmeter](https://github.com/ChetasLua/jevmeter) - Scores every sentence of a video against a chosen angle and renders it as a scored highlight reel.
- [brainstormity/Jev-Moderation-Bot](https://github.com/brainstormity/Jev-Moderation-Bot) - Discord moderation for spam and phishing links.
- [gaborishka/jev-wrapped](https://github.com/gaborishka/jev-wrapped) - Judges a Telegram channel's year of posts with Jev and renders a "wrapped" summary card.
- [stas4000/jev-scroll](https://github.com/stas4000/jev-scroll) - A Chrome extension that labels every X/Twitter post with a Jev decision while scrolling.
- [achimala/jev-paint](https://github.com/achimala/jev-paint) - Turns Jev into a parallel pixel-color predictor: brush width tracks Jev's per-pixel confidence.

## Simulation, Games & Hardware

- [fhshaik/typesafe-mario](https://github.com/fhshaik/typesafe-mario) - A Jev agent that plays Super Mario Bros. by reading structured emulator state instead of screenshots.
- [VBS2004/jev-plays-super-mario-bros](https://github.com/VBS2004/jev-plays-super-mario-bros) - A separate Jev-driven Mario agent, distinct implementation from the entry above.
- [standardagents/jevpilot](https://github.com/standardagents/jevpilot) - A playable Three.js driving simulator with a Jev-powered autopilot.
- [RomanSlack/jev-drone](https://github.com/RomanSlack/jev-drone) - A camera-only autonomous drone in MuJoCo, using a small Jev judgment model in the loop at 2.5Hz.
- [AboveColin/HA-Jev](https://github.com/AboveColin/HA-Jev) - Home Assistant integration: typed Jev answers exposed as sensors, plus actions and a conversation agent for Assist.
- [lhemerly/mcts-agent](https://github.com/lhemerly/mcts-agent) - Discriminative Monte Carlo Tree Search: Gemini plans, Jev scores and prunes the tree in milliseconds.
- [CPPAlien/playwithjev](https://github.com/CPPAlien/playwithjev) - A playable chess game against Jev with live typed inputs and probabilities.
- [thelau/jev-tetris](https://github.com/thelau/jev-tetris) - A Tetris where every legal placement is enumerated as a sentence and Jev points at one, visualizing its full probability distribution.
- [trycua/cua](https://github.com/trycua/cua/tree/main/libs/cua-s1) - See `libs/cua-s1`: home of `cua-s1-form-v0`, a 706K-parameter, MIT-licensed specialist model that fills web forms from UI state in ~50ms.
- [TholeG/typesafe-chess](https://github.com/TholeG/typesafe-chess) - Two Jev instances play chess against each other: every move is a typed Choice over the legal moves plus a Score position evaluation, optionally driving an AlphaZero-style MCTS.
- [lukaske/jev-doom-agent](https://github.com/lukaske/jev-doom-agent) - Runs two Chocolate Doom instances compiled to WebAssembly and has Jev pick a tactical macro from structured game state each tick, visibly falling back to an offline policy on a failed or low-confidence call.

## Finance & Trading

- [jarrodwatts/jev-trader](https://github.com/jarrodwatts/jev-trader) - Makes one AI trade decision per Monad block on Kuru MON-USDC; defaults to mock/dry-run without a configured private key.
- [svmanth/jmarket](https://github.com/svmanth/jmarket) - A Chrome extension giving Jev's own forecast on Polymarket-style questions instead of the crowd's.
- [OpenByteInc/QuantDinger](https://github.com/OpenByteInc/QuantDinger) - A self-hosted, open-source AI trading OS (strategy research, backtesting, paper/live execution) that gates trade entry behind a Jev System One decision filter.

## Benchmarks & Evaluation

- [iammrduncan/typesafe-ai-benchmark](https://github.com/iammrduncan/typesafe-ai-benchmark) - An LLM gateway that mimics TypeSafe's structured output contract, useful for benchmarking drop-in replacements against real Jev behavior.
- [goodrahstar/jev-column-race](https://github.com/goodrahstar/jev-column-race) - Races Jev against Gemini 3.8 Flash labelling 1,000 app reviews for sentiment/topic/bug/churn.
- [ickas/battleship-vs-jev](https://github.com/ickas/battleship-vs-jev) - A 228-test benchmark suite comparing Jev's decisions against scripted strategies at Battleship.
- [fstandhartinger/jevbench](https://github.com/fstandhartinger/jevbench) - JevBench: benchmarks Jev-class typed decision models on smartness, cost, speed, and reliability.
- [TrustifAI/typed_evals](https://github.com/TrustifAI/typed_evals) - A framework-agnostic Python library for typed, calibrated LLM/agent evaluation backends including Jev.
- [TheWayWithin/jev-bench](https://github.com/TheWayWithin/jev-bench) - A 42-claim citation-verification benchmark: Jev vs. GPT-5.4, Claude Sonnet 5, and Gemini 3.1 Pro.
- [zilliztech/deep-searcher](https://github.com/zilliztech/deep-searcher/blob/master/evaluation/jev_stopping/README.md) - Uses Jev to decide when an agentic search workflow has gathered enough evidence to stop; across 100 multi-hop questions it matched DeepSeek V4 Flash's 93.25% Recall@5 while cutting median decision latency from 2.23s to 0.55s.
- [zilliztech/memsearch](https://github.com/zilliztech/memsearch/blob/main/evaluation/reranking-evaluation.md) - Jev-based memory reranking raised Recall@5 from 74.71% to 79.41% over the baseline, though it still trailed Voyage rerank-3's 81.87%.
- [zilliztech/vector-graph-rag](https://github.com/zilliztech/vector-graph-rag/blob/main/evaluation/jev/README.md) - Jev filters graph relationships for HotpotQA/MuSiQue multi-hop QA, beating GPT-4o-mini but trailing GPT-5-mini on relationship-selection accuracy.
- [crzyc0d3r/jev-agent-judge](https://github.com/crzyc0d3r/jev-agent-judge) - Evaluates recorded support-agent traces with typed Jev judgments (grounded, honest, relevant, helpful) and logs each as an Opik experiment, routing mid-confidence scores to human review.

## Articles, Threads & Playbooks

Not every valuable Jev post ships a repo. These threads carry the architectural ideas driving the ecosystem above:

- [Ronin — the "100x Upgrade" playbook](https://x.com/DeRonin_/status/2100917158922387537) - You don't get the 100x by swapping your LLM for Jev; you get it by finding the calls that never needed a language model in the first place and deleting them.
- [Milon — "Jev is not a smaller LLM"](https://x.com/milonspace/status/2101495990725566640) - Restricts Jev to exactly three gating jobs: is this done, which tool next, does a human need to see it — everything else still goes to a model that can write.
- [lifcc — System 1 / System 2 agent bifurcation](https://x.com/mylifcc/status/2101504368746848492) - Argues production agents need a strict split: Jev handles millisecond-level routing, the heavy LLM stays dormant until deep reasoning is actually required.
- [Alcides Ticlla — the cost/latency gap, quantified](https://x.com/AlcidesTicllaCh/status/2101465729929220490) - The same classification task: $0.013880 in 8.566s on an LLM vs. $0.000081 in 0.114s on Jev, verbatim from Jev's own numbers.
- [てる (@rute1203d) — four domain playbooks](https://x.com/rute1203d/status/2100783005229011415) - Concrete patterns for support-ticket triage, search-result relevance, tool selection, and agent-memory gating.
- [dani_avila7 — Jev Model Router for Claude Code](https://x.com/dani_avila7/status/2101176629745561686) - Announces the `jev-model-router` mod (see [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates) above) with the reasoning behind locking the main model at session start to preserve prompt caching.
- [sakevoid — Jev is judgment, not cognition](https://x.com/sakevoid/status/2101676640879190343) - A mental model for agent architecture: Claude/Codex handle cognition, Jev handles fast judgment calls, deterministic code enforces hard rules, and humans veto the irreversible ones.
- [me_barnyx — 5 rules before you wire Jev in](https://x.com/me_barnyx/status/2101630380067500350) - A practical checklist — separate deciding from generating, set confidence thresholds before shipping, log confidence against real outcomes, treat vendor benchmarks skeptically — illustrated via the fast-jev-compaction context-compaction pattern.
- [neural_avb — Jev isn't deterministic](https://x.com/neural_avb/status/2101736546391244854) - Shows identical prompts returning different output probabilities across repeated runs, and that reordering candidate choices measurably shifts them.
- [bourneshao — the fatal flaw in Jev](https://x.com/bourneshao/status/2101802361588945073) - Jev confidently returns wrong typed verdicts on multi-step arithmetic (summing invoice line items), arguing a typed answer still needs validation.
- [drummatick — does Jev really save the cost?](https://x.com/drummatick/status/2101714564404715872) - Benchmarks Jev against GPT-5 on the Banking77 intent-classification dataset: GPT-5 beats Jev by 3.2% accuracy at 32x the cost, plus a Jev+GPT-5 cascade test.
- [kcp_kn — Jev as an agent-eval judge](https://x.com/kcp_kn/status/2101506638288965918) - Reports on LangChain's Deep Agents experiment where Jev matched human pass/fail labels 100% across 500 trials with up to 913x lower quality-score variance than GPT-5.6 Terra, at roughly 1/80th the cost of Claude Sonnet 4.6.
- [reachmeviz — Laya vs. Jev, tested](https://viswakumar.com/blog/laya_system_one_model) - Hands-on comparison finding Laya's out-of-the-box zero-shot classification near-random despite matching Jev's published numbers on trained domains, concluding Jev's real moat is zero-training-overhead generalization.
- [NathanFlurry — "jev is just a really smart switch statement"](https://x.com/NathanFlurry/status/2100036101809619314) - A hype-free mental model: 2016-era ML classifiers with 2026-era intelligence, not a GPT/Claude replacement.
- [whereischarly — benchmark it against encoders, not LLMs](https://x.com/whereischarly/status/2100955287200907343) - Argues the fair comparison for Jev isn't frontier LLMs but boring open-weight encoder classifiers that have done zero marketing.
- [0xRicker — "Jev Engineering" as a control-system layer](https://x.com/0xRicker/status/2101705843200721203) - Frames state → decision → action → verification → next state as a distinct architectural layer most agent stacks are missing.
- [miu21590 — mid-task reasoning-effort routing](https://x.com/miu21590/status/2101857866378362926) - Uses Jev to change a coding model's reasoning effort during a run rather than picking a model up front, reporting 50% lower cost.
- [Teknium — Jev-based compaction doesn't hold up](https://x.com/Teknium/status/2101398453578555898) - Ran Jev-driven context compaction against a reproducible public eval and found it degenerates to a free programmatic rule that gets worse each round and breaks prompt-cache reuse.
- [KrzysztofStaron — predict outcomes, not steps](https://x.com/KrzysztofStaron/status/2101422519391555867) - A concrete prompting technique for Jev's weak multi-step planning: reframe "which action to take" as "what outcome to aim for" (demoed on Tetris), reportedly 10x-ing task performance.
- [kwindla — Jev vs. GPT-5.6 Luna as a voice-pipeline operator](https://x.com/kwindla/status/2101394993957274021) - A domain-specific benchmark: Jev hits 92.6% command accuracy at 296ms median latency vs. Luna's 81.3% at 1,008ms in a speech-interface control task.
- [SUOHA_AI — Jev's own creator found its ceiling](https://x.com/SUOHA_AI/status/2101367171687280894) - Browser Use's founder, after the viral 7-second flight-booking demo, retested Jev on 20 complex real-world tasks and got 1/20 right vs. GPT-5.6 Luna's 17/20.
- [0x_kaize — free ways to access Jev without a waitlist](https://x.com/0x_kaize/status/2101330099802886343) - A practical, non-marketing rundown of no-waitlist Jev providers (OpenRouter, Vercel AI Gateway, Cloudflare, Netlify AI Gateway, OpenCode Zen) with a real price/context comparison.
- [nicbstme — Jev as Innovator's Dilemma](https://x.com/nicbstme/status/2101904295730016377) - Frames Jev as commoditizing the bottom of the ML market (classifiers, routers, scoring) in a way frontier LLM labs have no incentive to compete on.
- [ByrneHobart — cost discrimination, not price discrimination](https://x.com/ByrneHobart/status/2100233046792257801) - Frames Jev's real use as routing between deterministic rules and an expensive model per request, letting you do cost discrimination instead of flat pricing.
- [zelin1107 — auditing Jev's own numbers](https://x.com/zelin1107/status/2101904208547258587) - A close read of the launch blog's own "Nuance" disclosures — laptop-only benchmarks, unproven cost sustainability, in-house eval design, an admittedly non-empirical hallucination chart — arguing the widely-quoted 193.6x/444.6x figures are the company's best case, not a typical one.
- [Mahesh Lambe — four objections to the launch claims](https://x.com/Mahesh_Lambe/status/2101892492098781219) - "Can't hallucinate" only means schema-valid, not correct; the workflow eval's ground truth is the average of two LLMs' own predictions; the speed/cost multiples compare against TypeSafe's own slower wrapper rather than constrained-decoding baselines; and parallel typed outputs need consistency designed in by the developer.
- [Kaushik009911 — the tax Jev actually removes](https://x.com/Kaushik009911/status/2101879965977571591) - Argues the relevant comparison isn't Jev vs. a BERT classifier or grammar-constrained decoding, but the KV-cache and token-by-token cost those approaches still pay; Jev collapses a closed-state decision into one parallel forward pass under 200ms.
- [RobotsTJ500 — live-API mechanics and a code-review field test](https://x.com/RobotsTJ500/status/2101930064140968172) - Documents real measured latency (0.8-1.1s against the published 70-500ms) and field results from using Jev as a diff-triage layer, including how rephrasing a yes/no question shifted its score from 0.97 to 0.12.
- [Chrisondesk — comment moderation, line by line](https://x.com/Chrisondesk/status/2101894289475485849) - Moderated 100 comments for $0.002171 total and breaks down why: zero output-token cost, a closed answer space with nothing to invent, and RLCD-calibrated probabilities that make fixed thresholds meaningful in a way a chat model's self-reported confidence isn't.
- [noahkostesku — five places to put Jev in a coding-agent loop](https://x.com/noahkostesku/status/2102139134609391894) - Tool routing, context pruning, model escalation, termination checks, and test-failure triage — argues the moat is in how well a team wires decisioning into these points, not the model itself.
- [Prasenjit Sarkar — the $40M model with a 2-day head start](https://x.com/stretchcloud/status/2102335596421124212) - Lays out TypeSafe's Sept 15 seed round and System One category, then tracks how fast open-source caught up: Laya beat cloud Jev 11x on latency in a head-to-head on a 16GB MacBook Air, and Latent Space counted 6 independent Jev clones within 2 days of launch.
- [Prasenjit Sarkar — Jev vs. BM25 for tool retrieval](https://x.com/stretchcloud/status/2102436259830657057) - Jason Zhou's benchmark: Jev beat plain BM25 9x at matching tools to agent tasks across 3,000+ endpoints, positioned as a retrieval proxy layer exposing only search/call/schema-lookup rather than every tool schema.
- [Mahesh Nani — how Jev makes structured output faster](https://x.com/maheshnani122/status/2102239463028265387) - A mechanics explainer: parallel constrained decoding over a known JSON schema plus KV-cache prefill reuse, instead of generating structured output token by token.
- [Mahax — Jev engineering is a new layer, not cheaper routing](https://x.com/Mahaximus_/status/2102465392119570772) - Argues Jev is a separate decision layer sitting under LLM-generated work rather than a cheap LLM substitute, with cost examples: 1,018 papers classified for $0.08, 500 emails triaged for 3.5 cents.
- [Xiaofan Wu — a production playbook for typed decision models](https://x.com/xfanwu/status/2102408991783436645) - Three insertion points (upstream router, midstream execution gate, downstream verifier), three primitives (Choice/Score/Bool), and a 7-step rollout checklist; stresses Jev is "format-immune, not truth-immune."
- [Deokhyun — replacing MCP tool-calling with a Jev decision layer](https://x.com/evanyi_81/status/2102230224427753513) - Proposes API Registry + JEV Decision + Direct Executor in place of exposing large MCP tool schemas to the LLM, using Jev to pick which raw API to call directly.
- [OrcaRouter — reproducing Jev, and where the "open source beat it" claims fall apart](https://x.com/OrcaRouter/status/2102318172577911068) - Confirms Jev's bounded-answer-space insight but shows the open-source "beats Jev" benchmarks are in-distribution only (0.769 in-distribution vs. 0.541 out-of-distribution on the same checkpoint); finds data volume, not architecture, is the real lever (1,200→123,475 examples raised OOD score from 0.4069 to 0.5498).
- [Yarrow — stress-testing Jev on 48 real corporate-disclosure cases](https://x.com/Yarrow_ai/status/2102226848436645902) - Classification was reliable (48/48) but judgment wasn't: 10/48 false "No"s on unmentioned outcomes, re-running identical inputs changed a field in 8/48 cases, and just reordering input paragraphs flipped the result in 20/48 cases.
- [Eastwood — Jev loses to Kimi-K2 and fine-tuned Qwen3-14B on SemEval sentiment](https://x.com/Tsj_estwld/status/2102305073888116870) - Across all 10 SemEval-2026 DimABSA ST1 test sets, Jev went 0-10 against one-shot Kimi-K2 Thinking and 3-7 against a fine-tuned Qwen3-14B.
- [SYNTHLEX — the $200M model that got reproduced in 5 days](https://x.com/SYNTHLEX_/status/2102411667598356656) - Tallies 10,294 stars across 11 independent Jev clones with zero monetization, and argues the real moat isn't the architecture but calibration data — the record pairing a confidence score with what actually happened.
- [Tuana — Jev vs. tabular foundation models](https://x.com/tuanacelik/status/2102775182834426099) - Jev reads a row as text and predicts from world knowledge without fitting to your data, unlike a tabular foundation model like TabPFN that predicts from the labelled rows you pass in.
- [Matt Gunter — "classification is not a decision"](https://x.com/MatthewEGunter/status/2102877302237626804) - A five-point architectural critique: Jev's fixed option set, inability to reframe or fetch missing facts, and silent failure mode make a growing graph of Jev-gated if-statements tech debt, not a decision system.
- [void — the threshold is part of the prompt](https://x.com/sakevoid/status/2102896039678382177) - Ran 154 shell commands through 12 phrasings of the same danger-check question: accuracy stayed 94.8-100% throughout, but the decision threshold that matched a 0.5 cutoff moved from 0.14 to 0.68 depending on phrasing.
- [BourneS — 164 tracked Jev/decision-model projects](https://x.com/bourneshao/status/2102691360222351798) - A census of the six-day-old clone race: the winning pattern splits the agent (small model for text, Jev for the operation/element), and Jev-1.13 itself scores 0.045 ECE on 2,000 decisions, with 93.7% accuracy on the 24.5% of cases it's 90%+ confident on.
- [Prasenjit Sarkar — the Redis-in-front-of-Postgres pattern](https://x.com/stretchcloud/status/2102676090066231705) - Jev triaged 384 news headlines in 24.9s for $0.19 versus Claude Opus 5 completing 4 of 384 for 77 cents — roughly 390x cheaper per headline — framed as agent orchestration catching up to a pattern every layer of computing eventually grows.
- [Prasenjit Sarkar — code review's real bottleneck isn't the model](https://x.com/stretchcloud/status/2102894026219266265) - Jev scanned a 0.5M-line codebase for 12,938 findings in two minutes for $0.89, feeding an always-on Claude Opus 5.5 refactor loop; argues Jev's structurally-typed output removes the triage cost that dominates AI code-scanning economics.
- [WquGuru — Jev vs. its clones, head to head](https://x.com/wquguru/status/2102781168437567638) - On the same 20-question set: Jev 20/20, AnyJev (Qwen3-4B) 95%, Laya 65%, djev (Mac, 4-bit) 35% — and reversing djev's option order flipped 19 of its 20 answers.
- [生き残るための3K — the MacBook Air that beat the cloud](https://x.com/ikinokore_3k/status/2102593158681186391) - Konstantin Gladych's team raced local Laya against cloud Jev at Tetris on a 16GB MacBook Air and clocked Laya 11x faster, though replies note the gap may be round-trip latency rather than raw speed.

## Contributing

Contributions welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first. In short: every entry needs a link that resolves to a real, live project that is actually about Jev — not just a name mentioned in a tweet.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work.
