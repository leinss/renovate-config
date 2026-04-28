# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for repos under [`leinss`](https://github.com/leinss).

## Usage

In any consumer repo, add `renovate.json`:

```json
{
  "extends": ["github>leinss/renovate-config"]
}
```

Then enable the [Renovate GitHub App](https://github.com/apps/renovate) on the repo.

## Policy summary

- **`minimumReleaseAge: "7 days"`** — wait 7 days after a package version is published before opening a PR. Mitigates supply-chain attacks where compromised versions are caught and yanked within hours/days of publication.
- **Schedule:** Monday before 6am (Europe/Berlin) — batched weekly.
- **Grouping:** minor & patch updates batched into a single weekly PR; `@types/*` grouped separately.
- **Security overrides:** `vulnerabilityAlerts.minimumReleaseAge: "0 days"` — security patches bypass cooldown and ship immediately.
- **Limits:** max 5 concurrent open PRs, max 2 created per hour.

## Editing

Change `default.json` and merge to `main` — all consumer repos pick up the new policy on their next Renovate run.
