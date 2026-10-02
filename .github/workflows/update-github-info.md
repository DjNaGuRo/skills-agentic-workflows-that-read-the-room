---
name: update-github-info
description: Refresh Mona's GitHub Info content from official GitHub Blog and Changelog sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
network:
  allowed:
    - defaults
    - github.blog
    - github.com
tools:
  edit: true
  web-fetch:
  github:
    toolsets: [repos]
safe-outputs:
  create-pull-request:
    draft: true
---

# Update GitHub Info

Keep `site/content/github-info.md` current with practical, concise GitHub guidance for Mona's website.

## Research

1. Read `notes/mona-notes.md` and `site/content/github-info.md` using repository file tools. Follow Mona's editorial guidance and preserve the existing structure and themes.
2. Use the web-fetch tool to read both official sources:
   - https://github.blog/latest/
   - https://github.blog/changelog/
3. Select only recent, useful items that help developers learn GitHub faster. Verify every update against its official source; do not infer details beyond what the source says.

## Update

Edit only `site/content/github-info.md`. Add or refresh concise summaries of worthwhile items and include a direct source link for every item drawn from the GitHub Blog or Changelog. Keep existing useful content, remove only stale information that the sources clearly supersede, and do not invent updates when there is nothing worth adding.

## Propose for review

If the file has meaningful changes, use the configured `create-pull-request` safe output to open one draft pull request for Mona to review. Summarize the updates and cite their official source URLs in the PR description. Do not push or write changes directly to the default branch. If there are no meaningful changes, do not open a pull request.
