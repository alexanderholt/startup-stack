# AEO Playbook

Last scanned: 2026-10-27

General best practice for getting a site found, cited, and used by AI answer engines and agents. `/aeo` refreshes this file on every call. Each practice has two ratings, defined in `SKILL.md`: **Consensus** (are practitioners converging on it) and **Evidence** (does data show it works). **This file is public. Never add anything about a specific company's site here.** Site-specific notes go in `site-notes.md` (gitignored).

## Reachability

| Practice | Consensus | Evidence | Source |
|---|---|---|---|
| Allow AI search and user-fetch bots in robots.txt: OAI-SearchBot and ChatGPT-User (OpenAI), Claude-SearchBot and Claude-User (Anthropic), PerplexityBot, plus Googlebot and Bingbot. Blocking OAI-SearchBot removes a site from ChatGPT search answers. | Wide | Confirmed | [OpenAI bot docs](https://developers.openai.com/docs/gptbot); [SEJ on Anthropic's three bots](https://www.searchenginejournal.com/anthropics-claude-bots-make-robots-txt-decisions-more-granular/568253/) |
| Treat training bots (GPTBot, ClaudeBot, Google-Extended) as a separate decision. Blocking them does not block search or user fetches. | Wide | Confirmed | Same as above |
| Google AI Overviews and AI Mode use the normal Google index. A page must be indexed and eligible for snippets. Optimizing for them is SEO, not a separate discipline. | Wide | Confirmed | [Google: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features) |
| Put core content in server-rendered HTML. Several AI crawlers do not execute JavaScript, so client-rendered content may be invisible to them. | Wide | Converging | [Vercel/MERJ, "The rise of the AI crawler"](https://vercel.com/blog/the-rise-of-the-ai-crawler) (Dec 2024): major AI crawlers fetch JS files but do not run them; Googlebot and AppleBot are exceptions. Re-verify per crawler. |

## Readability and citability

| Practice | Consensus | Evidence | Source |
|---|---|---|---|
| Google says AI features need no special schema, no special markup, and no content chunking for AI. | Some | Confirmed | [Google: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features) |
| Structured data must match visible page content. | Wide | Confirmed | Google Search Central structured data guidelines |
| Google AI features use "query fan-out" (many related sub-searches), so coverage of the subtopics around a question matters, not just the head query. | Some | Confirmed | [Google: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features) |
| Adding cited sources, quotations, and statistics to content raised visibility in generative engine answers in controlled tests. | Wide | Confirmed (lab setting) | [Aggarwal et al., "GEO: Generative Engine Optimization," KDD 2024](https://arxiv.org/abs/2311.09735), up to 40% visibility gain. The tests ran in a lab; real-engine effect sizes are unverified. |
| Open each section with a self-contained direct answer, then supporting detail. | Wide | Untested | Widely recommended across practitioner guides ([Search Engine Land](https://searchengineland.com/mastering-generative-engine-optimization-in-2026-full-guide-469142)); no independent measurement found |
| Show a visible "last updated" date and keep core pages current. | Wide | Untested | Practitioner guides; vendor citation studies |
| Keep company facts (name, description, pricing, leadership) consistent across your site and third-party sites, and earn mentions on trusted sites. | Wide | Untested | Practitioner consensus; mechanism plausible (engines retrieve third-party pages), effect size unmeasured |
| State facts an agent needs (pricing, eligibility, contact path) in plain text, not images, PDFs, or gated widgets. | Some | Untested | INFERENCE from reachability findings; no direct study found |

## Agent-facing surfaces

| Practice | Consensus | Evidence | Source |
|---|---|---|---|
| llms.txt: publication has grown to roughly 10% of domains, but AI search crawlers rarely request it, and studies find no link to citations. Google says its search does not use it. Some evidence that coding agents and docs tools fetch it. Cheap to add if you have developer docs. Do not expect AI search gains. | Wide | Contested | [Optimizely](https://www.optimizely.com/field-notes/articles/does-llms-txt-work); [SE Ranking / Ahrefs summaries via 1clickreport](https://www.1clickreport.com/blog/llms-txt-evidence-2026) (vendor-reported) |
| FAQ / HowTo schema "for AI": many guides recommend it; Google says no special schema is needed for AI features. | Wide | Contested | Google doc above versus practitioner guides |
| NLWeb (an /ask endpoint plus an MCP server built on your Schema.org and RSS data). Quality depends on schema quality. Code is still described as proof of concept. Wait for agent demand in your own logs. | Rare | Untested | [Microsoft](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/the-future-of-ai-optimize-your-site-for-agents---its-cool-to-be-a-tool/4434189); [Cloudflare](https://blog.cloudflare.com/conversational-search-with-nlweb-and-autorag/); [Presenc adoption review](https://presenc.ai/research/nlweb-adoption-2026) |
| Public MCP server or WebMCP actions for agent tasks. Real security risk (tool poisoning) on the agent side. Only worth building when agents need to act, not just read. | Some | Untested | [NoHacks protocol overview](https://nohacks.co/blog/agentic-web-protocols) |

## Measurement

| Practice | Consensus | Evidence | Source |
|---|---|---|---|
| Track AI bot hits by user agent in server or CDN logs, and AI referral traffic in analytics. | Some | Converging | Standard practice across log studies; CDN providers expose AI-crawler reports |
| Keep a fixed set of real buyer prompts; check which sources each engine cites; repeat monthly. Answers vary by model and run, so judge trends, not single runs. | Wide | Untested | Practitioner guides; Google notes AI Mode and AI Overviews vary by model and technique |

## Changelog

- 2026-10-27: Initial baseline.
- 2026-10-27: Split ratings into Consensus (vendor checklists count fully) and Evidence (vendor studies with disclosed data count). "Emerging" became "Untested."
