---
name: bigquery-tweet-composer
description: |
  Composes tweet threads for Google BigQuery release note announcements.
  Use this skill when the user asks to tweet a BigQuery update, share a
  release note on X/Twitter, or compose a developer announcement thread.
  Do NOT use for general social media content or non-BigQuery topics.
version: 1.0.0
license: Apache-2.0
allowed-tools: Read Write
metadata:
  author: kanika-mamgain
---

# BigQuery Tweet Composer Skill

Turns raw BigQuery release notes into concise, developer-friendly tweet threads optimized for X/Twitter.

## When to use
- User provides a BigQuery release note (text, URL, or category + description)
- User says "tweet this", "share on X", "compose a thread", or "write a tweet for this update"

## When NOT to use
- General Twitter drafting unrelated to BigQuery
- Marketing copy or promotional material
- Release notes from other Google products (use a different skill)

## Workflow

1. **Read the template** at `assets/tweet_template.md` to understand the output format.
2. **Read the guidelines** at `references/bigquery_hashtags.md` to choose correct hashtags.
3. **Classify the update type** from the note content:
   - `Feature` → use 🚀
   - `Announcement` → use 📢
   - `Changed` → use 🔄
   - `Fix` / `Known Issue` → use 🛠️
   - `Deprecated` → use ⚠️
4. **Compose Tweet 1** (max 280 chars): hook sentence + emoji + type badge.
5. **Compose Tweet 2** (max 280 chars): key details / what changed / impact.
6. **Compose Tweet 3** (max 280 chars): call to action + 2-3 hashtags from the reference guide.
7. **Output** the full thread using the template format.

## Rules
- Never exceed 280 characters per tweet (count carefully).
- Always include `#BigQuery` in Tweet 3.
- Never invent facts — only use information from the provided release note.
- Use plain developer language — avoid marketing buzzwords.
