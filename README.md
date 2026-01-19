# 🚀 Complete GitHub Profile Setup Guide

## Step 1: Create Your Profile Repository

1. Go to GitHub and create a **new repository**
2. Name it **exactly** as your GitHub username (e.g., `pranaypatel`)
3. Make it **Public**
4. Check "Add a README file"
5. Click "Create repository"

---

## Step 2: Add the README Content

1. Go to your repository
2. Click on `README.md` file
3. Click the **pencil icon** (Edit)
4. **Delete all content** and paste the new README from the artifact
5. **Important**: Replace all instances of `pranaypatel` with your actual GitHub username
6. Click "Commit changes"

---

## Step 3: Enable Snake Animation (Optional but Awesome!)

### Create the GitHub Action Workflow:

1. In your profile repository, create this folder structure: `.github/workflows/`
2. Inside `workflows` folder, create a file named `snake.yml`
3. Paste this code:

```yaml
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 */12 * * *"  # Runs every 12 hours
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: Generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Push github-contribution-grid-snake.svg to output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

4. Commit this file
5. Go to **Actions** tab in your repository
6. Click on "Generate Snake Animation" workflow
7. Click "Run workflow" → "Run workflow"
8. Wait 1-2 minutes for it to complete
9. The snake animation will now work!

---

## Step 4: Enable WakaTime Stats (Optional)

WakaTime shows your weekly coding statistics (languages, time spent, etc.)

### Setup:

1. Sign up at [https://wakatime.com](https://wakatime.com)
2. Install WakaTime plugin in VS Code (or your IDE)
3. Copy your WakaTime API Key from dashboard
4. In your GitHub profile repo, go to **Settings** → **Secrets and variables** → **Actions**
5. Click "New repository secret"
6. Name: `WAKATIME_API_KEY`
7. Value: Paste your API key
8. Click "Add secret"

### Create WakaTime Workflow:

Create `.github/workflows/waka.yml`:

```yaml
name: WakaTime Stats

on:
  schedule:
    - cron: '0 0 * * *'  # Runs at 00:00 UTC every day
  workflow_dispatch:

jobs:
  upd
