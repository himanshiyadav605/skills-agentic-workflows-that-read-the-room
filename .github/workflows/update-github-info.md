---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
model: gpt-5-mini
---

# Update GitHub Info for Mona

Before making any changes, read `notes/mona-notes.md` and follow its editorial guidance. Then review the current `site/content/github-info.md` so updates preserve useful existing material and fit the site's practical focus.

Use `web-fetch` to consult both official sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Identify recent developments that are relevant to developers learning or using GitHub. Verify each proposed fact against its source. Keep updates concise and practical; do not add speculation, marketing language, or details that the sources do not support. Include source context in `site/content/github-info.md`: link to the specific article or changelog entry and identify its date and the practical takeaway. Preserve existing editorial guidance and homepage themes unless an official source gives a clear reason to update them. Avoid duplicating material already covered.

Use the `edit` tool to make changes only to `site/content/github-info.md`. Do not write, commit, or push changes directly to `main` or the default branch. Once the file contains a worthwhile, source-verified update, use the configured `create-pull-request` safe output to open a draft pull request for Mona to review. Summarize the changes and cite the official sources in the pull request description. Do not create an issue as a fallback. If neither source has a useful update, leave the file unchanged rather than inventing content.
