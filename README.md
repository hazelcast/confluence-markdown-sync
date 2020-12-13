# Confluence Markdown Sync Action

This Github Action serves the purpose of copying the contents of a Markdown `.md` file to a Confluence Cloud Page.

## Getting Started

```yml
# .github/workflows/my-workflow.yml
on: [push]

jobs:
  dev:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2

    - uses: confluence-markdown-sync
      with:
        from: './README.md'
        to: '123456' # The confluence page id where to write the output
        cloud: <my-confluence-cloud-id>
        user: <my.user@example.org>
        token: <my-token>

```

## Authentication

Uses basic auth for the rest api.

- `cloud`: The ID can be found by looking at yout confluence domain: `https://xxx.atlassian.net/...`
- `user`: The user that generated the access token
- `token`: You can generate the token [here](https://id.atlassian.com/manage-profile/security/api-tokens). Link to [Docs](https://confluence.atlassian.com/cloud/api-tokens-938839638.html)

- `to`: The page ID can be found by simply navigating to the page where you want the content to be postet to and looke at the url. It will look something like this: `https://<cloud-id>.atlassian.net/wiki/spaces/<space>/pages/<page-id>/<title>`