---
name: repo-standards-adoption
description: Use when bootstrapping a new GitHub repository from the standards baseline or installing the shared standard into an existing repository.
---

Adopt standards in one of two ways:

1. Future repos:
   - create a reusable template repository from this standards baseline
   - include the shared `AGENTS.md`, `.agents/skills/`, and starter repo metadata
   - keep project-specific commands and paths thin and local

2. Existing repos:
   - install the shared managed files into the repo
   - record which upstream standards repo and ref the repo follows
   - keep local overrides outside the managed paths

Use these repo tools:
- `bash scripts/create_template_repo.sh TARGET_DIR REPO_NAME STANDARDS_REPO`
- `bash scripts/bootstrap_repo.sh TARGET_REPO STANDARDS_REPO`
- `bash scripts/setup_target_repo.sh existing TARGET_REPO STANDARDS_REPO`
- `bash scripts/setup_target_repo.sh template TARGET_DIR REPO_NAME STANDARDS_REPO`

Adoption rules:
- keep the shared baseline generic
- let target repos own their local commands and directory-specific rules
- keep the root `AGENTS.md` short and move detailed behavior into skills
