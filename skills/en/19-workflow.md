# Planning, Workflow & Project Management
> 58 skills | Plan tasks, run research, analyze business opportunities, and manage delivery workflows

## Planning & Execution
| Skill | What it does | Level |
|-------|-------------|-------|
| `brainstorming` | Run creative brainstorming sessions | [CORE] |
| `plan-writing` | Write structured task plans | [CORE] |
| `writing-plans` | Create multi-step execution plans | [CORE] |
| `executing-plans` | Execute tasks from written plans | [CORE] |
| `concise-planning` | Generate quick, focused plans | [SPEC] |
| `planning-with-files` | Create plans backed by project files | [SPEC] |
| `subagent-driven-development` | Execute tasks using sub-agents | [SPEC] |
| `blueprint` | Turn a one-line idea into step-by-step instructions | [SPEC] |
| `ask-questions-if-underspecified` | Ask clarifying questions when requirements are vague | [SPEC] |
| `progressive-estimation` | Estimate effort with AI assistance | [SPEC] |

## Conductor System
| Skill | What it does | Level |
|-------|-------------|-------|
| `conductor-setup` | Initialize the Conductor project system | [SPEC] |
| `conductor-new-track` | Create a new work track | [SPEC] |
| `conductor-implement` | Execute tasks within a track | [SPEC] |
| `conductor-status` | Check project status across tracks | [SPEC] |
| `conductor-manage` | Manage track lifecycle and transitions | [SPEC] |
| `conductor-revert` | Undo changes with Git-aware rollback | [SPEC] |
| `conductor-validator` | Validate track artifacts and outputs | [SPEC] |
| `track-management` | Manage and organize work tracks | [SPEC] |
| `workflow-patterns` | Apply Conductor workflow patterns | [SPEC] |

## Delivery Workflows
| Skill | What it does | Level |
|-------|-------------|-------|
| `acceptance-orchestrator` | Orchestrate end-to-end task acceptance | [SPEC] |
| `closed-loop-delivery` | Deliver work against a specification | [SPEC] |
| `spec-to-code-compliance` | Verify code matches the specification | [SPEC] |
| `verification-before-completion` | Run verification checks before marking done | [SPEC] |
| `finishing-a-development-branch` | Complete and finalize a development branch | [SPEC] |
| `project-development` | Manage full project development lifecycle | [SPEC] |

## Research & Search
| Skill | What it does | Level |
|-------|-------------|-------|
| `deep-research` | Conduct multi-step deep research | [CORE] |
| `search-specialist` | Perform advanced web searches | [CORE] |
| `research-engineer` | Run academic and engineering research | [SPEC] |
| `claude-scientific-skills` | Analyze scientific data and papers | [SPEC] |
| `infinite-gratitude` | Run parallel research across sources | [SPEC] |
| `last30days` | Research events from the last 30 days | [SPEC] |
| `daily-news-report` | Scrape and compile daily news reports | [SPEC] |
| `exa-search` | Search the web with semantic understanding | [SPEC] |
| `tavily-web` | Search and extract content from the web | [SPEC] |
| `maxia` | Access the MAXIA AI marketplace | [SPEC] |

## Business Analysis
| Skill | What it does | Level |
|-------|-------------|-------|
| `business-analyst` | Perform AI-powered business analysis | [SPEC] |
| `startup-analyst` | Analyze startup market positioning | [SPEC] |
| `startup-financial-modeling` | Build startup financial models | [SPEC] |
| `startup-metrics-framework` | Define and track startup metrics | [SPEC] |
| `startup-business-analyst-business-case` | Write business case documents | [SPEC] |
| `startup-business-analyst-financial-projections` | Create financial projections | [SPEC] |
| `startup-business-analyst-market-opportunity` | Assess market opportunity size | [SPEC] |
| `competitive-landscape` | Map the competitive landscape | [SPEC] |
| `market-sizing-analysis` | Estimate total and serviceable market size | [SPEC] |
| `product-manager-toolkit` | Use product management tools and frameworks | [SPEC] |
| `product-manager` | Act as a senior product manager agent | [SPEC] |
| `team-composition-analysis` | Analyze and optimize team composition | [SPEC] |

## Finance & Trading
| Skill | What it does | Level |
|-------|-------------|-------|
| `quant-analyst` | Build quantitative financial models | [SPEC] |
| `risk-manager` | Assess and manage portfolio risk | [SPEC] |
| `risk-metrics-calculation` | Calculate VaR, CVaR, and Sharpe ratios | [SPEC] |
| `backtesting-frameworks` | Backtest trading strategies | [SPEC] |
| `alpha-vantage` | Fetch financial market data from Alpha Vantage | [SPEC] |

## Behavioral & Modes
| Skill | What it does | Level |
|-------|-------------|-------|
| `behavioral-modes` | Switch between AI operational modes | [SPEC] |
| `bdi-mental-states` | Model belief-desire-intention mental states | [SPEC] |
| `kaizen` | Apply continuous improvement practices | [SPEC] |

---

## Enriched Skills

### `brainstorming`
**What you need:** Helps you come up with ideas and explore different approaches before you start building anything. Think of it as a creative thinking partner that helps you figure out what to build and how.
**Level:** Beginner
**Tags:** #ideation #planning #creativity #problem-solving
**When to use:**
- You have a rough idea but need to explore different directions before committing
- You are stuck on a problem and want fresh perspectives or alternative solutions
- You want to compare multiple approaches side by side before picking one
**Combine with:** `brainstorming` > `writing-plans` > `executing-plans` > `react-nextjs-development`
**Example prompt:** > /brainstorming I want to build a habit tracker app — help me explore different feature ideas and decide what to build first
**Don't use when:** You already know exactly what you want to build and just need to start coding — skip straight to `writing-plans` or `executing-plans`

### `writing-plans`
**What you need:** Turns your idea into a clear, step-by-step plan before you write any code. It breaks big tasks into smaller pieces so you always know what to do next.
**Level:** Beginner
**Tags:** #planning #structure #project-management #organization
**When to use:**
- You know what you want to build but need a roadmap to get there
- Your project has multiple parts and you want to tackle them in the right order
- You want to hand off a plan to the AI so it can build things step by step
**Combine with:** `brainstorming` > `writing-plans` > `executing-plans` > `backend-architect`
**Example prompt:** > /writing-plans Create a plan for building a blog with user accounts, markdown posts, and a comment system using Next.js and Supabase
**Don't use when:** You have a tiny one-step task that does not need a plan — just ask the AI to do it directly

### `executing-plans`
**What you need:** Takes a plan you have already written and works through it step by step, building each piece and checking it off as it goes. It keeps track of progress so nothing gets missed.
**Level:** Beginner
**Tags:** #execution #implementation #step-by-step #automation
**When to use:**
- You have a written plan and want the AI to start building it piece by piece
- You want to resume work on a plan that was partially completed
- You need to follow a specific order of tasks and track what is done
**Combine with:** `writing-plans` > `executing-plans` > `verification-before-completion`
**Example prompt:** > /executing-plans Follow the plan in PLAN.md and start implementing from step 3 — steps 1 and 2 are already done
**Don't use when:** You do not have a plan yet — use `writing-plans` first to create one
