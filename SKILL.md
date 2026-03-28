---
name: awesome-skills-cloner
description: Clones GitHub skill repositories into the current workspace. Use this skill when users want to clone skill repos from GitHub, download agent skill collections, set up a local skills directory, or say "clone skills repo", "download skills from github", "get these skill repos", "pull skills locally". Essential for building a curated skills workspace.
---

# Awesome Skills Cloner

Clone GitHub skill repositories into the current workspace for local access and customization.

## When to Use This Skill

Use this skill when the user:

- Wants to clone skill repositories from GitHub
- Says "clone this skill repo" with a GitHub URL
- Wants to set up a local skills workspace with multiple repos
- References a list of skill repos to pull down
- Wants to update/refresh already cloned repos

## Known Skill Repositories

Here are well-known skill repos in the ecosystem:

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

## How to Clone Skills

### Step 1: Identify What to Clone

Parse the user's request to determine:
- A specific repo URL (e.g., `https://github.com/anthropics/skills.git`)
- A repo shorthand (e.g., `anthropics/skills`)
- Multiple repos from a list
- "All" repos from a known list

### Step 2: Clone Single Repo

```bash
# Clone to current workspace with repo name as directory
git clone https://github.com/<owner>/<repo>.git

# Or clone to a specific subdirectory
git clone https://github.com/<owner>/<repo>.git <custom-name>
```

### Step 3: Clone Multiple Repos

For batch cloning, use a loop:

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

### Step 4: Verify Clones

After cloning:
```bash
# List cloned directories
ls -la

# Check each has expected structure (SKILL.md or skills/ dir)
for dir in */; do
  echo "=== $dir ==="
  ls "$dir" | head -5
done
```

## Handling Already Cloned Repos

If a repo already exists locally:

```bash
if [ -d "<repo-name>" ]; then
  echo "Already cloned. Pulling latest..."
  cd <repo-name> && git pull
else
  git clone https://github.com/<owner>/<repo>.git
fi
```

Always ask the user: "This repo already exists. Pull latest changes, skip, or re-clone?"

## Cloning from Awesome Lists

If the user points to an "awesome" list or collection:

1. Read the README to find repo links
2. Extract GitHub URLs (pattern: `github.com/owner/repo`)
3. Clone each found repo
4. Report what was cloned

## After Cloning

Remind the user:
- Cloned repos are independent copies — use `git pull` to update
- Skills within repos may need to be registered/configured
- Check each repo's README for specific setup instructions

## Quick Reference

| Action | Command |
|--------|---------|
| Clone single repo | `git clone https://github.com/owner/repo.git` |
| Clone to specific dir | `git clone https://github.com/owner/repo.git my-dir` |
| Pull updates | `cd repo && git pull` |
| Clone multiple | Loop with `git clone` in background (`&`) |
