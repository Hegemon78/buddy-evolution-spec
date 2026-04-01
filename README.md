# Buddy Evolution Spec — v3

> Community-driven specification for the Claude Code Buddy companion system.  
> Born from [Issue #41867](https://github.com/anthropics/claude-code/issues/41867) and [Issue #41684](https://github.com/anthropics/claude-code/issues/41684) in anthropics/claude-code.

## What is this?

On April 1, 2026, Anthropic released `/buddy` — a Tamagotchi-style ASCII companion that lives in your Claude Code terminal. 18 species, 5 rarity tiers, personality stats, animations.

The community loved it. But we want more.

This repo is a **collaborative specification** for how the buddy system could evolve. Not a fork, not a hack — a structured proposal for Anthropic (or the community) to build from.

---

## Core Principles

1. **Buddy is optional.** `/buddy off` and it's gone. Never forced.
2. **Claude always performs at 100%.** Buddy stats are flavor, not function.
3. **Everything earnable for free.** No paywalls on features.
4. **Subscription tier = progression speed.** Same model as token limits.
5. **Community-shaped.** This spec evolves through PRs and discussion.
6. **Claude Code is universal.** People use it for coding, research, project management, writing, automation, and personal tasks. Buddy progression reflects ALL activity, not just code.

---

## Specification

### 1. Species & Rarity (Current System)

| Tier | Drop Rate | Species Examples |
|------|-----------|-----------------|
| Common | 45% | Duck, Goose, Blob, Snail |
| Uncommon | 25% | Cat, Rabbit, Owl, Penguin |
| Rare | 15% | Turtle, Octopus, Axolotl |
| Epic | 10% | Ghost, Robot, Dragon |
| Legendary | 5% | Capybara, Mushroom, Chonk |

- Species determined by account hash at creation
- 18 species total, each with unique ASCII art and personality

### 2. Progression System (Achievement-Based)

**Philosophy:** Reward skill and consistency, not idle time. Progression is relative to YOUR history — a beginner and a senior both grow at their own pace.

**Important:** Claude Code is not just a coding tool. Achievements and XP span all types of work — code, research, writing, project management, automation.

#### XP Sources

| Source | Description | XP Weight |
|--------|-------------|-----------|
| Session streak | Consecutive days of usage | High |
| Action diversity | Mix of code, research, writing, automation | Medium |
| Personal records | Beat your own bests | High |
| Project milestones | Commits, closed issues, PRs, completed tasks | Medium |
| Consistency | Regular usage patterns | Low (passive) |

#### Achievement Categories

Achievements are the primary progression driver. They span **four domains** to reflect the full range of Claude Code usage:

| Category | Example Achievements | Description |
|----------|---------------------|-------------|
| **Coding** | First Green Suite, Refactor Survivor, Debug Speedrun, Polyglot | Traditional development milestones |
| **Research** | Deep Dive (3h+ research session), Source Hunter (10+ web queries in session), Knowledge Mapper (structured document from raw data) | Investigation, analysis, learning |
| **Project Management** | Multi-Tasker (3+ projects in one day), Architect (created plan before implementation), Sprint Master (completed all planned tasks) | Planning, coordination, delivery |
| **Creative** | Wordsmith (1000+ word document), Bridge Builder (connected 2+ platforms in one task), Automator (set up a recurring workflow) | Writing, automation, integration |

> **Open for discussion:** These categories are initial proposals. The community is invited to suggest additional achievements via issues and PRs. See [Issue #1](https://github.com/Hegemon78/buddy-evolution-spec/issues/1) for FrankFMY's detailed achievement catalog (34 coding-focused achievements) as a starting point for expansion.

#### Levels

| Level | XP Required | Unlock |
|-------|-------------|--------|
| 1 | 0 | Base buddy |
| 5 | ~2 weeks active | First evolution choice |
| 10 | ~2 months active | Second evolution choice |
| 15 | ~4 months active | Shiny variant available |
| 20 | ~8 months active | Legendary cosmetics |

*XP rates scale with subscription tier: Pro = 1x, Team = 2x, Max = 5x*

### 3. Branching Evolution

At evolution milestones, **you choose** which path your buddy takes. Inspired by Digimon/Patapon progression systems.

```
         [Base Form]
            |
     Level 5 Choice
      /           \
  [Path A]     [Path B]
     |             |
 Level 10      Level 10
  Choice        Choice
  /    \        /    \
[A1]  [A2]   [B1]  [B2]
```

- **4 possible final forms** per species
- Choice is **permanent** — gives every buddy a unique identity
- Paths affect appearance and personality flavor (not Claude performance)
- Each evolution path reflects a **working philosophy** — one path rewards test-driven development, another rapid prototyping, another deep research. Your buddy becomes a mirror of *how* you work, not just *how much*.

**Example (Turtle):**
- Path A: "Scholar" — calm, methodical, quotes references
- Path B: "Trickster" — chaotic, jokes, unexpected reactions
  - A1: "Ancient Sage" — speaks rarely, always profound
  - A2: "Librarian" — catalogues everything, loves organization
  - B1: "Jester" — maximum chaos, puns, roasts
  - B2: "Phantom" — mysterious, cryptic, appears/disappears

#### Open Discussion: Auto-Evolution Mode

> **Proposed by [@bgreal5](https://github.com/bgreal5):** Instead of manual choice, evolution path could be determined automatically based on your stats and behavior patterns. If you primarily debug — Scholar path. High chaos in your workflow — Trickster path. Your usage shapes your buddy's evolution organically.
>
> This is an interesting alternative to manual selection. The exact mechanism needs further design. Community input welcome — open an issue to discuss.

### 4. Personality System

12 base personality presets assigned at creation. Personality affects:

- Speech style and vocabulary
- Reaction timing and frequency
- Animation preferences
- Comment tone (supportive <-> snarky)

**Personality deepens over time** — more history = more nuanced responses. A fresh buddy speaks in generic terms; a buddy with 100+ sessions references your actual patterns.

Future consideration: optional customization to change preset after creation.

### 5. Buddy Journal

Auto-generated `.buddy/journal.md` after each session:

```markdown
## 2026-04-01 — Session #847
**Project:** buddy-evolution-spec
**Duration:** 2h 14m
**Activity:** Research + writing + code review
**Files touched:** 23 across 2 packages
**Web queries:** 8 (competitor analysis)
**Documents created:** 1 (market research report)
**Tests:** 🔴->🟢 x3 | New files: 2
**Streak:** Day 12 — longest this month
**Milestone:** "Centurion" — 100th session in this project
```

#### Scope

Buddy is **global** — it persists across all your projects and sees your full history. But it's also **project-aware** — each project gets its own journal section, and buddy references project-specific context.

Think of it as: one buddy, many projects. Like a colleague who works with you on everything.

#### Value

- Personal activity diary (useful retrospective data across all work types)
- Progression fuel (achievements detected from journal data)
- Context for familiarity system (see below)
- Cross-project awareness — buddy can reference patterns across your entire workflow

### 6. Contextual Familiarity

Buddy tracks interaction frequency per project and per file in its soul file.

| Familiarity Level | Trigger | Buddy Behavior |
|-------------------|---------|----------------|
| New | First time in file/project | Curiosity animations, "what's this?" |
| Familiar | 10+ interactions | Comfortable, references past work |
| Expert | 50+ interactions | "Home turf" reactions, deep familiarity |
| Nostalgic | Return after 30+ days away | "Been a while!" — moment of recognition |

The **Nostalgic** state triggers specifically when you *return* to a file or project you haven't touched in weeks. That brief moment of recognition feels genuinely alive.

**Not suggestions** — purely personality expression. Buddy doesn't tell you what to do; it reacts to where you are.

### 7. Cosmetics

| Type | How to Get |
|------|-----------|
| Hats | Achievements OR purchase |
| Colors | Level milestones |
| Shiny variant | Level 15+ |
| Animations | Achievements |
| Titles | Milestones ("Bug Slayer", "Streak Master", "Deep Diver") |

All cosmetics are earnable through gameplay. Purchase is a shortcut, not a gate.

### 8. Stats

5 stats remain from current system:

| Stat | Affects | Does NOT affect |
|------|---------|-----------------|
| DEBUGGING | Buddy's commentary on bugs | Claude's actual bug detection |
| PATIENCE | How long buddy waits before reacting | Claude's response time |
| CHAOS | Randomness of buddy's behavior | Claude's output quality |
| WISDOM | Depth of buddy's observations | Claude's reasoning |
| SNARK | Sass level of buddy's comments | Claude's tone |

**Stats are a personality mirror.** They reflect your working style and grow through usage. They never gate functionality.

---

## Monetization Model

| Aspect | Free (any sub) | Pro ($20) | Team ($100) | Max ($200) |
|--------|---------------|-----------|-------------|------------|
| Buddy access | Yes | Yes | Yes | Yes |
| Progression | 1x speed | 1x speed | 2x speed | 5x speed |
| Cosmetics (earnable) | Yes | Yes | Yes | Yes |
| Cosmetics (purchasable) | — | Yes | Yes | Yes |
| Evolution paths | Yes | Yes | Yes | Yes |
| Journal | Yes | Yes | Yes | Yes |

**No loot boxes. No microtransaction store. No pay-to-win.**

Progression speed tied to subscription tier — the same model that already works for token limits. Higher tier = more value from every feature.

---

## Implementation Paths

This specification can be realized through two complementary approaches:

### Path A: Community Plugin (Primary Focus)

Build as an independent Claude Code plugin/extension. Community prototypes already exist, demonstrating feasibility.

**Advantages:** Ship fast, iterate with community, no dependency on Anthropic's roadmap.

### Path B: Anthropic-Native Integration

Propose to Anthropic for native Claude Code integration. The existing `/buddy` system already provides the foundation — species, stats, ASCII art, animations.

**Advantages:** Full access to session data, seamless UX, official support.

**Both paths are not mutually exclusive.** A community plugin can serve as a proof of concept that demonstrates demand and validates mechanics, potentially leading to official adoption.

---

## Contributing

This is a community specification. To contribute:

1. **Open an issue** — propose a new mechanic or discuss existing ones
2. **Submit a PR** — improve the spec directly
3. **React on GitHub** — thumbs up on [Issue #41867](https://github.com/anthropics/claude-code/issues/41867) to signal support to Anthropic
4. **Build** — reference implementations and plugins welcome

---

## Credits

| Role | Contributor |
|------|-------------|
| Project lead, author | [@Hegemon78](https://github.com/Hegemon78) — original proposal, v1/v2/v3 spec, monetization model, universal activity framework |

## Acknowledgments

Thanks to the community members whose feedback shaped this specification:

- [@FrankFMY](https://github.com/FrankFMY) — achievement-milestone mechanics, buddy journal concept, contextual familiarity idea
- [@bgreal5](https://github.com/bgreal5) — critical feedback on stats model, auto-evolution suggestion
- [@tarunt815](https://github.com/tarunt815) — pokemon-style evolution idea
- [@elmdecoste](https://github.com/elmdecoste) — digivolution branching concept
- r/ClaudeAI community — discussion and feedback

---

## Related

- [Issue #41867](https://github.com/anthropics/claude-code/issues/41867) — Original feature request (anthropics/claude-code)
- [Issue #41684](https://github.com/anthropics/claude-code/issues/41684) — RPG evolution proposal (anthropics/claude-code)
- [r/ClaudeAI discussion](https://www.reddit.com/r/ClaudeAI/comments/1s9egh1/) — Reddit thread

---

## Changelog

- **v3 (2026-04-01)** — Universal activity model (not coding-only), 4 achievement categories, auto-evolution as discussion topic, evolution paths as working philosophy, implementation roadmap
- **v2 (2026-04-01)** — Community rewrite: removed functional stats, added achievements/journal/familiarity/branching evolution
- **v1 (2026-04-01)** — Initial proposal

---

*This specification is a community proposal, not an official Anthropic document. Project lead: [@Hegemon78](https://github.com/Hegemon78)*
