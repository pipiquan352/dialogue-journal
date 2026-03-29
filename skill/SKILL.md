---
name: dialogue-journal
description: Use when the user says "沉淀一下", "记录一下", "这个对话值得分享", or wants to distill the current conversation into a shareable journal entry. Also use when invoking /journal or /沉淀.
---

# Dialogue Journal

Distill the current conversation into a refined dialogue-style journal entry, generate an HTML episode page, and publish it to the conversation journal site.

## When to Use

- User says "沉淀一下", "记录一下", "这个值得分享"
- User invokes /journal or /沉淀
- At end of a conversation the user found insightful

## Process

### Step 1: Identify Key Moments

Review the current conversation. Look for:
- Insights or realizations ("等一下，你发现了吗？")
- Turning points where the direction changed
- Ideas that crystallized through discussion
- Emotional or philosophical depth
- Humor and personality

**Do NOT include:** debugging details, code output, file paths, error messages, routine task execution.

### Step 2: Distill the Dialogue

Rewrite the highlights as a **refined conversation** between ππ and 小螃蟹:

- **Keep the dialogue format** — this is the core identity
- **Preserve voice and rhythm** — ππ's directness, 小螃蟹's reflective responses
- **Remove noise** — condense, rephrase, but keep the natural feel
- **Add `{ type: 'breath' }` separators** between thematic shifts
- **Mark key insights** with `<span class="insight">...</span>`
- **Mark emphasis** with `<em>...</em>`
- **Aim for 8-15 turns** — tight, not exhaustive
- **Make it self-contained** — a stranger should follow without context

Present the distilled dialogue to the user for review before generating.

### Step 3: Generate Episode

Once the user approves the content:

1. **Choose a title** — 中文 main title + English subtitle (both short)
2. **Choose tags** — 1-3 short tags for the episode
3. **Pick 2 preview lines** — one from ππ, one from 小螃蟹, for the index page
4. **Date** — use today's date in format `YYYY-MM-DD`

Create the episode HTML by copying the template structure from the most recent episode in `C:\Users\menquan\conversation-journal\episodes\`. The key parts to change:

- `<title>` tag
- `.header-date` content
- `.header-title` (中文标题)
- `.header-subtitle` (English subtitle)
- `.header-intro` (1-2 sentence intro for context)
- `CONVERSATION` array in the `<script>` (the distilled dialogue)

Save to: `C:\Users\menquan\conversation-journal\episodes\{YYYY-MM-DD}.html`

### Step 4: Update Index

In `C:\Users\menquan\conversation-journal\index.html`, add a new entry to the **beginning** of the `EPISODES` array (newest first):

```javascript
{
  date: 'Month DD, YYYY',
  title: '中文标题',
  subtitle: 'English subtitle',
  file: 'episodes/YYYY-MM-DD.html',
  preview: [
    { who: 'ππ', text: '...' },
    { who: '小螃蟹', text: '...' },
  ],
  tags: ['tag1', 'tag2'],
},
```

### Step 5: Publish

```bash
cd ~/conversation-journal
git add episodes/{date}.html index.html
git commit -m "Add episode: {title}"
git push
```

Provide the live URL: `https://pipiquan352.github.io/dialogue-journal/episodes/{date}.html`

## Important Notes

- **Always show the distilled dialogue to the user first** — they may want to adjust tone, remove something, or add context
- **Speaker names are always ππ and 小螃蟹** — never use real names
- **The intro line sets context for strangers** — write it as if the reader knows nothing
- **Keep the warm earth-tone design** — don't modify CSS unless asked
