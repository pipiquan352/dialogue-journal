# Dialogue Journal 对话即创作

Turn your best AI conversations into beautiful, shareable journal entries.

## What is this?

A conversation journal that distills insightful dialogues between human and AI into refined, editorial-style web pages — designed for screen recording and sharing on social media.

**Live site:** https://pipiquan352.github.io/dialogue-journal/

## How it works

1. Have a meaningful conversation with Claude
2. Say "沉淀一下" or invoke `/journal`
3. Claude distills the highlights into a refined dialogue
4. A beautiful HTML page is generated with typing animations
5. Record your screen → post to social media

Your creation cost is **zero** — the conversation itself is the content.

## Claude Code Skill

Copy `skill/SKILL.md` to your `~/.claude/skills/dialogue-journal/` folder to enable the `/journal` command in Claude Code.

## Design

- Mobile-first (440px) optimized for vertical screen recording
- Warm earth tones, editorial typography (Cormorant Garamond + Inter)
- Auto-playing typing animations with breathing pauses
- Replay button for re-recording

## Structure

```
index.html          — Collection homepage
episodes/           — Individual journal entries
skill/SKILL.md      — Claude Code skill definition
```
