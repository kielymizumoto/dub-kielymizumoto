# Self-hosting notes

This repository deploys Dub independently at:

- Dashboard: `dub.kielymizumoto.com`
- Short links: `go.kielymizumoto.com`

The root `kielymizumoto.com` website and the existing OpenReply Railway project
are outside this deployment.

## Intentional differences from upstream

- `apps/web/vercel.json` is removed because Dub's official self-hosting guide
  says the upstream Dub production cron schedule is not required for a
  self-hosted instance.
- The dashboard and default short-link hostnames are read from
  `NEXT_PUBLIC_APP_DOMAIN` and `NEXT_PUBLIC_APP_SHORT_DOMAIN`.
- `DefaultDomains` contains only the normalized self-hosted short domain, so
  new workspaces use `go.kielymizumoto.com` instead of Dub-owned domains.

No Enterprise Edition code or licensing notices are modified.

## Updating from Dub

Fetch and merge upstream into a review branch before updating production:

```bash
git fetch upstream
git switch -c codex/update-dub-YYYY-MM-DD
git merge upstream/main
```

Resolve conflicts while retaining the small self-hosting differences above,
then run the build and deployment checks before merging to `main`.
