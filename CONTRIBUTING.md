# Contributing to Likha Innovations

First off, thank you for contributing to our capstone project! This document serves as the **single source of truth** for how we collaborate, write code, and manage our repository. 

Since we are an 8-member team working on a sustainable IoT project for the community, following these guidelines ensures we don't step on each other's toes and keep our codebase thesis-ready.

---

## 📑 Table of Contents

1. [Repository Philosophy](#1-repository-philosophy)
2. [Branch Ruling (The Golden Rule)](#2-branch-ruling-the-golden-rule)
3. [Conventional Commit Convention](#3-conventional-commit-convention)
4. [Conventional Branch Naming](#4-conventional-branch-naming)
5. [Branch Protection Rules](#5-branch-protection-rules-github-settings)
6. [Definition of Done](#6-definition-of-done)
7. [Repository Rules](#7-repository-rules)
8. [Best Practices](#8-best-practices-for-coding-and-collaboration)
9. [Terminology Reference](#9-terminology-reference-glossary)

---

## 1. Repository Philosophy

### Our Mission
As **Likha Innovations**, we are building an IoT-based solution that is **sustainable, accessible, and helpful for the community**. Our code is not just for a grade—it is a prototype that could one day serve local communities, barangays, or non-profits.

### Our Vision
- **Open by Default**: Unless our university explicitly claims ownership, all our code will be open-source (MIT License) to encourage adoption and improvement.
- **Quality over Speed**: We prioritize clean, readable, and well-documented code over rushed, messy commits.
- **Team Accountability**: With 8 members, we must rely on systems (branching, commits, reviews) rather than memory or verbal communication.

### Core Values for our Repository
| Value | How we practice it |
| :--- | :--- |
| **Transparency** | All discussions, decisions, and code changes happen via GitHub Issues and Pull Requests. |
| **Traceability** | Every change is tied to a specific branch, conventional commit, and issue number. |
| **Sustainability** | We write code that is modular, easy to debug, and hardware-agnostic where possible. |

### Who we are
We are an 8-member capstone team from University of Caloocan City working under the guidance of our adviser. Our project focuses on leveraging IoT to solve a real-world community problem.

---

## 2. Branch Ruling (The Golden Rule)

### 🚨 The Absolute Rule
**No one—absolutely no one—is allowed to push directly to the `main` branch.**

> This includes the project lead. Everyone must follow the same process.

### Why?
- `main` represents the **stable, production-ready** version of our code.
- Since we are in the early stages and do not have a `dev` branch yet, `main` is our single source of truth. Breaking it means halting all 8 members.
- It enforces code review, which catches bugs before they reach the hardware.

### The Correct Workflow (Every Single Time)
1.  **Create a branch** from `main`.
2.  **Commit your work** on that branch.
3.  **Push your branch** to GitHub.
4.  **Open a Pull Request** targeting `main`.
5.  **Request a review** from the Project Lead.
6.  **Wait for approval**. If changes are requested, fix them and push again.
7.  **The Project Lead merges** the PR and deletes the branch.

### What happens if you break this rule?
- The commit will be reverted immediately.
- You will be required to fix the `main` branch yourself.
- Repeated violations will be flagged in our team retrospective.

### Exception
None. Unless GitHub is down, there is no reason to bypass this process.

---

## 3. Conventional Commit Convention

We strictly follow the **Conventional Commits** specification to automate changelogs and keep our thesis documentation clean.

### The Format

- **`type`**: What kind of change is this? (see table below).
- **`scope`**: (Optional) Which part of the project? e.g., `hardware`, `api`, `dashboard`, `database`.
- **`subject`**: A short, imperative description (max 50 chars, **lowercase**, no period at the end).

### Allowed Types
| Type | When to use |
| :--- | :--- |
| `feat` | A new feature for the user/community (e.g., new sensor reading). |
| `fix` | A bug fix (e.g., temperature conversion error). |
| `docs` | Changes to documentation (README, comments). |
| `style` | Code style (formatting, semicolons, *no logic changes*). |
| `refactor` | Code changes that neither fix a bug nor add a feature. |
| `perf` | Performance improvements. |
| `test` | Adding or updating tests. |
| `chore` | Updates to build tools, dependencies, or config files. |
| `revert` | Reverting a previous commit. |

### Good Examples
- `feat(sensors): add dht11 humidity read function`
- `fix(mqtt): resolve reconnect timeout issue`
- `docs: update hardware wiring diagram`
- `refactor(backend): simplify data parsing loop`

### Bad Examples (Do NOT do these)
- `fixed stuff`
- `WIP` (Work in Progress)
- `Updated code`
- `FEAT(SENSORS):` (use lowercase for type and scope)

### Commit Body (Optional)
If your commit requires more explanation, add a blank line after the subject and write a paragraph:

---

## 4. Conventional Branch Naming

To keep our repository organized, every branch must follow a strict naming convention.

### The Format
- Use **lowercase** only.
- Separate words with hyphens (`-`). This is called **kebab-case**.
- Keep it short but descriptive (3-5 words max).

### Allowed Types (Prefixes)
| Prefix | When to use |
| :--- | :--- |
| `feature/` | Adding new functionality. |
| `bugfix/` | Fixing a bug. |
| `hotfix/` | Urgent fix for production (use sparingly). |
| `chore/` | Documentation, config changes, or dependencies. |
| `experiment/` | Testing a risky or unproven idea (will be deleted soon). |

### Good Examples
- `feature/temperature-threshold-alert`
- `bugfix/mqtt-payload-parsing`
- `chore/update-readme-setup-guide`
- `feature/database-schema-v2`

### Bad Examples (Do NOT do these)
- `my-branch` (missing type)
- `Feature/Sensor` (wrong case and separator)
- `branch-1` (not descriptive enough)
- `fix/bug` (too vague)

### How to create your branch correctly
Always start from the latest `main`:
```bash
git checkout main
git pull origin main
git checkout -b feature/your-task-name
```

---

## 5. Branch Protection Rules (GitHub Settings)

To enforce our `main` branch rule, we must configure GitHub's branch protection settings. Since we are the repository admins, these settings will force everyone (including us) to follow the rules.

### Required Settings for `main`
As the Project Lead, navigate to **Settings** → **Branches** → **Add rule** for `main` and enable the following:

- ✅ **Require a pull request before merging**
- ✅ **Require approvals**: Set to `1` (the Project Lead will be the sole reviewer).
- ✅ **Dismiss stale pull request approvals** when new commits are pushed.
- ✅ **Require status checks to pass before merging** (Optional for now, but enable if we add GitHub Actions later).
- ✅ **Do not allow bypassing the above settings** (Ensure "Allow specified actors to bypass" is empty).
- ❌ **Do NOT** enable "Require linear history" yet (we can add this later for advanced teams).

### What this means in practice
1. A developer pushes code to `feature/something`.
2. They open a PR to `main`.
3. GitHub **blocks** the merge button until the Project Lead approves it.
4. The Project Lead reviews, approves, and merges.

### Manual Enforcement (Until Settings are Applied)
Since we are just starting, manually enforce these rules:
- No one should click "Merge" except the Project Lead.
- Remind teammates that merging their *own* PR without review is a violation of `02-branch-ruling.md`.

### Adding `dev` in the future
Once we deploy our initial prototype, we will introduce a `dev` branch. At that time:
- `main` will point to production.
- `dev` will point to staging.
- Protection rules will be updated to require PRs into both.

---

## 6. Definition of Done

A task is **only considered "Done"** when it meets ALL the criteria below. This ensures we don't have half-finished features clogging our repository.

## The DoD Checklist
For every Pull Request (PR) or GitHub Issue, verify the following:

### Code Completeness
- [ ] The code fulfills the requirements of the user story or issue.
- [ ] The code is tested on the actual hardware (if an IoT module) or simulated (if software-only).
- [ ] No console errors or runtime exceptions are present.

### Coding Standards
- [ ] The branch name follows `04-conventional-branch-naming.md`.
- [ ] All commit messages follow `03-conventional-commit-convention.md`.
- [ ] The code is readable and includes necessary inline comments for complex logic.
- [ ] No sensitive information (passwords, API keys) is hardcoded (use `.env` instead).

### Process & Review
- [ ] A Pull Request has been opened against `main`.
- [ ] The Project Lead has reviewed and approved the PR.
- [ ] All conversations/discussions in the PR are resolved.

### Post-Merge
- [ ] The PR has been successfully merged into `main`.
- [ ] The source branch has been deleted (both remotely and locally).
- [ ] The corresponding Issue has been closed (e.g., using `Closes #XX`).

### Special Considerations for IoT
- If the change involves hardware (e.g., new sensor code), **physical testing** is mandatory. It is not done until the sensor responds correctly on the breadboard.
- If the change is purely software (e.g., dashboard UI), it is not done until it passes a visual inspection by at least 2 other members.

---

## 7. Repository Rules

This file defines how we manage our organization's repositories beyond just `.github`.

### Required Files for Every Repo
Every new repository **must** contain these 3 files at the bare minimum:
1. **`README.md`**: Explains what the repo does, how to set it up, and links to the main docs.
2. **`.gitignore`**: Appropriate for the language (e.g., Python, Node, C++). Prevents committing build files.
---

## 8. Best Practices for Coding and Collaboration

These are non-negotiable habits that every member must adopt to ensure we don't step on each other's toes—especially since we have 8 people working on one project.

### 1. Write Clean Code (The "Boy Scout" Rule)
- **Leave the code better than you found it.** If you see a typo or a confusing variable name, fix it in a separate commit (or note it in the PR).
- **DRY (Don't Repeat Yourself)**: If you copy-paste code twice, it should be a function.
- **KISS (Keep It Simple, Stupid)**: Prefer simple, readable code over clever, complex code.

### 2. Hardware vs. Software Separation
- Do not hardcode hardware pin numbers directly into the main application logic. Use configuration files or constants at the top of the file.
- **Example (Good)**: `#define TEMP_SENSOR_PIN 4` at the top.
- **Example (Bad)**: `digitalRead(4)` scattered everywhere without context.

### 3. Secrets and Environment Variables
- **NEVER** commit passwords, Wi-Fi SSIDs, or API keys to GitHub.
- Use `.env` files (for Python/Node) or `secrets.h` (for Arduino/ESP32) and add these filenames to `.gitignore`.
- Provide a `env.example` file showing what variables are needed without exposing the real values.

### 4. Keep Git Clean
- **Fetch before you branch**: Always pull the latest `main` before creating a new branch.
- **Small, focused commits**: Commit often, but each commit should represent one logical change. Avoid giant commits with 20 unrelated file changes.
- **Write descriptive PR titles**: The PR title should summarize the whole feature (e.g., "Feat: Add automated irrigation trigger").

### 5. Communication
- If you are stuck on a branch for more than 2 days, **push your work** (even if incomplete) and open a "Draft PR" so others can see your progress.
- Use GitHub Issues to discuss architecture changes before writing code. It saves time.

---

## 9. Terminology Reference (Glossary)

To ensure we are all speaking the same language, here is a glossary of terms we use in our daily workflow and documentation.

### Git & GitHub Terms
| Term | Definition |
| :--- | :--- |
| **Repository (Repo)** | A folder containing all the code and version history for a specific component. |
| **Main** | The default, primary branch. Contains production/stable code. Direct pushes are forbidden. |
| **Branch** | A parallel version of the code. Used to develop features without affecting `main`. |
| **Pull Request (PR)** | A request to merge changes from one branch into another. Requires review. |
| **Merge** | The action of integrating code from one branch into another. |
| **Commit** | A snapshot of your changes with a descriptive message (`feat`, `fix`, etc.). |
| **Push** | Uploading your local commits to GitHub. |
| **Pull** | Downloading the latest changes from GitHub to your local machine. |
| **Issue** | A task, bug report, or feature request tracked on GitHub. |
| **Review** | The process of checking someone else's PR before allowing it to merge. |

### Project/IoT Terms
| Term | Definition |
| :--- | :--- |
| **Hardware** | Physical components (ESP32, sensors, relays, breadboard). |
| **Firmware** | The low-level software written in C/C++ that runs on the ESP32. |
| **Backend** | The server-side application (usually Python/Node) that receives data via MQTT. |
| **MQTT** | A lightweight messaging protocol used for IoT devices to send data to the server. |
| **Dashboard** | A web UI used to visualize sensor data and control actuators. |
| **Actuator** | A device that performs an action (e.g., turning on a pump, sounding a buzzer). |
| **Sensor** | A device that reads environmental data (e.g., temperature, moisture, humidity). |
| **ThingSpeak / Firebase** | Third-party cloud platforms we may use for data storage. |

### Process Terms
| Term | Definition |
| :--- | :--- |
| **DoD (Definition of Done)** | The checklist a task must pass before it is considered complete. |
| **CI/CD** | Automated testing and deployment (we will set this up later). |
| **Local** | Running code on your personal laptop. |
| **Production** | The live, deployed system (currently hosted on our local server or cloud). |

