# LinkedIn Automation Skill for Moltbot

Automate your LinkedIn presence with AI-powered engagement, content creation, and analytics — all from your terminal or chat.

Built for [Moltbot](https://molt.bot), this skill gives your AI assistant full control over LinkedIn: posting, commenting with @mentions, reposting, reading your feed, tracking engagement analytics, monitoring likes, and learning your personal writing style.

## Features

| Capability | What It Does |
|---|---|
| **Post & Publish** | Create text posts (image support included) directly from chat |
| **Smart Comments** | Comment on any post with automatic @mention resolution via LinkedIn typeahead |
| **Edit & Delete** | Modify or remove your comments by matching text fragments |
| **Repost with Thoughts** | Share posts to your network with your own commentary |
| **Feed Reader** | Scan your LinkedIn feed and surface relevant posts to engage with |
| **Engagement Analytics** | Track impressions, reactions, comments, and shares on your recent posts |
| **Profile Stats** | Monitor follower count, profile views, and search appearances |
| **Like Monitor** | Detect new likes/reactions on your content for timely follow-up comments |
| **Activity Scraper** | Review any LinkedIn profile's recent activity for research and outreach |
| **Voice & Style Learning** | Learns your tone, language, emoji habits, and hashtag preferences so suggestions sound like you |

## How It Works

This skill uses **Playwright** with a persistent Chromium browser session — no API keys, no LinkedIn developer account needed. Just log in once and the session persists.

Your AI assistant calls the CLI (`scripts/linkedin.py`) behind the scenes. Read-only actions (feed, analytics, likes) run freely. **Write actions (post, comment, repost) always require your explicit approval** before executing.

## Quick Start

```bash
# 1. Install dependencies
pip install playwright && playwright install chromium

# 2. Log in to LinkedIn (one-time — session persists)
python3 scripts/linkedin.py check-session

# 3. Learn your writing style
python3 scripts/linkedin.py learn-profile

# 4. Start using via Moltbot
moltbot skills install red777777/linkedin-automation
```

## Commands

```bash
python3 scripts/linkedin.py check-session          # Verify login
python3 scripts/linkedin.py feed --count 10         # Read your feed
python3 scripts/linkedin.py post --text "..."       # Publish a post
python3 scripts/linkedin.py comment --url "..." --text "Great post @Jane Doe!"
python3 scripts/linkedin.py edit-comment --url "..." --match "old" --text "new"
python3 scripts/linkedin.py delete-comment --url "..." --match "text to find"
python3 scripts/linkedin.py repost --url "..." --thoughts "My take..."
python3 scripts/linkedin.py analytics --count 10    # Post performance
python3 scripts/linkedin.py profile-stats           # Follower/view stats
python3 scripts/linkedin.py scan-likes --count 15   # New like alerts
python3 scripts/linkedin.py activity --profile-url "https://linkedin.com/in/..." --count 5
python3 scripts/linkedin.py learn-profile           # Build your style profile
```

All commands output structured JSON. Enable debug mode: `LINKEDIN_DEBUG=1`.

## @Mention Support

Comments support natural `@FirstName LastName` syntax. The skill types the name into LinkedIn's typeahead, progressively matching until it finds the right person. If no match is found, the name is inserted as plain text with a warning.

## Style Learning

On first run, `learn-profile` analyzes your recent posts and comments to build a style profile (`~/.linkedin-style.json`) capturing your:

- **Language** — German, English, or mixed
- **Tone** — casual, professional, or professional-friendly
- **Emoji usage** — heavy, moderate, or minimal
- **Top hashtags** and recurring topics
- **Sample posts** for voice reference

The AI reads this profile before drafting any suggestion, so everything sounds like **you**.

## Included Reference Guides

- **Content Strategy** — Hook formulas, post structure, optimal posting times, hashtag strategy
- **Engagement Playbook** — Algorithm signals, comment quality formulas, weekly engagement routine
- **DOM Patterns** — LinkedIn selector reference for troubleshooting and maintenance

## Rate Limit Guidelines

| Action | Daily | Weekly |
|---|---|---|
| Posts | 2-3 | 10-15 |
| Comments | 20-30 | — |
| Likes | 100 | — |
| Connection requests | 30 | 100 |

## Requirements

- Python 3.10+
- Playwright with Chromium
- [Moltbot](https://molt.bot) (or any compatible AI assistant)

## Disclaimer

This skill is for **personal, non-commercial use only**. It automates your own LinkedIn account for personal productivity. Do not use for spam, mass outreach, or scraping. Use responsibly and in accordance with [LinkedIn's User Agreement](https://www.linkedin.com/legal/user-agreement). The author assumes no liability for misuse or account restrictions.

## Author

**Andreas Kulpa** — [bigdataheaven.com](https://bigdataheaven.com)

---

Built for [Moltbot](https://molt.bot) — your AI-powered messaging gateway.
