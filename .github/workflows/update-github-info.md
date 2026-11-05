---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:

permissions: read-all

engine:
  id: copilot
  copilot-sdk: true

tools:
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` to understand Mona's editorial direction and the current content.

Use `web-fetch` to read both official sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Choose timely, useful items for developers. Update only `site/content/github-info.md`, keeping summaries short and practical. Attribute each update to its source with a link, and do not invent facts or include information that is not supported by the fetched pages.

Propose the change by creating a pull request for Mona to review. Do not write directly to `main` or merge the pull request.