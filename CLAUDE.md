# iseeart Feedback Site — Claude Context

## What this project is
A password-protected static site (GitHub Pages) for collecting and presenting structured UX/product feedback on **isee.art** — an AI-powered platform that helps artists manage their catalog, build a portfolio site, and share work with collectors.

The feedback is gathered by Alon and shared with the isee.art team.

## My role
- Maintain `feedback.json` — add new items when Alon describes them or drops screenshots
- Keep `index.html` design clean and functional
- Commit and push changes to trigger auto-deploy

## About isee.art
- Mobile-first, AI-powered art management platform
- Key features: AI artwork import, digital catalogs, portfolio websites (custom `artist.isee.art` subdomains), QR tags, live insights, inventory management
- Artists get a profile page at `[name].isee.art` — e.g. `maygrabli.isee.art`
- Paid plan: isee.white at $290/yr

## Current feedback subject
Artist profile pages on isee.art — using **maygrabli** (May Grabli, painter from Yaffa) as the sample. She is also a real testimonial user on the platform.

## Critical: always pull before committing
ALWAYS run `git pull` before making any changes to `feedback.json` or `statuses.json`.
The user changes statuses via the UI (which commits directly to the remote via GitHub API).
If you commit without pulling first, you will overwrite their status changes.

When adding a new feedback item:
1. `git pull` — get the latest statuses
2. Add the item to `feedback.json`
3. Add `"<id>": "Open"` to `statuses.json` (leave all other entries untouched)
4. Rename any new screenshots to the naming convention
5. Commit and push

## How to add feedback
Alon will describe an issue or drop a screenshot. I interpret it, assign a category, write a clean title + description, and update `feedback.json`.

If a screenshot is provided, save it to `screenshots/` and reference the filename in the item.

**Categories:** `UI/UX Bug`, `Product Idea`, `User Flow`, `General`

## Feedback item schema
```json
{
  "id": 3,
  "title": "Short, specific title",
  "category": "Product Idea",
  "section": "Public Profile",
  "priority": "Low",
  "screenshot": "screenshot-003.png",
  "description": "Clear explanation of the issue or idea."
}
```
Set `"screenshot": null` when there's no image.

**Screenshot naming convention:** `{zero-padded-id}-{kebab-slug}.png` — e.g. `004-contact-topic-dropdown.png`
Always rename macOS auto-generated screenshot filenames to this convention before committing, and update the `screenshot` field in `feedback.json` accordingly.

**Sections:** `Public Profile`, `Dashboard` — keep it at these two, no sub-sections.

**Priority values:** `High`, `Medium`, `Low` — default to `Low` when not specified.

## Live site
https://alon-slutzky.github.io/iseeart-feedback/
Password: `iseeart`

## Design principles
- Cards are text-forward — description is the primary content
- Screenshots are optional small thumbnails (right side of card), never dominant
- No placeholder shown when screenshot is absent
- Keep it minimal and fast to scan
