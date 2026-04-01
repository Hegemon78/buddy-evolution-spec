# Buddy Evolution Spec

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

#### XP Sources

| Source | Description | XP Weight |
|--------|-------------|-----------|
| Session streak | Consecutive days of usage | High |
| Action diversity | Mix of code, tests, deploy, docs | Medium |
| Personal records | Beat your own bests | High |
| Project milestones | Commits, closed issues, PRs | Medium |
| Consistency | Regular usage patterns | Low (passive) |

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

**Example (Turtle):**
- Path A: "Scholar" → calm, methodical, quotes references
- Path B: "Trickster" → chaotic, jokes, unexpected reactions
  - A1: "Ancient Sage" — speaks rarely, always profound
  - A2: "Librarian" — catalogues everything, loves organization
  - B1: "Jester" — maximum chaos, puns, roasts
  - B2: "Phantom" — mysterious, cryptic, appears/disappears

### 4. Personality System

12 base personality patterns assigned at creation (random). Personality affects:

- Speech style and vocabulary
- Reaction timing and frequency
- Animation preferences
- Comment tone (supportive ↔ snarky)

**Personality deepens over time** — more history = more nuanced responses. A fresh buddy speaks in generic terms; a buddy with 100+ sessions references your actual patterns.

### 5. Buddy Journal

Auto-generated `.buddy/journal.md` after each session:

```markdown
## 2026-04-01 — Session #847
**Project:** buddy-evolution-spec
**Duration:** 2h 14m
**Files touched:** 23 across 2 packages
**Tests:** 🔴→🟢 ×3 | New files: 2
**Streak:** Day 12 — longest this month
**Milestone:** 🏆 "Centurion" — 100th session in this project
```

#### Scope

Buddy is **global** — it persists across all your projects and sees your full history. But it's also **project-aware** — each project gets its own journal section, and buddy references project-specific context.

Think of it as: one buddy, many projects. Like a colleague who works with you on everything.

#### Value

- Personal coding diary (useful retrospective data)
- Progression fuel (achievements detected from journal data)
- Context for familiarity system (see below)

### 6. Contextual Familiarity

Buddy tracks file-touch frequency per project in its soul file.

| Familiarity Level | Trigger | Buddy Behavior |
|-------------------|---------|----------------|
| New | First time in file | Curiosity animations, "what's this?" |
| Familiar | 10+ touches | Comfortable, references past work |
| Expert | 50+ touches | "Home turf" reactions, deep familiarity |
| Nostalgic | Haven't visited in 30+ days | "Been a while!" reactions |

**Not suggestions** — purely personality expression. Buddy doesn't tell you what to do; it reacts to where you are.

### 7. Cosmetics

| Type | How to Get |
|------|-----------|
| Hats | Achievements OR purchase |
| Colors | Level milestones |
| Shiny variant | Level 15+ |
| Animations | Achievements |
| Titles | Milestones ("Bug Slayer", "Streak Master") |

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

**Stats are a personality mirror.** They reflect your coding style and grow through usage. They never gate functionality.

---

## Monetization Model

| Aspect | Free (any sub) | Pro ($20) | Team ($100) | Max ($200) |
|--------|---------------|-----------|-------------|------------|
| Buddy access | ✅ | ✅ | ✅ | ✅ |
| Progression | 1x speed | 1x speed | 2x speed | 5x speed |
| Cosmetics (earnable) | ✅ | ✅ | ✅ | ✅ |
| Cosmetics (purchasable) | — | ✅ | ✅ | ✅ |
| Evolution paths | ✅ | ✅ | ✅ | ✅ |
| Journal | ✅ | ✅ | ✅ | ✅ |

**No loot boxes. No microtransaction store. No pay-to-win.**

Progression speed tied to subscription tier — the same model that already works for token limits. Higher tier = more value from every feature.

---

## Contributing

This is a community specification. To contribute:

1. **Open an issue** — propose a new mechanic or discuss existing ones
2. **Submit a PR** — improve the spec directly
3. **React on GitHub** — 👍 on [Issue #41867](https://github.com/anthropics/claude-code/issues/41867) to signal support to Anthropic

---

## Credits

| Contributor | Contribution |
|-------------|-------------|
| [@Hegemon78](https://github.com/Hegemon78) | Original proposal, v2 rewrite, monetization model |
| [@FrankFMY](https://github.com/FrankFMY) | Achievement-milestone evolution, buddy journal, contextual familiarity, stat synergies |
| [@tarunt815](https://github.com/tarunt815) | Pokemon-style evolution concept |
| [@elmdecoste](https://github.com/elmdecoste) | Digivolution branching paths |
| [@bgreal5](https://github.com/bgreal5) | Critical feedback: stats as flavor, not function |
| r/ClaudeAI community | Extensive discussion and reality-checking |

---

## Related

- [Issue #41867](https://github.com/anthropics/claude-code/issues/41867) — Original feature request (anthropics/claude-code)
- [Issue #41684](https://github.com/anthropics/claude-code/issues/41684) — RPG evolution proposal (anthropics/claude-code)
- [r/ClaudeAI discussion](https://www.reddit.com/r/ClaudeAI/comments/1s9egh1/) — Reddit thread

---

*This specification is a community proposal, not an official Anthropic document.*
