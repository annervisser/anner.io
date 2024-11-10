---
date: '2023-02-24T11:59:44+01:00'
title: 'Gamifying Psalm baseline reduction'
tags: ['psalm', 'github-actions']
cover:
    image: /images/gamifying-psalm-baseline.png
    alt: Screenshot of a comment on GitHub showing the baseline reduced by 1
---

When using PHP static analysis tools like Psalm,
how do we motivate a team to work on decreasing the baseline? Gamification!

❓ Static analysis?
When writing modern PHP code, static analysis tools like Psalm and PHPStan are essential
to prevent mistakes caused by PHP's dynamic nature.
They provide types not in the language, generics and much more.

📋 What's a baseline?
To introduce these tools into legacy code is quite a challenge:
It's a huge task to immediately fix all errors.
This is why they allow you to create a baseline file: a file that lists all current errors
and tells the tool to ignore them for now.
This is great to ensure the quality of new code, 
and means you don't have to refactor all existing code at once.

👾 How about that gamification?
But how do you motive your team to get this baseline smaller?
Let's add a bit of gamification, 
by commenting on any pull request that improves (or worsens) the baseline.

I've made a GitHub action that makes this very easy to do.

[View the full documentation on GitHub](https://github.com/annervisser/psalm-baseline-progress-action)

Or add this workflow to your repository:
```yaml
# .github/workflows/psalm-baseline-comment.yml
on:
  pull_request:
jobs:
  comment-psalm-baseline:
    runs-on: ubuntu-latest
    permissions:
      contents: read # Default permission when no others are specified, needed for actions/checkout
      pull-requests: write # Needed to post a comment on a pull request
    steps:
      - uses: actions/checkout@v4

      - id: baseline-scores
        uses: annervisser/psalm-baseline-progress-action@v1

      - uses: thollander/actions-comment-pull-request@v3
        with:
          message: ${{ steps.psalm-baseline-progress-action.outputs.output_message }}
          comment-tag: 'psalm_baseline_score_comment' # Add marker so existing comment can be updated
          create-if-not-exists: ${{ steps.psalm-baseline-progress-action.outputs.score_diff != 0 }} # Only create comment when baseline score changed, but always update existing comment
          # github-token: <a GitHub PAT> # Only needed to comment on pull requests coming from forks
```
