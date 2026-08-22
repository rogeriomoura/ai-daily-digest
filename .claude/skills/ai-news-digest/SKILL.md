---
name: ai-news-digest
description: Research today's AI news (model releases, notable open-source projects, other significant news) and publish a dated digest to this repo. Use when asked to produce or update the daily AI digest.
---

# AI News Digest

Produces one dated markdown file summarizing what happened in AI today, then commits and pushes it. Written to run unattended (no human review before the push), so favor accuracy and restraint over volume — skip anything unverified rather than guessing.

## Steps

1. **Get today's date** (`date +%Y-%m-%d`, local run environment date is fine — this is a daily cadence, not a precise timestamp).

2. **Check recent digests** — read the last 2–3 files in `digests/` (if any exist) so today's picks don't repeat yesterday's.

3. **Research**, using web search across three angles. Don't over-search — a handful of targeted queries beats a broad crawl:
   - **Model releases**: new or updated models from major labs (OpenAI, Anthropic, Google, Meta, Mistral, xAI, DeepSeek, Qwen, and similar) — new checkpoints, notable benchmark claims, API/pricing changes.
   - **Open source**: newly trending or newly notable open-source AI projects, libraries, or tools worth a developer's attention.
   - **Other news**: anything else clearly significant that day — funding, policy/regulation, notable papers, major outages/incidents. Skip routine opinion pieces and rehashed takes.

4. **Select and filter.** Aim for roughly 5–10 items total across all three categories, favoring genuinely new/notable over comprehensive. Drop anything that's a duplicate of a recent digest, unverified/rumor-only, or not really AI news.

5. **If it's a slow day**, still write a short entry (even just 1–2 items, or a one-line "quiet day, nothing major" note) rather than skipping the run entirely — a missing file is indistinguishable from a broken routine; a "quiet day" file is not.

6. **Write `digests/<today's date>.md`**:

   ```markdown
   # AI Daily Digest — <YYYY-MM-DD>

   ## Model Releases
   - **<Headline>** — <1-3 sentence summary>. [Source](<url>)

   ## Open Source
   - **<Headline>** — <1-3 sentence summary>. [Source](<url>)

   ## Other News
   - **<Headline>** — <1-3 sentence summary>. [Source](<url>)
   ```

   Omit any section with no items that day rather than leaving it empty.

7. **Update `README.md`**:
   - Replace the `**Latest:**` line with a link to today's file.
   - Add today's file to the top of the `## Archive` list (newest first), as `- [<YYYY-MM-DD>](digests/<YYYY-MM-DD>.md)`.

8. **Commit and push** directly to `main`:
   ```
   git add README.md digests/<today's date>.md
   git commit -m "Daily digest: <YYYY-MM-DD>"
   git push
   ```
