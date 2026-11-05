---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

engine:
  id: copilot
  copilot-sdk: true

model: auto

tools:
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    draft: true
    max: 1
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Keep `site/content/github-info.md` current with concise, practical updates for developers.

## Instructions

1. Read `notes/mona-notes.md` and follow Mona's editorial guidance.
2. Use `web-fetch` to read https://github.blog/latest/ and https://github.blog/changelog/.
3. Select only useful, recent items that fit the site's focus. Verify details from the fetched pages and cite the source URL for every update derived from the GitHub Blog or Changelog.
4. Edit only `site/content/github-info.md`. Keep summaries short and practical, avoid duplicating existing themes, and preserve the file's existing structure and style.
5. If there are meaningful updates, propose them in a draft pull request for Mona to review. Describe the sources and changes in the pull request. Do not write directly to the default branch. If nothing merits an update, do not open an empty pull request.