# 🚀 Profile Setup Guide

This document explains how this GitHub profile is structured and how to maintain it.

---

## 📁 Repository Structure

```
technosaran/
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md            # Bug report template
│   │   ├── feature_request.md       # Feature request template
│   │   ├── question.md              # Question template
│   │   └── config.yml               # Template configuration
│   ├── workflows/
│   │   ├── update-readme.yml        # Daily timestamp updates
│   │   ├── profile-stats.yml        # Stats refresh every 6 hours
│   │   ├── advanced-automation.yml  # Comprehensive automation
│   │   └── snake.yml                # Snake animation generator
│   ├── CODEOWNERS                   # Code ownership configuration
│   ├── dependabot.yml               # Automated dependency updates
│   ├── FUNDING.yml                  # Sponsorship options
│   └── PULL_REQUEST_TEMPLATE.md     # PR template
├── README.md                        # Main profile page
├── PROJECTS.md                      # Detailed project descriptions
├── SKILLS.md                        # Technical skills breakdown
├── QUICK_LINKS.md                   # Fast navigation hub
├── CONTRIBUTING.md                  # Contribution guidelines
├── CODE_OF_CONDUCT.md              # Community standards
├── SECURITY.md                      # Security policy
├── SETUP.md                         # This file
├── BADGES_REFERENCE.md             # Badge customization
├── VISUAL_GUIDE.md                  # Visual elements guide
├── ENHANCEMENTS_SUMMARY.md         # All improvements summary
├── AUTOMATION_GUIDE.md             # Automation documentation
├── LICENSE                          # MIT License
└── .gitignore                       # Git ignore rules
```

---

## 🔧 GitHub Actions Workflows

### 1. Update README Timestamp
**File:** `.github/workflows/update-readme.yml`  
**Frequency:** Daily at 00:00 UTC  
**Purpose:** Keeps the "Last update" timestamp current

### 2. Profile Stats Update
**File:** `.github/workflows/profile-stats.yml`  
**Frequency:** Every 6 hours  
**Purpose:** Refreshes profile statistics

### 3. Advanced Profile Automation
**File:** `.github/workflows/advanced-automation.yml`  
**Frequency:** Daily + Every 6 hours + On push  
**Purpose:** Comprehensive profile automation with stats

### 4. Snake Contribution Animation
**File:** `.github/workflows/snake.yml`  
**Frequency:** Daily at midnight + On push  
**Purpose:** Generates animated snake eating your contributions  
**Output:** SVGs in the `output` branch

### Manual Trigger
All workflows can be triggered manually:
1. Go to Actions tab
2. Select the workflow
3. Click "Run workflow"

---

## 🎨 Customization Guide

### Update Contact Information

Edit these placeholders in `README.md`:
- LinkedIn URL: `https://www.linkedin.com/in/your-linkedin`
- Email: `your.email@example.com`
- Portfolio: `https://technosaran.github.io/portfolio`

### Add Project Links

Update `README.md` and `PROJECTS.md` with actual repository links:
```markdown
[Smart Crop Doctor](https://github.com/technosaran/smart-crop-doctor)
```

### Customize Badges

Current badges use:
- shields.io for static badges
- github-readme-stats for dynamic stats
- capsule-render for headers/footers

Modify colors and themes in the badge URLs.

---

## 📊 Dynamic Stats Services

### GitHub Readme Stats
```markdown
![Stats](https://github-readme-stats.vercel.app/api?username=technosaran&theme=tokyonight)
```

**Themes:** tokyonight, radical, merko, gruvbox, dark, default

### GitHub Streak Stats
```markdown
![Streak](https://streak-stats.demolab.com/?user=technosaran&theme=tokyonight)
```

### Profile Views Counter
```markdown
![Views](https://komarev.com/ghpvc/?username=technosaran&color=00eaff)
```

---

## 🔄 Maintenance Tasks

### Weekly
- Review and update project statuses
- Check for broken links
- Update roadmap items

### Monthly
- Add new projects to PROJECTS.md
- Update skills in SKILLS.md
- Review and respond to issues

### As Needed
- Update contact information
- Add new badges
- Refresh screenshots
- Update tech stack

---

## 🎯 Best Practices

### Commit Messages
Use conventional commits:
- `feat:` New features
- `fix:` Bug fixes
- `docs:` Documentation updates
- `chore:` Maintenance tasks
- `style:` Formatting changes

### README Updates
- Keep content concise
- Use visual elements (badges, stats)
- Update regularly
- Test all links

### Project Documentation
- Add screenshots to project repos
- Write clear setup instructions
- Include demo links when available
- Keep READMEs updated

---

## 🚀 Advanced Features

### Add Custom Badges
Visit [shields.io](https://shields.io) to create custom badges:
```markdown
![Custom](https://img.shields.io/badge/Your-Badge-color)
```

### Add GitHub Trophies
```markdown
![Trophy](https://github-profile-trophy.vercel.app/?username=technosaran&theme=tokyonight)
```

### Add Activity Graph
```markdown
![Activity](https://github-readme-activity-graph.vercel.app/graph?username=technosaran&theme=tokyo-night)
```

---

## 🔗 Useful Resources

- [GitHub Profile README Guide](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile)
- [Shields.io Badge Generator](https://shields.io)
- [GitHub Readme Stats](https://github.com/anuraghazra/github-readme-stats)
- [Awesome GitHub Profile README](https://github.com/abhisheknaiidu/awesome-github-profile-readme)

---

## 📧 Support

Questions about this setup?
- Open an issue in this repo
- Email: your.email@example.com
- LinkedIn: [Connect with me](https://www.linkedin.com/in/your-linkedin)

---

**Keep building. Keep improving.** 🚀
