# 🤖 Automation Guide

A guide to the automation systems powering this GitHub profile.

---

## 📋 Automation Overview

This profile uses GitHub Actions workflows to maintain an up-to-date presence. The automation handles stats updates and contribution visualizations.

### 🔄 Active Workflows

| Workflow | Schedule | Purpose | File |
|:---------|:---------|:--------|:-----|
| Advanced Automation | Daily + Every 6h | Stats & timestamp updates | `advanced-automation.yml` |
| Profile Stats | Every 6 hours | Statistics refresh | `profile-stats.yml` |
| Snake Animation | Daily at midnight | Contribution grid animation | `snake.yml` |
| README Update | Daily at midnight | Timestamp refresh | `update-readme.yml` |

---

## 🔧 Workflow Details

### 1. Advanced Profile Automation

**File:** `.github/workflows/advanced-automation.yml`

**Triggers:**
- ⏰ Daily at midnight UTC
- ⏰ Every 6 hours
- 🚀 On push to main branch
- 🎯 Manual dispatch

**Functions:**
- Generates repository statistics
- Updates README timestamp
- Commits changes with descriptive messages
- Creates workflow run summary

```yaml
# Key configuration
on:
  schedule:
    - cron: '0 0 * * *'   # Daily at midnight
    - cron: '0 */6 * * *' # Every 6 hours
  workflow_dispatch: {}   # Manual trigger
  push:
    branches: [main]
```

**Output:**
- Updated timestamp in README footer
- Repository statistics logged to workflow summary

---

### 2. Profile Stats Update

**File:** `.github/workflows/profile-stats.yml`

**Triggers:**
- ⏰ Every 6 hours
- 🎯 Manual dispatch

**Neural Functions:**
- Refreshes GitHub statistics cache
- Ensures stats cards display current data
- Triggers external stat services refresh

---

### 3. Snake Contribution Animation

**File:** `.github/workflows/snake.yml`

**Triggers:**
- ⏰ Daily at midnight UTC
- 🚀 On push to main branch
- 🎯 Manual dispatch

**Neural Functions:**
- Generates animated snake eating contribution graph
- Creates both light and dark mode SVGs
- Generates ocean-themed GIF animation
- Pushes artifacts to `output` branch

**Output Files:**
- `github-contribution-grid-snake.svg` (light mode)
- `github-contribution-grid-snake-dark.svg` (dark mode)
- `ocean.gif` (animated ocean theme)

**Usage in README:**
```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/technosaran/technosaran/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/technosaran/technosaran/output/github-contribution-grid-snake.svg" />
  <img alt="github-snake" src="https://raw.githubusercontent.com/technosaran/technosaran/output/github-contribution-grid-snake.svg" />
</picture>
```

---

### 4. README Timestamp Update

**File:** `.github/workflows/update-readme.yml`

**Triggers:**
- ⏰ Daily at midnight UTC
- 🎯 Manual dispatch

**Neural Functions:**
- Updates the "Last update" timestamp in README
- Maintains profile freshness indicators
- Clean commit messages with [skip ci] flag

---

## 🛸 Manual Trigger Guide

All workflows support manual execution:

### Step-by-Step:
1. Navigate to **Actions** tab in your repository
2. Select the workflow you want to run
3. Click **Run workflow** button
4. Select the branch (usually `main`)
5. Click **Run workflow** to execute

### Use Cases:
- 🔧 Testing workflow changes
- 🔄 Forcing immediate stat refresh
- 🐛 Debugging automation issues
- 📊 Regenerating snake animation

---

## ⚛️ Customization Guide

### Changing Schedule Frequency

Modify the `cron` expression in workflow files:

```yaml
schedule:
  - cron: '0 */12 * * *'  # Every 12 hours
  - cron: '0 6 * * *'     # Daily at 6 AM UTC
  - cron: '0 0 * * 0'     # Weekly on Sundays
```

**Cron Expression Format:** `minute hour day month weekday`

| Field | Values | Example |
|:------|:-------|:--------|
| Minute | 0-59 | `30` = at minute 30 |
| Hour | 0-23 | `6` = 6 AM UTC |
| Day | 1-31 | `1` = first day of month |
| Month | 1-12 | `*` = every month |
| Weekday | 0-6 | `0` = Sunday |

### Customizing Snake Animation

Edit `.github/workflows/snake.yml`:

```yaml
outputs: |
  dist/github-contribution-grid-snake.svg
  dist/github-contribution-grid-snake-dark.svg?palette=github-dark
  dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
```

**Custom Snake Colors:**
- `color_snake=purple` - Purple snake
- `color_snake=#A78BFA` - Quantum purple snake
- `color_dots=#8B5CF6,#A78BFA,#C084FC` - Quantum purple dots

