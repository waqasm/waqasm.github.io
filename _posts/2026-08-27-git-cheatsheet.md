---
title: "Git Cheatsheet"
date: 2026-08-27 22:56:00
categories: [CheatSheets]
tags: [Technology, CheatSheets]
description: "A git cheatsheet"
image:
  path: /assets/img/headers/preview.webp
  alt: "Git Cheatsheet"
---


# Git Cheat Sheet

## Setup & Configuration
```bash
# Set author name used in commits
git config --global user.name "Your Name"

# Set email used in commits
git config --global user.email "you@example.com"

# Use main as default branch for new repositories
git config --global init.defaultBranch main

# View all active Git configuration values
git config --list
```

## Create & Clone Repositories
```bash
# Initialize a new repository in current folder
git init

# Clone repository into a folder with repo name
git clone <repository-url>

# Clone repository into a custom folder
git clone <repository-url> <folder-name>
```

## Check Status
```bash
# Detailed status
git status

# Compact status (-s = short format)
git status -s
```

## Stage Changes
```bash
# Stage a specific file
git add <file>

# Stage all changes in current directory
git add .

# Stage all changes including deletions (-A = all)
git add -A
```

## Commit Changes
```bash
# Create commit with message (-m)
git commit -m "Commit message"

# Stage and commit tracked files only (-a)
git commit -am "Commit tracked files"

# Modify last commit message/content
git commit --amend
```

## View History
```bash
# Full commit history
git log

# One commit per line
git log --oneline

# Visual branch graph
# --graph = ASCII graph
# --all = include all branches
git log --graph --oneline --all

# Show commit details
git show <commit-id>
```

## Branching
```bash
# List branches
git branch

# Create a new branch
git branch <branch-name>

# Switch to existing branch
git checkout <branch-name>
# Modern alternative
git switch <branch-name>

# Create and switch in one command (-c = create)
git switch -c <branch-name>

# Delete merged branch (-d = safe delete)
git branch -d <branch-name>
```

## Merge & Rebase
```bash
# Merge branch into current branch
git merge <branch-name>

# Replay commits on top of another branch
git rebase <branch-name>

# Interactive rebase for last 3 commits (-i)
git rebase -i HEAD~3
```

## Remote Repositories
```bash
# View configured remotes
git remote -v

# Add remote named origin
git remote add origin <url>

# Download latest changes without merging
git fetch

# Fetch and merge changes from main
git pull origin main

# Push local commits to remote branch
git push origin main
```

## Stashing
```bash
# Save uncommitted changes temporarily
git stash

# List stashes
git stash list

# Apply and remove latest stash
git stash pop

# Apply stash but keep it in list
git stash apply
```

## Undo Changes
```bash
# Restore file to last committed state
git restore <file>

# Unstage file but keep local changes
# --staged affects staging area only
git restore --staged <file>

# Move HEAD back one commit, keep changes staged
# --soft preserves files and staging area
git reset --soft HEAD~1

# Remove commit and local changes permanently
# --hard changes working directory too
git reset --hard HEAD~1

# Create a new commit that reverses a commit
git revert <commit-id>
```

## Tags
```bash
# List tags
git tag

# Create tag
git tag v1.0.0

# Push a specific tag
git push origin v1.0.0

# Push all local tags
# --tags sends every tag
ngit push --tags
```

## Diff
```bash
# Unstaged changes
git diff

# Staged changes only
# --staged compares staged changes against last commit
git diff --staged

# Compare two branches
git diff main feature-branch
```

## Cleanup
```bash
# Remove untracked files and directories
# -f = force, -d = include directories
git clean -fd

# Repository housekeeping and optimization
git gc
```

## Useful Aliases
```bash
# git st
git config --global alias.st status

# git co
git config --global alias.co checkout

# git br
git config --global alias.br branch

# Pretty log view
git config --global alias.lg "log --oneline --graph --decorate --all"
```

## Common Workflows

### New Feature
```bash
git switch -c feature/my-feature
git add .
git commit -m "Add feature"
# -u sets upstream tracking branch
git push -u origin feature/my-feature
```

### Sync With Main
```bash
git switch main
git pull origin main
git switch feature/my-feature
git rebase main
```

### Resolve Merge Conflict
```bash
# Edit conflicting files
git add .
git commit
```
