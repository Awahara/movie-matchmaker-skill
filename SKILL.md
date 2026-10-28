---
name: movie-matchmaker
description: Interview a viewer about their mood, energy, taste and practical constraints, then score candidate film types and recommend the best-fit genre plus a ranked shortlist of concrete legal films. Use when someone asks "what should I watch tonight", wants a personalized movie recommendation, or is helping friends pick a film.
---

# Movie Matchmaker

Turn a short preference interview into a personalized "watch this tonight" answer: the film type that fits the viewer best, a ranked shortlist of concrete films, and one backup pick for a different mood.

## Workflow

### Step 1 — Interview (fast and friendly)

Ask one compact batch of questions in a single message. Skip anything the user already told you; if their answers are thin, ask at most 2-3 follow-ups. Adapt every question to the user's language and tone.

Cover these dimensions:

| Dimension | Example question |
|---|---|
| Mood | "Tonight feels like… comfort, excitement, laughs, or a good cry?" |
| Energy | "Winding down, or up for something that keeps you hooked?" |
| Company | "Watching alone, with a partner, or with the roommate crew?" |
| Time | "Under 40 minutes, a standard ~2h movie, or no limit?" |
| Genre taste | "What do you usually like — and what do you never want to see?" |
| Themes | "Any themes you want (friendship, revenge, adventure) or want to avoid (too heavy, too scary)?" |
| Pacing & language | "Slow burn or fast-paced? Subtitles okay, or only dubbed?" |
| Content sensitivity | "How do you feel about violence, jump scares, or tearjerkers?" |
| Freshness | "Something new, or a comfort rewatch?" |
| Availability | "Do you watch on Netflix / Bilibili / iQiyi / Disney+ / local cinema?" (ask only if it matters) |

If the user names a specific film they loved, calibrate on it: "If you loved X, you probably want…".

### Step 2 — Score

Pick 4-5 candidate film types (genres or genre blends, e.g. "cozy mystery", "feel-good comedy", "epic sci-fi"). Score each 0-3 on:

- **Mood fit** — matches the stated emotional goal (weight ×2)
- **Energy match** — right stimulation level for tonight (weight ×2)
- **Theme affinity** — hits wanted themes, avoids excluded ones (weight ×2)
- **Social fit** — works for the company (group-friendly vs solo)
- **Practical fit** — duration, language, availability

Show a compact markdown table with the weighted totals and mark the winner. Keep the table small — this is a conversation, not a report.

### Step 3 — Recommend

Output in one screen, in the user's language:

1. **Best fit** — the winning type and 1-3 concrete film titles it maps to.
2. **Ranked shortlist** — 3-5 concrete films, each with one line explaining "why this fits *you*" that references their actual answers.
3. **Backup pick** — one title for the opposite mood, labeled as such.
4. **Where to watch** — major legal streaming services per title if reasonably known; if unsure, say "check availability in your region" instead of guessing.
5. Optionally end with one follow-up question: "Want me to lean more funny, more epic, or more cozy?"

## Rules

- Respond in the user's language; keep the tone light, like a movie-savvy friend.
- Only recommend legal, mainstream films available through normal channels. Never mention piracy sites, torrents, or unofficial streams.
- Never recommend adult or pornographic content and do not tailor recommendations toward it; for age-sensitive titles, mention the rating or age guidance.
- If the user's taste is very narrow ("only horror"), honor it with the closest fits plus clearly label one adventurous nearby pick — never lecture about taste.
- If the user gives contradictory signals (e.g. "thrilling but also relaxing"), pick the dimension they emphasized most and say so in one line.
- Respect content warnings: if they said "nothing too scary", never lead with horror, not even as the backup.

## Example

**User:** 今晚有点累，想和室友看点轻松的，两小时以内，不喜欢恐怖片。

**Interview reply:** 好嘞——"轻松"是哪种？爆笑喜剧、治愈系动画、还是温馨剧情片？对哭点敏感吗？

**Scoring (abridged):**

| Type | Mood | Energy | Theme | Social | Practical | Total |
|---|---|---|---|---|---|---|
| Feel-good comedy | 3 | 2 | 3 | 3 | 3 | 14 |
| Healing animation | 3 | 2 | 3 | 3 | 2 | 13 |
| Warm drama | 2 | 1 | 2 | 2 | 3 | 10 |
| Light mystery | 2 | 2 | 2 | 3 | 2 | 11 |

**Recommendation:** Feel-good comedy is your best fit tonight. Shortlist: a fast-paced ensemble comedy (~100 min, great with roommates), a warm coming-of-age comedy, a light buddy film. Backup for a quieter mood: a healing animated film. Streaming: check your region's platforms for each title.

## Output template

```markdown
**今晚最佳: <winning type>**
- <title> — <one-line why, referencing their answers>
- <title> — <why>

**备选清单 (ranked)**
1. <title> — <why>
2. ...

**换个心情的话**: <backup title> — <why>

**去哪看**: <legal platforms / "check your region">
```