### Modifying Commit Messages

Update the commit message in workflow files:

```yaml
git commit -m "🤖 Quantum Update: Profile synchronized [skip ci]"
```

**Emoji Conventions:**
- 🤖 - Automated updates
- 📊 - Stats updates
- 🐍 - Snake animation
- ⚛️ - Quantum updates

---

## 🔮 Troubleshooting

### Common Issues & Solutions

#### Workflow Not Running
**Problem:** Scheduled workflow doesn't execute  
**Solutions:**
1. Check if workflow file has syntax errors
2. Ensure repository has recent activity (60-day inactivity limit)
3. Verify workflow permissions in repository settings

#### Snake Animation Not Generating
**Problem:** Snake SVG not appearing or updating  
**Solutions:**
1. Check if `output` branch exists
2. Verify `GITHUB_TOKEN` permissions include `contents: write`
3. Manually trigger workflow and check logs

#### Timestamp Not Updating
**Problem:** README timestamp shows old date  
**Solutions:**
1. Check if sed pattern matches current format
2. Verify workflow has push permissions
3. Check for merge conflicts

#### Rate Limiting
**Problem:** External services return errors  
**Solutions:**
1. Reduce workflow frequency
2. Check service status pages
3. Use cached versions temporarily

---

## 📊 Monitoring Workflows

### Check Workflow Status
1. Go to **Actions** tab
2. View recent workflow runs
3. Check ✅ success or ❌ failure status
4. Click on run for detailed logs

### Enable Notifications
1. Go to **Settings** → **Notifications**
2. Enable workflow failure notifications
3. Configure email or Slack alerts

### Workflow Insights
- View execution time trends
- Monitor success/failure rates
- Identify frequently failing workflows

---

## 🌌 Advanced Automation Patterns

### Conditional Execution

```yaml
- name: Check for Changes
  id: check
  run: |
    if git diff --quiet; then
      echo "changes=false" >> $GITHUB_OUTPUT
    else
      echo "changes=true" >> $GITHUB_OUTPUT
    fi

- name: Commit Changes
  if: steps.check.outputs.changes == 'true'
  run: |
    git commit -m "Update"
    git push
```

### Matrix Builds

```yaml
strategy:
  matrix:
    theme: [dark, light]
    format: [svg, png]
```

### Caching Dependencies

```yaml
- uses: actions/cache@v3
  with:
    path: ~/.npm
    key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
```

### Workflow Artifacts

```yaml
- uses: actions/upload-artifact@v3
  with:
    name: profile-assets
    path: dist/
    retention-days: 30
```

---

## 🧬 Security Best Practices

### Token Permissions
- Use minimal required permissions
- Prefer `contents: write` over full access
- Avoid storing secrets in workflow files

### Input Validation
- Sanitize user inputs in workflows
- Validate external data before processing
- Use environment variables for sensitive data

### Audit Trail
- All workflow runs are logged
- Review runs periodically for anomalies
- Monitor for unexpected executions

---

## 🚀 Future Automation Ideas

### Potential Enhancements
- 📈 Weekly progress reports
- 🎯 Milestone celebration automation
- 📧 Contributor welcome messages
- 🏆 Achievement badge updates
- 📊 Coding time metrics integration
- 🌐 Blog post fetching automation

### Integration Opportunities
- Wakatime coding stats
- Spotify now playing
- Dev.to/Medium article sync
- Twitter/X feed integration

---

## 📚 Resources

### Official Documentation
- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Workflow Syntax Reference](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- [Cron Expression Guide](https://crontab.guru/)

### Useful Actions
- [actions/checkout](https://github.com/actions/checkout) - Repository checkout
- [actions/setup-python](https://github.com/actions/setup-python) - Python setup
- [Platane/snk](https://github.com/Platane/snk) - Snake animation
- [crazy-max/ghaction-github-pages](https://github.com/crazy-max/ghaction-github-pages) - Pages deployment

### Community
- [Awesome GitHub Actions](https://github.com/sdras/awesome-actions)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)

---

<div align="center">

### 🌌 Quantum Automation Status

![Automation](https://img.shields.io/badge/🤖_Automation-Active-8B5CF6?style=for-the-badge&logo=github-actions&logoColor=white)
![Workflows](https://img.shields.io/badge/⚛️_Workflows-4_Active-A78BFA?style=for-the-badge&logo=clockify&logoColor=white)
![Status](https://img.shields.io/badge/🛸_Status-Self_Evolving-C084FC?style=for-the-badge&logo=dependabot&logoColor=white)

**⚛️ Your profile is now a self-maintaining quantum system!** 🌌

</div>
