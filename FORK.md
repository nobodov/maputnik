# Fork notes

This fork exists to produce Windows `.exe` builds of Maputnik from `main`.

## Workflows

| Workflow | Trigger | Purpose |
|---|---|---|
| `Sync fork with upstream` | Daily + manual | Fast-forwards `main` from `maplibre/maputnik` |
| `Build Windows Desktop` | Push to `main` + manual | Builds `maputnik.exe`, publishes to `nightly-main` release |

Inherited upstream workflows (`deploy`, `release`, …) are disabled — they target the upstream org and fail on a fork.

## Sync from upstream

**Actions → Sync fork with upstream → Run workflow.**
Runs automatically once a day; use this button to force it. BUT GitHub disables cron workflows after 60 days of repo inactivity. For this reason is needed to run sync manually by Click **Run workflow**

## Build Windows `.exe`

**Actions → Build Windows Desktop → Run workflow.**
Also triggers automatically after every sync. Takes 2–3 minutes.

## Get the binary

- **Releases → `nightly-main` → `maputnik.exe`** — permanent, overwritten each build.
- **Actions → run → Artifacts → `maputnik-windows`** — expires in 90 days.

## Troubleshooting

- **Sync fails with "not possible to fast-forward"** — the fork's `main` has diverged. Reset it via GitHub's "Sync fork" button on the repo page, or keep custom changes on a separate branch.
- **Scheduled sync stopped running** — GitHub disables cron workflows after 60 days of repo inactivity. Click **Run workflow** once to re-enable.
- **A re-enabled upstream workflow starts failing again** — disable it again via Actions → workflow → ⋯ → Disable.
