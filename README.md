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

> See [§9 Achievement Catalog](#9-achievement-catalog) for the full list of 34 defined achievements and their triggers.

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

### 9. Achievement Catalog

34 achievements across 6 categories. Every trigger maps to a metric already tracked by the [buddy-evolution PoC](https://github.com/RaphaelRUzan/buddy-evolution) session tracker — no guesswork, no new telemetry required.

**Design principles:**
- Every trigger is technically detectable from session data
- No achievement rewards bad behavior (no "skip tests", no "rush code")
- XP values are bonuses on top of session XP, not the sole progression driver
- Hidden achievements (marked 🔒) are only revealed after earning
- Repeatable achievements (marked ♻️) give ongoing micro-rewards

#### Coding

| Achievement | Trigger | XP | Rarity |
|---|---|---|---|
| First Steps | Complete first session | 100 | Common |
| Getting Comfortable | Complete 10 sessions | 200 | Common |
| Centurion | Complete 100 sessions | 1,000 | Uncommon |
| Veteran | Complete 500 sessions | 3,000 | Rare |
| Living Legend | Complete 1,000 sessions | 10,000 | Legendary |
| The Architect | 20+ file edits in one session | 500 | Rare |
| Tool Master | 100+ tool calls in one session | 400 | Uncommon |
| Wordsmith | 100K+ output tokens in one session | 600 | Rare |

#### Testing

| Achievement | Trigger | XP | Rarity |
|---|---|---|---|
| First Test | Run tests in a session (`testRuns ≥ 1`) | 100 | Common |
| Test Enthusiast | 10+ test runs in one session | 300 | Uncommon |
| Test Marathon | 50+ test runs in one session | 1,000 | Epic |
| Test-Driven | Run tests in 10 consecutive sessions | 800 | Rare |

#### Debugging

| Achievement | Trigger | XP | Rarity |
|---|---|---|---|
| Persistence | 5+ rejected tool calls, still complete work (`fileEdits > 0`) | 300 | Uncommon |
| Against All Odds | 20+ rejected tool calls, still complete work | 800 | Epic |
| Unbreakable | 0 rejected calls in a session with 50+ total calls | 500 | Rare |
| Context Survivor | Productive work after context reset (`resets ≥ 1, edits ≥ 5`) | 400 | Uncommon |

#### Consistency

| Achievement | Trigger | XP | Rarity |
|---|---|---|---|
| Streak: Week | 7 consecutive days | 500 | Common |
| Streak: Month | 30 consecutive days | 2,000 | Rare |
| Streak: Quarter | 90 consecutive days | 5,000 | Epic |
| Streak: Year | 365 consecutive days | 20,000 | Legendary |
| Early Bird ♻️ | Session started before 7 AM local | 100 | Common |
| Night Owl ♻️ | Session active past midnight | 100 | Common |
| Marathon | Session longer than 4 hours | 600 | Rare |

#### Exploration

| Achievement | Trigger | XP | Rarity |
|---|---|---|---|
| Tourist | Work in 5 different projects | 400 | Uncommon |
| Globe Trotter | Work in 20 different projects | 1,500 | Epic |
| Deep Roots | Reach Expert familiarity (50+ touches) on 5 files | 800 | Rare |
| Homecoming | Return to a file after 30+ days (triggers Nostalgic) | 200 | Common |
| Old Friend | Return to an Expert file after 60+ days away | 500 | Rare |

#### Meta

| Achievement | Trigger | XP | Rarity | |
|---|---|---|---|---|
| Pet Day | `/buddy pet` 10 times in one session | 50 | Common | |
| First Evolution | Make first evolution choice (level 5) | 1,000 | Uncommon | |
| Final Form | Make second evolution choice (level 10) | 3,000 | Rare | |
| The Collector | Earn 20 different achievements | 2,000 | Epic | |
| Happy Birthday | Use buddy on 1-year hatch anniversary | 5,000 | Legendary | 🔒 |
| Completionist | Earn all non-hidden achievements | 10,000 | Legendary | 🔒 |

#### Distribution

| Rarity | XP Range | Count |
|---|---|---|
| Common | 50–500 | 8 (23%) |
| Uncommon | 300–1,000 | 7 (21%) |
| Rare | 500–3,000 | 10 (29%) |
| Epic | 800–5,000 | 5 (15%) |
| Legendary | 5,000–20,000 | 4 (12%) |

Rare-heavy distribution is intentional — the mid-game should always have something to work toward. Exact numbers are a starting point; final balancing depends on the XP-to-level curve.

### 10. Interaction Commands

| Command | Description | Status |
|---|---|---|
| `/buddy` | Toggle buddy on/off | Existing |
| `/buddy pet` | Pet your buddy | Existing |
| `/buddy stats` | Show level, XP, stats, streak | New |
| `/buddy achievements` | List earned, in-progress, and hidden | New |
| `/buddy journal` | Show recent journal entries | New |
| `/buddy evolve` | Make evolution choice (when eligible) | New |
| `/buddy rename <name>` | Rename your buddy | New |

#### Example outputs

**`/buddy stats`**

```
🐉 Zephyr — Epic Dragon (Scholar)
Level 7 ████████░░ 45,200 / 60,000 XP
Streak: 12 days (🔥 1.2x)

DEBUGGING ██████████████████░░  79 (+12)
PATIENCE  █████████░░░░░░░░░░░  53  (+8)
CHAOS     ████░░░░░░░░░░░░░░░░  25  (+2)
WISDOM    ████████████████████  94 (+16)
SNARK     ██████████░░░░░░░░░░  55  (+3)
```

*Base stat shown first, growth bonus in parentheses. Bar length reflects effective stat (base + growth).*

**`/buddy achievements`**

```
🏆 Achievements — 12/32 earned

Recent:
  ✅ Centurion — Complete 100 sessions (+1,000 XP)
  ✅ Streak: Month — 30 consecutive days (+2,000 XP)

In Progress:
  ⬜ Veteran ········· 147/500 sessions
  ⬜ Deep Roots ······ 3/5 Expert files
  ⬜ Streak: Quarter · 34/90 days

🔒 2 hidden achievements undiscovered
```

*Non-hidden total is 32. Progress bars show partial completion for trackable achievements.*

**`/buddy evolve`**

```
🐉 Zephyr is ready to evolve!

Choose a path — this is permanent:

  [A] Scholar — calm, methodical, quotes references
  [B] Trickster — chaotic, jokes, unexpected reactions

Type A or B to choose.
```

*Only appears when level threshold is reached and choice hasn't been made. Shows species-specific path descriptions.*

### 11. Technical Schema

Soul file v2 — stored at `.buddy/soul.json`. Backwards-compatible extension of the current soul file.

```jsonc
{
  "version": 2,

  // === Immutable identity (set at creation) ===
  "identity": {
    "species": "dragon",
    "name": "Zephyr",
    "rarity": "epic",
    "personality": "methodical",
    "hatchedAt": "2026-04-01T10:00:00Z",
    "accountHash": "a1b2c3"
  },

  // === Progression state ===
  "progression": {
    "level": 7,
    "totalXP": 45200,
    "tier": "juvenile",              // hatchling | juvenile | adult | elder | ascended
    "evolutionPath": ["scholar"],    // choices made so far (max 2)
    "evolvedAt": {                   // timestamp of each tier transition
      "juvenile": "2026-04-15T12:00:00Z",
      "adult": null,
      "elder": null,
      "ascended": null
    }
  },

  // === Stats: base (from hash, immutable) + growth (from usage) ===
  "stats": {
    "base": { "debugging": 67, "patience": 45, "chaos": 23, "wisdom": 78, "snark": 52 },
    "growth": { "debugging": 12.4, "patience": 8.1, "chaos": 2.3, "wisdom": 15.6, "snark": 3.2 }
  },

  // === Streak tracking ===
  "streak": {
    "currentDays": 12,
    "longestDays": 34,
    "lastSessionDate": "2026-04-01"  // ISO date, not datetime
  },

  // === Achievement state ===
  "achievements": {
    "earned": [
      { "id": "first_steps", "at": "2026-04-01T10:30:00Z" },
      { "id": "centurion", "at": "2026-07-10T09:15:00Z" }
    ],
    "progress": {                    // only unearned achievements with partial progress
      "veteran": { "current": 147, "target": 500 },
      "streak_quarter": { "current": 34, "target": 90 }
    }
  },

  // === Per-project file familiarity ===
  "familiarity": {
    "/home/user/myproject": {
      "sessions": 47,
      "files": {
        "src/auth.ts": { "touches": 83, "last": "2026-04-01" },
        "src/api.ts": { "touches": 12, "last": "2026-03-01" }
      }
    }
  },

  // === Cosmetic state ===
  "cosmetics": {
    "hat": null,
    "color": "default",
    "shiny": false,
    "title": "Centurion"
  },

  // === Cumulative lifetime metrics ===
  "lifetime": {
    "sessions": 147,
    "durationMinutes": 17640,
    "outputTokens": 3200000,
    "inputTokens": 7500000,
    "toolCalls": 9800,
    "rejectedToolCalls": 210,
    "fileEdits": 5400,
    "testRuns": 1300,
    "forceSnips": 28,
    "contextResets": 7
  }
}
```

#### Design decisions

| Decision | Rationale |
|---|---|
| `stats.base` is immutable | Determined by account hash at creation — your starting personality never changes |
| `stats.growth` uses diminishing returns | Formula: `rawGrowth × (100 / (100 + currentGrowth))` — fast early growth, asymptotic cap |
| `achievements.progress` is transient | Once earned, achievement moves to `earned` array and is deleted from `progress` |
| `familiarity` is per-project | Buddy is global but tracks each project independently — supports both cross-project identity and project-specific reactions |
| `lifetime` mirrors session metrics | Accumulates totals from every session — needed for achievement detection without replaying history |
| `evolvedAt` records timestamps | Each tier transition is logged once and never overwritten — useful for journal milestones |

#### Migration (v1 → v2)

On first v2 session, the existing soul file is extended non-destructively:

1. Preserve all current fields (`identity`, `stats.base`, `hatchedAt`)
2. Add `progression` at level 1, 0 XP, tier `"hatchling"`
3. Add empty `achievements`, `familiarity`, `cosmetics`
4. Add `lifetime` with all counters at 0 (no retroactive credit)
5. Add `stats.growth` initialized to 0 for all stats
6. Set `version: 2`

Missing v2 fields return safe defaults on read — a v1 soul file still works, it just starts fresh on progression.

#### Session-end pipeline

Achievement detection runs once per session via `processSessionEnd(metrics, soul)`:

```
1. Update soul.lifetime     ← accumulate session metrics
2. Update soul.streak       ← increment or reset based on date gap
3. Update soul.stats.growth ← apply diminishing returns formula
4. Update soul.familiarity  ← bump touch counts, detect Homecoming/Old Friend
5. Check achievements       ← evaluate triggers against updated state
6. Award XP                 ← add achievement XP to soul.progression.totalXP
7. Check level/tier         ← promote if threshold crossed
8. Write soul file          ← persist updated state
```

Order matters — lifetime stats and familiarity must update before achievement triggers are evaluated, and achievement XP must be awarded before checking level thresholds.

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
- [buddy-evolution PoC](https://github.com/RaphaelRUzan/buddy-evolution) — Working proof of concept with 104 tests (XP engine, stat growth, sprite overlays)

---

*This specification is a community proposal, not an official Anthropic document.*
