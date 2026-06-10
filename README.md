# fork-sync 🔄

Automatically keeps **all your GitHub forks** in sync with their upstream repositories — every week, hands-free.

## How It Works

A single GitHub Action runs **every Monday at 6am UTC**:

1. Lists every fork on your account via the GitHub API
2. Calls the [`merge-upstream`](https://docs.github.com/rest/branches/branches#sync-a-fork-branch-with-the-upstream-repository) endpoint for each one (same as clicking **"Sync fork"** in the UI)
3. Posts a summary report — synced / up-to-date / failed — in the Actions run summary

No clones, no checkouts, no force-pushes. Pure API. A fork with merge conflicts is skipped and reported, never overwritten.

## Setup

1. Create a [Personal Access Token](https://github.com/settings/tokens) with `repo` scope
2. Add it as a repository secret named **`FORK_SYNC_PAT`**
   (Settings → Secrets and variables → Actions → New repository secret)
3. Done — it runs automatically every Monday

### Manual run

Actions tab → **Sync All Forks** → **Run workflow**

## Why Not GITHUB_TOKEN?

The default `GITHUB_TOKEN` only has access to the repo the workflow runs in. Syncing *other* repos on your account requires a PAT with `repo` scope.

---

Made with ❤️ by [Lord1Egypt](https://github.com/Lord1Egypt)
