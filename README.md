# Awesome Skills Cloner

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![OpenCode](https://img.shields.io/badge/OpenCode-Skill-green.svg)](https://opencode.ai)

A skill for OpenCode that clones GitHub skill repositories into the current workspace for local access and customization.

## Overview

This skill enables users to clone skill repositories from GitHub, download agent skill collections, set up a local skills directory, or pull skills locally. It is essential for building a curated skills workspace.

## When to Use This Skill

Use this skill when you want to:

- Clone skill repositories from GitHub
- Download agent skill collections
- Set up a local skills workspace with multiple repos
- Update/refresh already cloned repositories

## Known Skill Repositories

| Repository | Description |
|------------|-------------|
| `anthropics/skills` | Official Anthropic skills collection |
| `anthropics/claude-plugins-official` | Official Claude plugins |
| `anthropics/knowledge-work-plugins` | Knowledge work focused plugins |
| `obra/superpowers` | Superpowers skill collection |
| `affaan-m/everything-claude-code` | Comprehensive Claude Code skills |
| `Jeffallan/claude-skills` | Community Claude skills |
| `msitarzewski/agency-agents` | Agency/agent skills |
| `garrytan/gstack` | Garry Tan's skill stack |
| `MiniMax-AI/skills` | MiniMax AI skills |
| `browser-use/browser-use` | Browser automation skills |
| `mvanhorn/last30days-skill` | Last 30 days skill |
| `OthmanAdi/planning-with-files` | Planning with files skill |

## Usage

### Clone a Single Repository

```bash
# Clone to current workspace with repo name as directory
git clone https://github.com/<owner>/<repo>.git

# Or clone to a specific subdirectory
git clone https://github.com/<owner>/<repo>.git <custom-name>
```

### Clone Multiple Repositories

```bash
# Clone multiple repos in parallel
repos=(
  "anthropics/skills"
  "obra/superpowers"
  "affaan-m/everything-claude-code"
)

for repo in "${repos[@]}"; do
  git clone "https://github.com/${repo}.git" &
done
wait
```

### Update Already Cloned Repos

```bash
if [ -d "<repo-name>" ]; then
  echo "Already cloned. Pulling latest..."
  cd <repo-name> && git pull
else
  git clone https://github.com/<owner>/<repo>.git
fi
```

## Quick Reference

| Action | Command |
|--------|---------|
| Clone single repo | `git clone https://github.com/owner/repo.git` |
| Clone to specific dir | `git clone https://github.com/owner/repo.git my-dir` |
| Pull updates | `cd repo && git pull` |
| Clone multiple | Loop with `git clone` in background (`&`) |

## Notes

- Cloned repositories are independent copies — use `git pull` to update
- Skills within repositories may need to be registered/configured
- Check each repository's README for specific setup instructions
