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

## About Jev

- [typesafe.ai](https://typesafe.ai) - TypeSafe AI's homepage.
- [typesafe.ai/Jev](https://typesafe.ai/Jev) - Product page for Jev.
- [Launch announcement](https://x.com/CompleteSkeptic/status/2099925682726002904) - Diogo Almeida (co-inventor of RLHF and InstructGPT at OpenAI) introduces Jev: a "System 1" model claimed to be 20-200x faster and 40-400x cheaper than generative frontier models for decision-shaped tasks. 32K context window; no image/audio input; cannot write code or prose by design.
- [typesafe-ai/skills](https://github.com/typesafe-ai/skills) - Official agent skills for building with the System One API. Install via `npx skills add typesafe-ai/skills --skill typesafe-ai`, or as a Claude Code plugin with `claude plugin marketplace add typesafe-ai/skills`.
- [typesafe-ai/system-one-adapter-python](https://github.com/typesafe-ai/system-one-adapter-python) - TypeSafe's own official drop-in adapter: swap `TypeSafeClient` for OpenAI/Anthropic/compatible backends to compare Jev against chat models using the same code.
- [typesafe.ai/blog/introducing-system-one-models-and-jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev) - TypeSafe's own announcement post for System One models and Jev.
- [docs.typesafe.ai](https://docs.typesafe.ai/introduction) - Official API docs for the System One / Jev endpoint.
- [InfoQ — TypeSafe AI Releases Jev](https://www.infoq.com/news/2026/10/typesafe-ai-jev-released/) - News write-up of the release of Jev as a decision-only model that returns typed probabilities instead of text.
- [The Information — Jev Fervor Leads to Talk of Big Valuation Boost](https://www.theinformation.com/newsletters/dealmaker/jev-fervor-leads-talk-big-valuation-boost) - Reports TypeSafe AI is in talks with investors to raise $1 billion or more at a valuation above $10 billion.

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
- [SupersonicLabs/Julia-1](https://huggingface.co/SupersonicLabs/Julia-1) - A 144M-parameter Apache-2.0 decision model on mmBERT-small; runs on CPU, scores 73.15% on Jev's own Typed Decisions benchmark, with a WebGPU ONNX build for in-browser inference.
- [ollaya-dev/ollaya](https://github.com/ollaya-dev/ollaya) - "Ollama for decision models": pulls and serves Laya, Decider, NLI, and GLiClass locally behind a TypeSafe-compatible API.
- [InternLM/Intern-Decision](https://github.com/InternLM/Intern-Decision) - Apache-2.0 multimodal decision models (0.8B/2B/4B on Qwen3.5) returning calibrated choice, score, and yes/no probabilities, released with training, inference, and calibration-benchmark code; the 4B averages 90.02 vs. Jev's 88.74 on seven benchmarks in the authors' own eval.
- [Remek/basal-1.0-4.5B](https://huggingface.co/Remek/basal-1.0-4.5B) - A Polish/English typed-decision model on Bielik-4.5B, inspired by Jev and returning a calibrated probability per allowed answer in one forward pass; the [rkinas/basal](https://github.com/rkinas/basal) inference engine is listed on its card.
- [PostHog/jeeves](https://huggingface.co/PostHog/jeeves) - Jeeves-9B: an Apache-2.0 Jev-like decision model on Qwen3.5-9B with a pointer head that writes a reasoning chain per question before returning calibrated probabilities.
- [autotrust/JEV-27B](https://huggingface.co/autotrust/JEV-27B) - An Apache-2.0 LoRA-plus-decision-head student of Jev 1.13 on Qwen3.8-27B, answering typed noul/choice/score questions in one forward pass.
- [tomerglick57/Jevstiller](https://github.com/tomerglick57/Jevstiller) - Distills a repeated Jev classification task into a local model on the fly, so the same call gets the same answers on your own hardware.
- [mode-io/vllm-jev](https://github.com/mode-io/vllm-jev) - Native vLLM serving for Jev-style decision models on Linux and Apple Silicon, with multimodal demos.
- [TokenRhythm/NeoHorse-Jev-4B](https://huggingface.co/TokenRhythm/NeoHorse-Jev-4B) - An Apache-2.0 4B open decision model that turns app states into structured decisions with probabilities, also published on ModelScope.
- [caiovicentino1/Eikos-27B](https://huggingface.co/caiovicentino1/Eikos-27B) - An open 27B Jev-like decision model with a 4B sibling and quantized builds, evaluated against Jev and Laya on JevBench (official runs requested).
- [avbiswas/bev-decider-0.4B](https://huggingface.co/avbiswas/bev-decider-0.4B) - A 0.4B Jev-compatible decision model that is invariant to option order by construction; 74.7% vs. Jev 1.13's 78.0% on 5,000 held-out questions.
- [r-ms/mini-jev](https://github.com/r-ms/mini-jev) - Measures what a Jev-style interface looks like on a frozen Qwen3-4B by reading option-letter logits in one forward pass instead of generating JSON.
- [rongxinzy/LightJev](https://github.com/rongxinzy/LightJev) - Trains small backbones (standard: Qwen3-0.6B) into finite-candidate decision models with CE/Brier training, evaluation, and a Hugging Face checkpoint.
- [firelex/jeff](https://github.com/firelex/jeff) - A 0.8B open "System 1" decision model with swappable LoRA adapters on one base, using the same request format as Jev; unaffiliated, and distinct from logan-markewich/jeff above.
- [feder-cr/jev](https://github.com/feder-cr/jev) - "jevos": an open-source alternative to Jev for yes/no decisions that runs on your laptop.
- [Shanghua-Gao/RSI-Jev](https://github.com/Shanghua-Gao/RSI-Jev) - Typed-decision models (noul/choice/score) trained by a self-improving loop of AI agents, released with checkpoints, the code that produced them, and every failed version; includes a vision variant.
- [perplexity-ai/pplx-decider-v1-27b](https://huggingface.co/perplexity-ai/pplx-decider-v1-27b) - Perplexity's Apache-2.0 decision model fine-tuned from Qwen3.8-27B and served through its Decisions API, which it reports scores higher than Jev on its own benchmarks.
- [Cloudflare/clef](https://huggingface.co/Cloudflare/clef) - Cloudflare's Apache-2.0 Clef decision models, Jev-API compatible with a faster [clef-flash](https://huggingface.co/Cloudflare/clef-flash) variant, announced alongside an RL fine-tuning platform in [the launch post](https://blog.cloudflare.com/clef-decision-models/).
- [strands-labs/strands-decider](https://github.com/strands-labs/strands-decider) - AWS's Apache-2.0 Strands Decider, a small local decision model (2B on Qwen3.5) that picks among options or rates on a scale with a calibrated confidence, released with its training recipe.
- [autotrust/JEV-27B-VL](https://huggingface.co/autotrust/JEV-27B-VL) - The multimodal sibling of JEV-27B above: an Apache-2.0 open-weight decision model that takes image input.
- [OmniJev/OneJev-0.8B](https://huggingface.co/OmniJev/OneJev-0.8B) - An Apache-2.0 multimodal System One decision model on Qwen3.5-0.8B; the [OneJev in the Browser](https://huggingface.co/spaces/shreyask/onejev-web) demo runs it on WebGPU without the image leaving the page.
- [telepatia-ai/hertz-1](https://huggingface.co/telepatia-ai/hertz-1) - A Jev-style typed-decision model for Portuguese and Spanish audio, pairing a Parakeet-TDT encoder with a frozen Laya decision head so it decides without transcribing first.
- [Maincode/matilda-jev-v1](https://huggingface.co/Maincode/matilda-jev-v1) - Maincode's Apache-2.0 "Matilda Jev" on Qwen3.8-27B: a one-pass decision model that scores choice, yes/no, and ordered score questions over text, JSON state, or images, with a 255-option readout.
- [aryanbains/Rook-V1](https://huggingface.co/aryanbains/Rook-V1) - An Apache-2.0 research preview adding a LoRA adapter and decision head to Decision 2.0 Lux 9B for self-hosted bounded choices; the owner reports 67.75% vs. Jev's 68.00% on four matched workflows, without raw runs.
- [TheREZOR/TinyDecide](https://huggingface.co/TheREZOR/TinyDecide) - A 10.4M-parameter, 4-bit Apache-2.0 Jev-style decision model on ELECTRA-small that answers several typed questions in one encoder pass and runs on an ESP32-S3 microcontroller.
- [gai-labs/reflex-1](https://huggingface.co/gai-labs/reflex-1) - Reflex-1: a 421M-parameter Apache-2.0 dual-encoder decision model that picks among per-request choices in one forward pass on a laptop CPU, reporting 96.09% on SciQ and 92.93% on Banking77 in the authors' own tests.
- [TextCortex/clef-cybersecurity](https://huggingface.co/TextCortex/clef-cybersecurity) - An Apache-2.0 fine-tune of Cloudflare's clef-flash for prompt-injection and data-exfiltration detection that TextCortex reports beats Jev on prompt injection hidden in large PDFs.
- [Rizzo-AI-Academy/rizzo-flow](https://github.com/Rizzo-AI-Academy/rizzo-flow) - An open, local take on Jev that returns typed decisions from an LLM without generating a single token.
- [Yinsongxu/LLM2Jev](https://github.com/Yinsongxu/LLM2Jev) - Turns local language models into Jev-style structured decision models over text and images using prefill alone, with no token-by-token decoding.
- [mohit67890/imajev](https://github.com/mohit67890/imajev) - An open Jev-style typed-decision model that also takes images: a photo, app state, and typed questions go in and calibrated probabilities come out, locally.

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
- [dzhng/jevgrep](https://github.com/dzhng/jevgrep) - A CLI for coding agents that uses Jev to find relevant files and source context by asking what the code does, instead of matching keywords.
- [leepokai/jev-guard](https://github.com/leepokai/jev-guard) - An auto-mode wrapper for coding agents (Claude Code, Codex, Copilot, Gemini, Cursor, Pi, OpenCode, ACP) that risk-scores every tool call with Jev, flags prompt injection in tool results, and vets skills/plugins before they run.
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
- [muthuishere/jevx](https://github.com/muthuishere/jevx) - An agent-skill CLI for Claude Code/Codex/any agent giving yes/no/unsure and pick-one/rating answers from a Jev-style model, with exit-code contracts and hook-based guardrails.
- [shaharia-lab/jev-cli](https://github.com/shaharia-lab/jev-cli) - A command-line tool for Jev: ask yes/no, multiple-choice, and rubric questions about text and get calibrated probabilities as shell exit codes, JSON, or MCP tools.
- [caiovicentino/jev-shield](https://github.com/caiovicentino/jev-shield) - A semantic MCP firewall powered by Jev that screens every tool call, result, and description with calibrated System One verification.
- [egma-ai/jev-code-reviewer](https://github.com/egma-ai/jev-code-reviewer) - Reviews agent-generated PR behavior rather than just diffs, using Jev to prioritize what needs human attention.
- [abhixhek/jevcal](https://github.com/abhixhek/jevcal) - Calibrates, thresholds, and drift-checks typed decision models like Jev against an LLM teacher.
- [ThinkFlowLab/system1-agents](https://github.com/ThinkFlowLab/system1-agents) - Uses System 1 decision models (Jev, Laya, Cua-S1) as the fast-decision "brain" for browser-use, computer-use, game, and robotics agents.
- [sumleo/prompt2jev](https://github.com/sumleo/prompt2jev) - An agent skill and CLI that turns natural language, an LLM prompt, or the code that runs one into typed Jev questions and a runnable script.
- [ringzerosec/jev-runtime-security](https://github.com/ringzerosec/jev-runtime-security) - Kernel-level, syscall-time policy enforcement for AI coding agents that can call Jev as an optional check.
- [CommandCodeAI/cmd-mod-jev-nudge](https://github.com/CommandCodeAI/cmd-mod-jev-nudge) - A Command Code mod where Jev judges whether the agent stopped with work left and nudges it to keep going.
- [everafterlabs/jes](https://github.com/everafterlabs/jes) - Open-source guardrails for AI agents that check prompts, retrieved content, tool calls, tool results, and responses for prompt injection, jailbreaks, and secret/PII leaks using decision models like Jev.
- [gulbaki/jev-llm-guard](https://github.com/gulbaki/jev-llm-guard) - A contextual OWASP LLM Top 10 guardrail powered by Jev, with a Turkish interactive demo.
- [WXK-AI/jev-opus](https://github.com/WXK-AI/jev-opus) - A CLI and Claude Code plugin that runs Claude Opus 5.5 with the effort level re-decided at every step by Jev while keeping the prompt cache intact.
- [valentynkit/jev-belay](https://github.com/valentynkit/jev-belay) - A Claude Code Stop hook that blocks an unverified "done": it reads the transcript for evidence, asks Jev once, and fails open on everything else.
- [shimo4228/jev-skill-router](https://github.com/shimo4228/jev-skill-router) - A reference Claude Code hook that asks Jev which installed skill fits each prompt and logs the answer without acting on it.
- [abgregs/jev-skill-router](https://github.com/abgregs/jev-skill-router) - A separately built skill router for coding agents that asks Jev one Noul per skill, sharded in parallel, distinct from shimo4228/jev-skill-router above.
- [suenot/codex-jev-router](https://github.com/suenot/codex-jev-router) - A portable setup that lets Jev pick the model for each Codex subagent for cost-aware routing, with English and Russian instructions.
- [valentynkit/jev-commit](https://github.com/valentynkit/jev-commit) - A pre-commit hook where one Jev call judges whether the commit message matches the staged diff and flags debug leftovers and scope creep.
- [luantak/is-malicious](https://github.com/luantak/is-malicious) - A Node CLI that sends a codebase's source, config, build, and CI files to Jev and points to suspicious lines before you run unfamiliar code.
- [can1357/jegrep](https://github.com/can1357/jegrep) - A Rust semantic grep that scores files with Jev yes/no probabilities and returns file and line ranges with no embedding index or daemon, distinct from dzhng/jevgrep above.
- [kierandotai/jev-scout](https://github.com/kierandotai/jev-scout) - An MCP server where Jev scores every search query, result, and fetched page an agent touches for relevance and credibility.
- [allebee/pytest-jev](https://github.com/allebee/pytest-jev) - A pytest plugin for plain-English assertions on LLM output, passing only when Jev's calibrated probabilities clear a threshold.
- [luobosibing2/dsh-jev-plugin](https://github.com/luobosibing2/dsh-jev-plugin) - A DeepSeek Harness plugin adding Jev as a System One decision layer for agent selection, supervision, corrections, and approvals.
- [abhishek085/jevcontrol-hermes](https://github.com/abhishek085/jevcontrol-hermes) - A beta plugin for Hermes Agent where a small decision model handles secret-leak checks, memory filing, and safe-command approvals in about a tenth of a second.
- [tsale/jevline](https://github.com/tsale/jevline) - A proof of concept that starts from one confirmed-malicious process and has Jev link related telemetry into an incident timeline and evidence table; the author reports 40 of 41 attack-chain processes found in 21 seconds for $0.11 on one lab intrusion.
- [Ubayed-Bin-Sufian/GitReview-Radar](https://github.com/Ubayed-Bin-Sufian/GitReview-Radar) - "PR-Pulse": syncs open GitHub pull requests, evaluates each with Jev into an actionable state, and shows a prioritized review queue on an AWS-hosted dashboard.

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
- [lakehq/sail](https://github.com/lakehq/sail) - The Rust Spark-replacement query engine; v0.7.2 adds built-in async Jev SQL functions (`jev_noul`, `jev_choice`, `jev_score`) that return typed answers per row.
- [ollama/ollama](https://github.com/ollama/ollama/releases/tag/v0.35.0) - Ollama v0.35 adds decision-model support through a Jev-style `/v1/systemone` endpoint, with Nimble and Tev1 available to pull locally.
- [unslothai/unsloth](https://github.com/unslothai/unsloth/releases/tag/v0.1.900-beta) - Unsloth Desktop v0.1.900 can run and serve decision models such as Laya locally behind a Jev-compatible API.
- [twentyhq/twenty](https://github.com/twentyhq/twenty) - Twenty CRM's workflow builder adds a step that classifies a record into user-defined categories with a probability each, powered by Jev.
- [confident-ai/deepeval](https://github.com/confident-ai/deepeval/blob/main/deepeval/metrics/jev_eval/jev_eval.py) - DeepEval's JevEval metric, which scores outputs from Jev's decision probabilities (weighted mean with confidence), in Python and TypeScript.
- [marcreichel/laya-php](https://github.com/marcreichel/laya-php) - A Laravel-ready PHP SDK for Laya (a Jev alternative), classifying text in 100+ languages self-hosted.
- [botassembly/thinkthen](https://github.com/botassembly/thinkthen) - A Rust SDK and CLI (MIT, 24 language bindings) where code asks a bounded question about text and gets a typed answer back, such as yes/no/not-sure exit codes for shell scripts, running on System One models like Jev.
- [laravel/ai](https://github.com/laravel/ai) - The Laravel AI SDK ships a TypeSafe provider for classification with Jev as of v1.0.
- [cequence-io/openai-scala-client](https://github.com/cequence-io/openai-scala-client/releases/tag/v1.4.0) - The Scala OpenAI client's v1.4.0 adds Liquid's d1 as a second decision model beside its existing Jev support.
- [Liquid AI — Decision Models (d1)](https://docs.liquid.ai/lfm/models/decision-models) - Docs for Liquid's API-only d1 decision model, which serves Jev's noul/choice/score primitives at a `/decisions/v1/systemone` endpoint that the TypeSafe Python and TypeScript SDKs can call by changing the base URL.
- [Databricks — Running open-Jev in SQL on Databricks](https://www.databricks.com/blog/running-open-jev-sql-databricks) - Walks through serving an open Jev-style decision model behind Databricks SQL so rows can be classified through `ai_query`.
- [Arize AX — September 2026 release notes](https://arize.com/docs/ax/release-notes/history/2026/09-2026) - Adds Jev as a judge for high-volume structured evaluations.
- [tnaftali/s1-tui](https://github.com/tnaftali/s1-tui) - A terminal UI for testing System One typed decisions (noul/choice/score) that lets you switch live between local Laya on MLX and hosted Jev on the same input.
- [carldaws/hunch](https://github.com/carldaws/hunch) - Probabilistic control flow for Ruby and Rails, branching on a typed Jev answer such as `Hunch.likely?("fraudulent", given: order)`.
- [dfinke/Jev](https://github.com/dfinke/Jev) - A PowerShell module for asking Jev typed yes/no, choice, and score questions and acting on the structured answers in scripts.
- [hfgolino/llmClassificR](https://github.com/hfgolino/llmClassificR) - An R text-classification toolkit that adds Jev calls from pure R (single-label, multi-label, and ordinal rating) alongside calibration tools and bag-of-words baselines.

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
- [michaelswissa/jevry](https://github.com/michaelswissa/jevry) - An MIT-licensed desktop browser agent for website tasks, cited research, and supported games.

## Data & Retrieval

- [realZachi/pg-jev](https://github.com/realZachi/pg-jev) - A PostgreSQL extension for filtering, classifying, and sorting rows with natural language — no vector DB required.
- [superagents-lab/jev-search](https://github.com/superagents-lab/jev-search) - Web search built on Jev for source selection, query understanding, and relevance ranking.
- [kylemclaren/jevsearch](https://github.com/kylemclaren/jevsearch) - A shadcn/ui site-search block that shows keyword hits instantly, then re-ranks the top 20 with one Jev request (a Noul per page plus a Choice over all of them), distinct from superagents-lab/jev-search.
- [jexp/neo4jev](https://github.com/jexp/neo4jev) - Traverses a Neo4j graph by having Jev classify which neighboring relationship to follow next.
- [jerryjliu/docjev](https://github.com/jerryjliu/docjev) - OSS library that uses Jev plus LiteParse (and optional LlamaParse OCR) to classify documents and split multi-document packets by natural-language category rules; ~6x faster than GPT-5.6-luna at equivalent accuracy.
- [kylemclaren/jevpdf](https://github.com/kylemclaren/jevpdf) - Searches a PDF by meaning in the browser: pdf.js extracts each line locally and Jev answers one Noul per line, highlighting matches page by page ranked by probability.
- [pinecone-io/using-typesafe-and-pinecone](https://github.com/pinecone-io/using-typesafe-and-pinecone) - Pinecone's reference integration reranking retrieved candidates against natural-language criteria with Jev instead of a long-context LLM call; ~5x faster and ~43x cheaper than Claude Opus 5 on the same 200-candidate rerank in their benchmark.
- [lancedb/lancedb](https://github.com/lancedb/lancedb/blob/main/python/python/lancedb/rerankers/typesafe.py) - LanceDB's built-in TypeSafe reranker, benchmarked against 19 reranker configurations across 5 datasets (HotpotQA Hit@1 63.5% to 72.9% with Jev).
- [assafelovic/gpt-researcher](https://github.com/assafelovic/gpt-researcher/blob/main/gpt_researcher/context/jev_filter.py) - GPT Researcher's Jev context filter, swapped in for embedding similarity; the maintainers report 73% vs. 46% relevant context and reports preferred 15-3 in blind comparisons.
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
- [giuliosmall/pg_typesafe](https://github.com/giuliosmall/pg_typesafe) - A pre-alpha C PostgreSQL extension calling Jev directly from SQL for categorical classification, a separately built alternative to realZachi/pg-jev above.
- [chenmingtang830/jevgraph](https://github.com/chenmingtang830/jevgraph) - A schema-guided document-to-graph pipeline that replaces open-ended triple extraction with typed Jev relation decisions and evidence-backed candidate graphs.
- [naogify/japanese-person-name-detector](https://github.com/naogify/japanese-person-name-detector) - A TypeScript module that judges whether a string looks like a Japanese personal name by combining regex rules, a name dictionary, and an optional Jev call.

## Content, Media & Moderation

- [trungdq88/youtube-sponsor-detection](https://github.com/trungdq88/youtube-sponsor-detection) - Detects YouTube sponsor segments from live audio and transcript, powered by Jev.
- [ChetasLua/jevmeter](https://github.com/ChetasLua/jevmeter) - Scores every sentence of a video against a chosen angle and renders it as a scored highlight reel.
- [brainstormity/Jev-Moderation-Bot](https://github.com/brainstormity/Jev-Moderation-Bot) - Discord moderation for spam and phishing links.
- [gaborishka/jev-wrapped](https://github.com/gaborishka/jev-wrapped) - Judges a Telegram channel's year of posts with Jev and renders a "wrapped" summary card.
- [stas4000/jev-scroll](https://github.com/stas4000/jev-scroll) - A Chrome extension that labels every X/Twitter post with a Jev decision while scrolling.
- [achimala/jev-paint](https://github.com/achimala/jev-paint) - Turns Jev into a parallel pixel-color predictor: brush width tracks Jev's per-pixel confidence.
- [tomita-anri/jev-ad-blocker](https://github.com/tomita-anri/jev-ad-blocker) - A Chrome extension that uses Jev to identify and remove only ads from a page.
- [fazlerocks/jevmail](https://github.com/fazlerocks/jevmail) - Open-source, read-only Gmail triage that sorts an inbox into Needs Reply/Updates/Promos/Sales/Spam with Jev, ~1,000 emails/minute for 3 cents.
- [TREMOR — Jev Rank](https://www.tigzig.com/post/tremor-news-jev-rank-oct2026) - Scores about 800 headlines from 64 feeds from 0 to 100 against your interests with Jev in under 2 seconds and sorts the news page by that score.
- [gnipbao/jev-highlight-cutter](https://github.com/gnipbao/jev-highlight-cutter) - A skill and Python CLI that scores interview and podcast transcript segments with Jev, picks non-overlapping highlights within a target length, and cuts them locally with FFmpeg.

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
- [rokbenko/quackd](https://github.com/rokbenko/quackd) - A CLI for controlling one or many robots with an LLM brain each, with an optional Jev (or Laya/Kev) decision model that answers the turns that are a choice among skills the robot already has.

## Finance & Trading

- [jarrodwatts/jev-trader](https://github.com/jarrodwatts/jev-trader) - Makes one AI trade decision per Monad block on Kuru MON-USDC; defaults to mock/dry-run without a configured private key.
- [svmanth/jmarket](https://github.com/svmanth/jmarket) - A Chrome extension giving Jev's own forecast on Polymarket-style questions instead of the crowd's.
- [OpenByteInc/QuantDinger](https://github.com/OpenByteInc/QuantDinger) - A self-hosted, open-source AI trading OS (strategy research, backtesting, paper/live execution) that gates trade entry behind a Jev System One decision filter.
- [aowang-ai/jev-trade](https://github.com/aowang-ai/jev-trade) - A live Jev-driven trader on Hyperliquid, a separate build from jarrodwatts/jev-trader above.

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
- [sumleo/RLCDAlignBench](https://github.com/sumleo/RLCDAlignBench) - "Just Ask Jev": 44 alignment-failure-detection benchmarks for RLCD-style zero-shot detectors like Jev, matching GPT-4o-mini on StrongREJECT at a fraction of the cost.
- [jesyspa/jev-lean](https://github.com/jesyspa/jev-lean) - A Lean proof-automation harness that uses Jev to select lemmas and tactics.
- [multimodalart/jev-decision-index](https://huggingface.co/spaces/multimodalart/jev-decision-index) - The Jev Decision Index: a Hugging Face Space benchmarking and tracking dozens of open reproductions of Jev on one shared suite.
- [kachar/jev-tool-search](https://github.com/kachar/jev-tool-search) - Benchmarks BM25, embeddings, rerankers, and Jev for agent tool search on 525 real MCP tools, plus an experimental Jev search engine.
- [patchy631/jev-as-judge](https://github.com/patchy631/jev-as-judge) - A tutorial that scores ten synthetic refund-support traces with Jev's yes/no and ordinal answers in one request and logs them as a Comet Opik experiment, with an offline demo.

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
- [Martin Casado (a16z) — why the labs missed it](https://x.com/a16z/status/2103911378222477377) - Argues frontier labs are building "beings that speak," so a model built to choose between a fixed set of options instead of generating text sat outside what they were optimizing for.
- [pukerrainbrow — the practitioner pushback, point by point](https://x.com/pukerrainbrow/status/2103758223602008538) - Notes Jev is architecturally a zero-shot classifier that's existed since 2019, that its "can't hallucinate" claim only guarantees schema-valid output rather than correctness, and cites a benchmark where a local bge-small-embedding-plus-logistic-regression model beat it on Banking77 (93.3% vs. 83.2%) at a fraction of the latency.
- [fluixoo — TypeSafe's own 193.6x claim, retested](https://x.com/fluixoo/status/2103755424117686645) - An independent 791-decision test measured Jev at 3.6x faster than GPT-5.6 Terra (not TypeSafe's advertised 193.6x) and several accuracy points behind on hard cases, but found a cascade — routing only the uncertain 19-23% of decisions to Terra — matched Terra's accuracy at roughly a quarter of its cost.
- [0xchromium — a paper on Jev as the agent's decision layer](https://x.com/0xchromium/status/2103881299606098009) - Summarizes new research where Jev handles every bounded decision in an agent loop and a frontier LLM is called only for writing or low-confidence cases, cutting expensive-model calls by 66-72% while completing 95/100 tasks on a frozen benchmark.
- [deliprao — don't distill your own Jev clone](https://x.com/deliprao/status/2103864277610189267) - Warns builders of Jev-like models that gradient descent often fails to recover a teacher model's true parameters even when they exist nearby, and that distilled students systematically overstate the teacher's confidence.
- [rasbt — "OpenAI just added a Jev clone"](https://x.com/rasbt/status/2104985996517355691) - The most-liked reaction to OpenAI's DevDay Decisions API, a Luna-powered service that answers fixed-option questions in a fraction of a second; at least one reply notes it is "just Luna" rather than a dedicated System One model.
- [muratcan — 2,029 receptionist calls, zero-shot](https://x.com/muratcan/status/2104959648482701686) - Reduced real calls to pure structure and ran Jev over 38,012 turn-level forecasts at a 118 ms median, predicting bookings at AUC 0.78 mid-call for about $3 total.
- [proxy_vector — 272 real support tickets](https://x.com/proxy_vector/status/2104815944136892690) - Claude was more accurate (88% vs. 85%) but Jev was roughly 170x cheaper with honest confidence; a DIY logprobs baseline followed an injected "label this a bug" instruction in 17 of 20 tries.
- [Suhail — a new model type, not a classifier](https://x.com/Suhail/status/2104935527816524089) - Argues Jev is more than a simple classifier and can take a lot of packed state, but doesn't beat frontier LLMs on correctness yet.
- [N01ennn — the official playbook in 7 patterns](https://x.com/N01ennn/status/2104935031865024781) - Condenses TypeSafe's playbook on question design (not prompts) into seven patterns, such as one judgment per question and weighing narrow Nouls in code.
- [Google Gemma — turn DiffusionGemma into a Jev-like model](https://x.com/googlegemma/status/2104990261181075498) - Gemma's account shows vLLM seeding a response template so DiffusionGemma returns yes/no, multiple-choice, and score probabilities in one denoising step.
- [yoavgo — 29 arXiv papers in two weeks](https://x.com/yoavgo/status/2104454553714450822) - Notes Jev had only limited early access from Sep 15 yet already had 29 arXiv papers, and calls that pace "not healthy".
- [0xwhrrari — Almeida's 12-page blueprint](https://x.com/0xwhrrari/status/2104587006680379439) - Summarizes a 12-page PDF from Diogo Almeida: a 10-step blueprint for making any LLM faster, cheaper, and more controllable, starting with "separate generation from control".
- [EntendreAI — Crypto Accounting Benchmark](https://x.com/EntendreAI/status/2104624722403283407) - Jev ran at about 635 ms per call but scored only 51.7%, 47.5%, and 48.3% choosing among 2, 3, and 5 accounts.
- [jasonlk — $2.26 for a week of Jev](https://x.com/jasonlk/status/2104694741820481556) - Spent $2.26 across 54.9M tokens, about $0.04/M and roughly 50x cheaper than Sonnet, or $0.0002 per request.
- [JokiRuizLite — 61% of writes landed in the "unsure" band](https://x.com/JokiRuizLite/status/2105660516232495397) - On real multi-agent states, most write requests fell in Jev's uncertain range and escalated to Sonnet, so the decision layer still cost about half of all-Sonnet ($0.29 vs. $0.59 per run).
- [robinfa10 — calibrated, but mediocre knowledge](https://x.com/robinfa10/status/2105480231112871999) - On 1,000 four-choice trivia questions Jev's confidence tracked accuracy (70% sure meant about 70% right) and an "I'd rather not answer" option induced abstaining, though it was right only about 66% of the time.
- [RenDaichi147380 — Jev vs. GPT-6 Luna on 113 cases](https://x.com/RenDaichi147380/status/2105615520284455260) - A Japanese write-up where Luna was more accurate overall (81-99% vs. Jev's 67%), but Jev reached 98% at confidence of 0.9 or more and gave 0 changed answers across 15 identical runs against Luna's 5.
- [sh_reya — per-row API calls don't fit batch work](https://x.com/sh_reya/status/2105737403306762350) - Argues a per-row decision-model API is a poor fit for batch filtering, estimating Qwen3-4B on one H100 could filter 5,000 reviews in about 6.6 seconds.
- [ryanflorence — $21 overnight on Jev tokens](https://x.com/ryanflorence/status/2105676555909570980) - Polling Jev every 500 ms per game bot burned $21 overnight; the fix is to call it only on role-relevant events.
- [KhuyenTran16 — why Jev isn't PydanticAI](https://x.com/KhuyenTran16/status/2105659858494136506) - Pydantic validates output after a model responds, whereas Jev constrains the decision beforehand by scoring only the allowed answers.
- [ElArk — what "calibrated" means for System One models](https://elarkk.github.io/blog/jev-probabilities-calibration) - A blog post on when Jev's probabilities can be trusted, explored through calibration and ensembles.
- [Robert Schwentker — Jevathon hacks that deserve encores](https://www.linkedin.com/pulse/jevathon-hacks-deserve-encores-robert-schwentker-nhhvc/) - A roundup of TypeSafe's Jevathon projects, noting several teams independently built a pre-execution checkpoint for agent actions.
- [Fastino — Introducing GLiDE](https://fastino.ai/blog/introducing-glide-the-first-thinking-decision-model) - Announces a decision model that turns reasoning on only when its top answer is uncertain, reporting 64.81 on Decision Index 0.2.1, 6.9 points above Jev, in the vendor's own evaluation.
- [Sentdex — decision models for robotics](https://x.com/Sentdex/status/2107513551539617948) - After testing decision models including vision-capable Clef, finds them not smart enough to replace specialised RL/ACT/VLA policies or larger multimodal LLMs, since a call to the decision model is still needed.
- [imryven — the Jevons paradox for decisions](https://x.com/imryven/status/2107583659704225909) - One task cost about 3 cents on a frontier model vs. about 0.04 cents on Jev (76x cheaper), yet argues cheaper decisions may still raise total spend.
- [HackerNoon — Using Jev to reduce our reasoner cost by 30%](https://hackernoon.com/using-jev-to-reduce-our-reasoner-cost-by-30percent) - Uses Jev for document routing and source recall in a production insurance-claims AI workflow to cut reasoner cost.
- [Stephen Solka — Can Jev save my inbox?](https://huggingface.co/blog/stephen-solka/use-jev-to-delete-fundraising-emails) - A Hugging Face post testing Jev on deleting fundraising emails, with the 100-email evaluation results.
- [radius5 — a Jev and Clef gate for image generation (Zenn, Japanese)](https://zenn.dev/radius5/articles/20261004-j3v7cl3f) - A two-stage Jev plus Clef gate in front of an image-generation service to avoid paid-but-refused requests, covering thresholds, caching, and failure handling.
- [Data/AI Engineer — Build a Jev judge in MLflow](https://dataaiengineer.substack.com/p/build-a-jev-judge-in-mlflow-then) - Builds a Jev scorer with MLflow, tests the Python wiring, and measures false acceptances before replacing an existing evaluator.

## Contributing

Contributions welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first. In short: every entry needs a link that resolves to a real, live project that is actually about Jev — not just a name mentioned in a tweet.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work.
