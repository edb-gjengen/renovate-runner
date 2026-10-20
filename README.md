# renovate-runner

Runs [Renovate](https://docs.renovatebot.com) on edb's repositories on git.neuf.no, daily around 17:00, from
`.gitea/workflows/renovate.yaml`.

Renovate finds repositories by autodiscovery: every repository in `edb` it can write to. To add a repository, give
Renovate write access to it. Renovate then opens an onboarding PR with a `renovate.json`, unless the repository already
has one. Each repository's `renovate.json` decides what is updated and when.

## Secrets

- `RENOVATE_TOKEN`: a Gitea token with the scopes `write:repository`, `write:issue`,
  `read:user` and `read:organization`.
- `RENOVATE_GITHUB_COM_TOKEN`: a GitHub token with read-only access to public repositories. Without it Renovate hits
  GitHub's rate limit, skips GitHub Actions, pre-commit and mise lookups, and finds no release notes.

## Running it now

Actions → Renovate → Run workflow. A run also processes the checkboxes ticked on a repository's Dependency
Dashboard issue.
