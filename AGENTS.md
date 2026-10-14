# GitHub Pages Repository — AI Assistant Governance Rules

> **CRITICAL DIRECTIVE FOR ALL AI AGENTS (Claude, Cursor, Copilot, Antigravity, etc.)**
> This repository hosts the production dashboard frontend for Delta Strangle Bot.

---

## 1. Cardinal Governance Rules

### Rule 1: Universal PR-Only Architecture — NEVER Commit Directly to Main
- Direct commits or pushes to the `main` branch are **STRICTLY PROHIBITED**.
- Any command or API call attempting direct branch mutation (e.g., GitHub REST API `PUT /contents/...` committed directly to `main` without an ephemeral branch reference) is a governance violation.
- Every single modification, UI update, bug fix, or deployment MUST be authored on an ephemeral feature branch (`feat/*`, `fix/*`, `chore/*`) and merged exclusively via a Pull Request.

### Rule 2: Ephemeral Branch Workflow
1. Cut an ephemeral branch from `main`: `feat/<description>`.
2. Commit files strictly to the ephemeral branch.
3. Open a Pull Request targeting `main`.
4. Merge via Pull Request.

### Rule 3: Zero-Commit Cloudflare KV Architecture
- Live portfolio state and metrics are served dynamically from Cloudflare Edge KV (`https://delta-strangle-scheduler.ajay14sharma.workers.dev/api/snapshot`).
- Do not commit daily or automated trading snapshot data into this repository.
