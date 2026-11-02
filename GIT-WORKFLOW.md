# Universal Daily Git Workflow

A disciplined, reproducible, and recruiter-friendly daily Git workflow for managing all 27 repositories across the 7 engineering pillars.

---

## Workflow Principles

1. **Isolation:** Never commit directly on an experimental state without verifying tests.
2. **Security:** Always verify that no `.env`, credentials, or secret keys are staged before committing.
3. **Traceability:** Use Conventional Commits (`feat:`, `fix:`, `docs:`, `test:`, `refactor:`, `chore:`).
4. **Documentation Sync:** Whenever code is implemented or tests pass, update the corresponding `README.md` and `PROGRESS.md`.

---

## Daily 7-Step Command Protocol

### Step 1: Navigate to the Target Repository & Project Directory
Select the appropriate level repository and navigate into the target project folder:

```bash
# Example: Navigating to Backend Level 1, Project 02
cd d:/my\ personal-workspace/github-ecosystem/backend-beginner-projects/02-restful-api-task-manager

# Or Automation Level 1, Project 02:
# cd d:/my\ personal-workspace/github-ecosystem/automation-beginner-projects/02-file-processing-data-pipeline

# Or AI Agent Level 1, Project 02:
# cd d:/my\ personal-workspace/github-ecosystem/ai-agents-beginner-projects/02-structured-data-extractor-agent
```

### Step 2: Ensure Clean Main & Create Feature Branch
```bash
# Pull latest changes from remote
git checkout main
git pull origin main

# Create and switch to a descriptive feature branch
git checkout -b feat/project-02-implementation
```

### Step 3: Implement Code, Tests & Documentation
Work inside the established project directory structure:
- `src/`: Production application source code.
- `tests/`: Automated test cases and validation assertions.
- `README.md`: Technical project documentation, architecture details, and reproduction steps.

### Step 4: Run Tests & Verify Clean Working Tree
Before staging any changes, run the automated test suite and check git status:

```bash
# Node.js project:
npm test

# Python project:
python -m unittest discover tests/
# or: pytest tests/

# Verify that no .env, credentials, or build artifacts are untracked
git status
```

### Step 5: Update Progress Tracking
Update the repository progress tracker (e.g., `PROGRESS.md`, `README.md`, or `COMPLETE-PROJECT-CATALOG.md`):
- Change project status from `Available` to `In Progress` or `Completed`.
- Record test execution results and completion timestamp.

### Step 6: Atomic Conventional Commit
Stage only the relevant files (never `git add .` indiscriminately if sensitive files might exist):

```bash
# Stage application code, tests, and documentation
git add src/ tests/ README.md

# Stage updated progress tracker in root
git add ../PROGRESS.md

# Commit with a structured Conventional Commit message
git commit -m "feat(p02): implement REST task manager endpoints with JWT auth and test suite"
```

### Step 7: Merge to Main & Push to GitHub
```bash
# Switch to main branch
git checkout main

# Merge feature branch
git merge feat/project-02-implementation

# Push verified changes to GitHub
git push origin main

# Clean up local feature branch
git branch -d feat/project-02-implementation
```

---

## Conventional Commit Reference

| Prefix | Usage | Example |
| :--- | :--- | :--- |
| `feat` | New project implementation or feature | `feat(p02): implement JWT authentication middleware` |
| `fix` | Bug fix or error resolution | `fix(p01): resolve connection pool timeout in database client` |
| `test` | Adding or updating test cases | `test(p03): add end-to-end integration tests for webhooks` |
| `docs` | Documentation, README, or roadmap update | `docs(hub): update progress metrics across level 1 repos` |
| `refactor` | Code restructuring without feature changes | `refactor(p04): extract reusable validation schema helper` |
| `chore` | Dependency updates, tooling, or config | `chore(deps): update fastify to v4.26.0` |

---

## Security & Clean Hygiene Checklist

- [ ] `.env` is listed in `.gitignore` and has NEVER been added to git history.
- [ ] Only sanitized `.env.example` with dummy placeholder values is committed.
- [ ] No hardcoded passwords, tokens, or private keys exist in source code.
- [ ] Git remote URL uses clean HTTPS format (`https://github.com/EmaanHumayun/<repo>.git`) with zero embedded tokens.
- [ ] All automated tests pass with 100% success rate before merging to `main`.
