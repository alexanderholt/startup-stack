# CEO Advisory Skills

**A virtual advisory board for non-technical startup CEOs, built as Claude Code skills.**

Seven expert personas, three quality tools, and a compliance workflow. Each advisor brings deep experience with early-stage startups — you summon them on demand with slash commands.

## The advisors

| Command | Role | What they do |
|---|---|---|
| `/gc` | General Counsel | Legal risk, contracts, liability, regulatory interpretation |
| `/cfo` | CFO | Financial models, pricing, fundraising, burn rate, unit economics |
| `/angel` | Angel advisor | Strategy, valuation, big decisions, honest encouragement |
| `/sales` | VP Sales | Outreach emails, follow-up strategy, objection handling |
| `/ux` | UX strategist | User workflows, information design, audience perspective |
| `/devil` | Dev team advocate | Pressure-test specs and issues before sending to your developer |
| `/coach` | CEO coach | Time management, priorities, avoidance patterns, hard truths |
| `/expert` | On-demand expert | Research, draft, analyze, or build in any domain not covered by a named advisor |

## The tools

| Command | What it does |
|---|---|
| `/expert-review` | Dispatches a domain specialist to review work you can't evaluate yourself |
| `/brand-review` | Reviews any content against your brand guide for terminology, voice, and tone |
| `/voice-check` | Scans documents for AI writing patterns and deviations from your voice profile |
| `/compliance-review` | Formal regulatory compliance assessment — produces a saved report |

## Who this is for

You run an early-stage startup. You work in Claude Code. You are not a developer — you use Claude Code to manage your business, write outreach, create specs, build financial models, and make decisions. You want consistent, expert-level thinking without having to prompt for it every time.

This is not a generic prompt pack. Each advisor has:

- **Domain expertise** calibrated to early-stage startups
- **Structural constraints** that force rigor (the CFO must separate assumptions from conclusions; the GC must cite specific regulations; the angel must state why the advice might be wrong)
- **Anti-sycophancy checks** — every advisor asks itself whether it's telling you what's true or what you want to hear
- **Cross-referral** — advisors suggest when another advisor should weigh in

## How the advisors work together

```
You:    /angel should I raise a seed round now?

Angel:  Here's my take on timing... [advice with one risk stated]
        The fundraising math is /cfo territory — worth running
        the numbers before you decide.

You:    /cfo what would a $150k raise at this stage look like?

CFO:    Assumptions (medium confidence): [labeled list]
        Conclusion: [math shown]
        One thing to flag for /gc — your SAFE terms should be
        reviewed before you sign anything.
```

Each invocation is a standalone consultation. The advisors don't persist across messages — if you want to continue a conversation with one, re-invoke the command or reference them by name.

## Install

### Step 1: Copy the skills to your project

```bash
# From your project root
cp -r path/to/ceo-advisory-skills/.claude/skills/ .claude/skills/
```

Or clone and copy:

```bash
git clone https://github.com/alexanderholt/ceo-advisory-skills.git /tmp/ceo-advisory-skills
cp -r /tmp/ceo-advisory-skills/.claude/skills/ .claude/skills/
```

### Step 2: Fill in your company context

```bash
cd .claude/skills/references
cp company-context-template.md company-context.md
```

Open `company-context.md` and fill in your company's details. Every advisor reads this file to ground their advice in your actual situation. Write constraints, not prose:

```markdown
## Company
- **Name:** Acme Corp
- **Stage:** Pre-revenue
- **Funding:** Bootstrapped, planning $200k angel raise

## Target users
- **Primary audience:** Hospital compliance officers
- **What their day looks like:** Reviewing audit reports, managing vendor certifications. Experts in healthcare regulation. Not tech people.
```

The more specific your context, the better the advice.

### Step 3: Customize the compliance checklist (optional)

The default `compliance-review/checklist.md` is an example for loan recommendation products in higher education. Replace it with your own industry-specific items, or skip this step if you don't need compliance reviews.

### Step 4: Add regulatory references (optional)

Drop your industry's regulatory documents into `compliance-review/references/`. The compliance review skill reads these as its source of truth. See the README in that folder for guidance.

### Step 5: Restart Claude Code

The skills are discoverable after restart. Type `/cfo` or `/coach` to verify.

## What not to commit

The `.gitignore` excludes your filled-in `company-context.md` and any regulatory documents in `compliance-review/references/`. These contain proprietary information. Only the templates and README files are safe to commit.

## Customization

**Adding an advisor:** Create a new folder in `.claude/skills/` with a `SKILL.md`. Follow the pattern of any existing advisor. Add it to `references/advisor-roster.md`.

**Removing an advisor:** Delete the folder and remove it from `advisor-roster.md`.

**Changing an advisor's behavior:** Edit the `SKILL.md` directly. The structural constraint and "before you speak" sections are where most behavioral tuning happens.

**Making advisors auto-invoke:** Remove `disable-model-invocation: true` from the frontmatter. Claude will then activate the advisor automatically when it detects a relevant topic. We recommend against this — overlapping triggers cause more confusion than convenience.

## How it works

Each advisor is a [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code) — a markdown file with YAML frontmatter that Claude reads when you invoke the command. The skill contains the persona's expertise, communication style, structural constraints, and a link to your company context.

Key technical details:

- `disable-model-invocation: true` — advisors only activate when you summon them
- `context: fork` (compliance review only) — runs in an isolated subagent
- `allowed-tools` (compliance review only) — restricted to Read, Write, Glob, Grep
- `$ARGUMENTS` — whatever you type after the command gets passed to the advisor

## Design principles

**Structural constraints over self-reflection.** Telling an LLM "don't be sycophantic" has limited effect. Requiring it to cite a specific regulation, show its math, or state why the advice might be wrong forces rigor structurally.

**Constraints over descriptions.** The company context file works best with hard constraints ("pre-revenue, 2-person team, users are domain experts") rather than descriptive prose. Constraints hold up better over long conversations.

**Domain boundaries.** The CFO doesn't opine on strategy; the angel doesn't build spreadsheets. Each advisor stays in their lane and refers you to the right colleague when a question crosses domains.

**Honest by design.** Every advisor has an anti-sycophancy check tailored to their role. The coach's is the strongest: "Am I being supportive because it's warranted, or because I'm avoiding a hard truth?"

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- A Claude Code project directory (the skills are project-scoped)

## License

MIT
