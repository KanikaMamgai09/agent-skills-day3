# Agent Skills — Kaggle × Google AI Agents Workshop (Day 3)

Hands-on labs exploring **Agent Skills** — a lightweight way to give AI agents on-demand specialist knowledge without overloading their context window.

Built as part of the [Kaggle × Google 5-Day AI Agents Workshop](https://www.kaggle.com/learn-guide/5-day-genai).

---

## What are Agent Skills?

An Agent Skill is a folder with a `SKILL.md` file that tells an AI agent **when** and **how** to do something specific. Instead of loading all instructions upfront, the agent loads a skill only when it's relevant — this is called **progressive disclosure**.

```
my-skill/
├── SKILL.md          ← trigger description + step-by-step instructions
├── assets/           ← templates and output formats
├── references/       ← lookup guides the agent reads on demand
└── scripts/          ← scripts the agent can run
```

---

## Labs

### Lab 1 — 4 Skill Patterns in Antigravity CLI

Explored the four levels of skill complexity using [rominirani/antigravity-skills](https://github.com/rominirani/antigravity-skills):

| Skill | Pattern | What it did |
|---|---|---|
| `git-commit-formatter` | Basic Router | Auto-formatted every commit as `feat(scope): description` |
| `license-header-adder` | Asset Utilization | Read a template file and prepended Apache 2.0 header to new source files |
| `json-to-pydantic` | Few-Shot Learning | Converted `product.json` into typed Pydantic classes using examples |
| `database-schema-validator` | Procedural Logic | Ran `validate_schema.py`, caught 3 SQL violations, suggested fixes |

Also scaffolded a **weather-assistant agent** using [Google Agents CLI](https://github.com/google/agents-cli) and ran it in the ADK Playground (local web UI showing the agent's tool graph).

### Lab 2 — Custom Skill: `bigquery-tweet-composer`

Built a custom skill from scratch that turns BigQuery release notes into tweet threads.

**How it works:**
1. Agent reads `SKILL.md` → loads a 7-step workflow
2. Agent reads `assets/tweet_template.md` → applies the 3-tweet format
3. Agent reads `references/bigquery_hashtags.md` → picks the right hashtags
4. Outputs a complete thread with emoji, character counts, and `#NowGA`

---

## Tech Stack

- **Antigravity CLI (`agy`)** — AI coding assistant by Google
- **Google Agent Development Kit (ADK) 2.3.0** — framework for building agents
- **Google Agents CLI (`agents-cli`)** — scaffolds and runs ADK agents locally
- **`npx skills`** — package manager for installing agent skills
- **Python, Pydantic, SQL**

---

## Project Structure

```
Day-3/
├── lab1-skills-tutorial/
│   └── workspace/
│       ├── git_test/auth.py          ← Skill 1 demo (Conventional Commits)
│       ├── api_client.js             ← Skill 2 demo (license header)
│       ├── product.json              ← Skill 3 input
│       ├── product_model.py          ← Skill 3 output (Pydantic model)
│       └── bad_schema.sql            ← Skill 4 demo (schema validator)
├── lab2-custom-skill/
│   └── bigquery-tweet-composer/
│       ├── SKILL.md                  ← Skill definition + workflow
│       ├── assets/tweet_template.md  ← Output format template
│       └── references/bigquery_hashtags.md
└── weather-assistant/                ← ADK agent scaffolded by agents-cli
    └── app/agent.py                  ← root_agent with get_weather tool
```

---

## Key Concepts Learned

- **Progressive Disclosure** — skills load only when the agent detects relevance, preventing context overload
- **Skill Authoring** — writing `SKILL.md` with clear trigger descriptions and step-by-step instructions
- **4 Skill Patterns** — from instruction-only to script-executing skills
- **npx skills** — installing community skills from GitHub registries
