---
name: project-site-structure
description: Key file locations, nav ordering, and config conventions for the CoVLab al-folio site
metadata:
  type: project
---

Site URL: https://kubicina.github.io/covlab/
Base URL: /covlab/
Theme: al_folio_core (gem-owned; do NOT touch \_layouts/, \_includes/, \_sass/)

Nav order (nav: true pages in \_pages/):

- nav_order 2: publications (/publications/)
- nav_order 3: projects (/projects/)
- nav_order 4: people (/people/) ← set when People page was created
- nav_order 7: (was people, now moved to 4)

Important \_config.yml conventions:

- Per-person bio content files in \_pages/ that should NOT become standalone pages must be listed in the `exclude:` block (e.g., \_pages/about_einstein.md, \_pages/people_pi_placeholder.md).
- imagemagick.enabled: true — processes assets/img/ for responsive WebP; images placed in assets/img/people/ will be processed automatically.
- scholar.last_name / first_name controls the "author highlight" in bibliography rendering.

Data files in \_data/:

- people.yml — lab member roster (created 2026-06-06)
- coauthors.yml — publication co-author name→URL mapping (for bibliography)
- cv.yml — CV data
- featured_plugins.yml — plugin feature flags (starter wiring, do not repurpose)
- repositories.yml, socials.yml, citations.yml, venues.yml — other starter data
