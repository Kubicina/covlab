---
name: project-people-page
description: Architecture of the /people/ page — profiles.md + people.yml + per-person content files
metadata:
  type: project
---

The People page lives at permalink `/people/` and is implemented across three layers:

1. `_pages/profiles.md` — uses `layout: profiles` (al_folio_core gem). The front matter `profiles:` list renders featured cards (photo + bio text + contact info). The page body contains Liquid that iterates `site.data.people` grouped by `group` field to render all members as Bootstrap cards.

2. `_data/people.yml` — the authoritative roster. Each entry has: `name`, `title`, `role`, `image` (relative to `assets/img/people/`), `expertise` (list), `email`, `orcid`, `scholar`, `website`, `content` (optional `_pages/` filename for bio), `group` (one of: principal_investigators, researchers, phd_students, master_students, alumni), `active` (true/false).

3. Per-person bio files in `_pages/` — plain Markdown snippets, no front matter needed. Referenced by `content:` field in `people.yml`. Must be added to the `exclude:` list in `_config.yml` to avoid being built as standalone pages.

Photos go in `assets/img/people/`. Use `placeholder.jpg` until real photos are available.

Group display order: Principal Investigators → Researchers & Postdocs → PhD Students → Master Students → Alumni (alumni shown only when active: false entries exist).

**Why:** The `layout: profiles` pattern is the al-folio built-in for people/team pages. Using `_data/people.yml` separates content from presentation so new members can be added by editing one data file only.
