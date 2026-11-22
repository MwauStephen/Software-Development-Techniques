# Agentic Software Engineering Playbook

**15 Reusable AI Prompts for the Complete Software Development Lifecycle**

From idea and PRD to design, implementation, verification, security, clean Git history, and reusable agent skills.

# Source fidelity and how to use this guide

The uploaded screenshots clearly show the ordered stage names and the author’s central philosophy. However, the prompt text inside the 15-card overview is too small to read accurately. The prompts below are ORIGINAL RECONSTRUCTIONS for practical reuse, not verbatim transcription from the graphic. Stage titles are retained from the visible overview; capitalization is normalized.

Operating principle: Human defines the outcome → Agent executes a bounded workflow → Tests verify outcomes → Human reviews and approves the result.

Before using a prompt, replace \[BRACKETED PLACEHOLDERS\], provide relevant files/context, and agree on the approval boundary. Each stage should produce a reviewable artifact before the next stage begins.

# Workflow at a glance

- 01 Write a Full PRD — Requirements

- 02 Create Your CLAUDE.md — Project context

- 03 Ultra Plan Mode — Planning

- 04 Spec-Driven Development — Specifications

- 05 Full UI/UX Design Brief — Design

- 06 Implementation Plan — Engineering plan

- 07 Wire Up an MCP Server — Tool integration

- 08 Connect Your Database — Data integration

- 09 Find Security Gaps — Security review

- 10 Debug an Error Fast — Debugging

- 11 E2E Test Your Application — End-to-end verification

- 12 Clean Up Dead Code — Code quality

- 13 Write Clean Git Commits — Version control

- 14 Hooks and Guardrails — Policy and automation

- 15 Turn a Task into Skill — Reusable capability

# The 15 reusable prompts

## 01 Write a Full PRD

**Purpose:** Requirements

**COPY-READY PROMPT**

> Act as a senior product manager and software architect. Help me create a comprehensive Product Requirements Document for \[PROJECT / FEATURE\]. Context: \[BUSINESS PROBLEM\], users: \[PERSONAS\], goals: \[OUTCOMES\], stack: \[STACK\], constraints: \[CONSTRAINTS\]. Include the problem statement, business objectives, user personas, user journeys, MVP vs later scope, functional and non-functional requirements, acceptance criteria, business rules, assumptions, dependencies, risks, measurable success metrics, and open decisions. Distinguish confirmed requirements from assumptions. Ask only essential unanswered questions; otherwise proceed with clearly labeled assumptions. Do not write implementation code.

**Exit artifact:** Approved PRD and explicit MVP scope.

## 02 Create Your CLAUDE.md

**Purpose:** Project context

**COPY-READY PROMPT**

> Examine the existing project structure and documents before proposing changes. Draft or update a concise CLAUDE.md (or equivalent agent-instruction file for my coding tool) for \[PROJECT\]. Capture product purpose, tech stack, repository layout, setup commands, architectural boundaries, naming conventions, security and multitenancy rules, test commands, coding standards, known pitfalls, and definition of done. Base statements on actual repository evidence; mark unknowns for confirmation. Do not overwrite existing instructions or invent commands. Show the proposed file and obtain my review before changing it.

**Exit artifact:** Reviewable project-instructions file grounded in the repository.

## 03 Ultra Plan Mode

**Purpose:** Planning

**COPY-READY PROMPT**

> Act as a lead engineer in planning-only mode. For \[FEATURE\], read the PRD, existing architecture, related code, and tests. Identify requirements, affected modules and files, data flow, dependencies, security implications, edge cases, and alternatives. Divide work into small independently testable slices with dependencies and acceptance criteria. Provide a risk register, test strategy, rollback strategy, and exact verification commands where known. Surface uncertainties and decisions needing approval. Do not modify code or run destructive commands. Wait for plan approval.

**Exit artifact:** Approved plan broken into testable slices.

## 04 Spec-Driven Development

**Purpose:** Specifications

**COPY-READY PROMPT**

> Convert the approved requirements for \[FEATURE / SLICE\] into an implementation-ready technical specification. Define API contracts, request/response examples, data models and migrations, authorization rules, validation, failure states, idempotency and concurrency handling where relevant, UI states, integration boundaries, and measurable acceptance tests. Include a requirement-to-test traceability table. Avoid undocumented assumptions; flag decisions. Do not implement until the spec is reviewed.

**Exit artifact:** Technical specification with verifiable acceptance tests.

## 05 Full UI/UX Design Brief

**Purpose:** Design

**COPY-READY PROMPT**

> Act as a product designer and frontend architect. Using the approved PRD and technical spec for \[FEATURE\], create a UI/UX brief covering user goals, information architecture, key flows, screens, component states (loading, empty, success, error), responsive behavior, accessibility, forms and validation messages, design system usage, and edge cases. Include wireframe descriptions and implementation notes for \[FRONTEND STACK\]. Highlight assumptions and do not invent brand guidelines. Produce a design review checklist before coding.

**Exit artifact:** Design brief and user-flow checklist.

## 06 Implementation Plan

**Purpose:** Engineering plan

**COPY-READY PROMPT**

> Using the approved PRD, technical spec, and UI/UX brief, build a file-by-file implementation plan for \[SLICE\]. Detail backend and frontend responsibilities, endpoints, services, database changes, validation, authorization, tests, documentation, migration/rollback, and order of execution. Minimize unnecessary refactors. Specify exactly how each acceptance criterion will be verified. Provide estimated complexity and blocking questions, then stop for human approval before editing files.

**Exit artifact:** Scoped, reviewable file-level implementation plan.

## 07 Wire Up an MCP Server

**Purpose:** Tool integration

**COPY-READY PROMPT**

> Evaluate whether an MCP server is necessary for \[USE CASE\]. Explain required capabilities, candidate server, permissions, data exposure, trust boundaries, and alternatives. Propose least-privilege configuration for \[CODING AGENT / ENVIRONMENT\], with secret storage via environment variables or a secret manager. Include installation instructions based on verified official documentation, connection tests, permission prompts, and a rollback procedure. Never print credentials, grant broad access without justification, or change production systems without explicit approval.

**Exit artifact:** Auditable MCP integration proposal and connection checks.

## 08 Connect Your Database

**Purpose:** Data integration

**COPY-READY PROMPT**

> Review the data requirements for \[FEATURE\] and the current database schema in \[PROJECT\]. Propose tables, relationships, indexes, constraints, migrations, transactions, and access-control boundaries. Describe how to connect the application through configuration without exposing secrets. Plan test data and local/staging validation, query performance checks, safe migration and rollback, and backups for any risky change. Do not connect to production or run destructive migrations without explicit permission.

**Exit artifact:** Schema/migration proposal and verified nonproduction integration.

## 09 Find Security Gaps

**Purpose:** Security review

**COPY-READY PROMPT**

> Act as an application security reviewer. Inspect the code diff and adjacent flows for \[SLICE\]. Analyze authentication, authorization and IDOR, tenant isolation, input validation, injection, XSS/CSRF, secret handling, file uploads, logging of sensitive data, dependencies, rate limiting, and business-logic abuse. Rank findings by severity, likelihood, evidence, and impact. For each finding give the affected file, a safe remediation, and a regression test. Distinguish verified flaws from hypotheses. Do not claim the code is secure merely because scans pass.

**Exit artifact:** Prioritized security findings and remediation tests.

## 10 Debug an Error Fast

**Purpose:** Debugging

**COPY-READY PROMPT**

> Investigate this issue: \[ERROR / EXPECTED VS ACTUAL BEHAVIOR\]. Given \[REPRO STEPS\], \[LOGS\], and \[ENVIRONMENT\], first reproduce it safely. Identify the smallest plausible root cause using code and evidence; list competing hypotheses if uncertain. Propose the minimal fix, add a regression test, and run targeted checks. Explain the cause, modified files, test results, and remaining uncertainty. Avoid speculative broad refactoring and do not suppress errors to make tests green.

**Exit artifact:** Evidence-based root cause, minimal fix, regression test.

## 11 E2E Test Your Application

**Purpose:** End-to-end verification

**COPY-READY PROMPT**

> Design and, if permitted, execute end-to-end tests for \[FEATURE\] against a safe test environment. Cover the primary happy path, authorization and tenant boundaries, invalid inputs, error handling, repeated submissions, browser/mobile states if applicable, and integration failures. Prefer reliable fixtures and deterministic tests. Report each scenario as pass, fail, or not run, with evidence, exact commands, failing traces, and follow-up actions. Never claim a test was executed unless it actually ran.

**Exit artifact:** E2E test matrix and truthful execution report.

## 12 Clean Up Dead Code

**Purpose:** Code quality

**COPY-READY PROMPT**

> Review the diff for \[SLICE\] and identify unused imports, dead code, duplication, unclear naming, overly complex logic, debug statements, missing types, and documentation drift. Preserve public contracts, existing behaviors, and project conventions. Suggest only necessary cleanup, preferably as a separate small patch. Run appropriate linters and tests after changes. Report what changed, why it is safe, and which checks were not run.

**Exit artifact:** Small maintainability improvements with regression checks.

## 13 Write Clean Git Commits

**Purpose:** Version control

**COPY-READY PROMPT**

> Inspect the working tree and diff for \[SLICE\]. Group actual changes into logically independent, reviewable Git commits. For each proposed commit, provide a conventional-commit subject, a meaningful body summarizing why and what changed, and a precise file list. Flag unrelated changes, generated files, secrets, and untracked artifacts. Do not stage, commit, amend, push, or force-push anything. Present the proposed sequence for my approval; I will make the commits manually.

**Exit artifact:** Human-approved conventional commit plan, no automatic Git actions.

## 14 Hooks and Guardrails

**Purpose:** Policy and automation

**COPY-READY PROMPT**

> Propose safeguards for our agentic development workflow in \[PROJECT\]. Identify safe pre-commit/pre-push checks, formatting and lint hooks, automated unit/integration tests, secret scanning, migration safety checks, protected branches, tool permission limits, prohibited operations, and required human approval gates. Separate checks that can run automatically from actions that must remain manual. Explain false positives, bypass procedures with accountability, and how to test each guardrail. Do not install or activate hooks without review.

**Exit artifact:** Documented guardrails and approval boundaries.

## 15 Turn a Task into Skill

**Purpose:** Reusable capability

**COPY-READY PROMPT**

> Convert this repeated workflow into a reusable agent skill: \[WORKFLOW\]. Define its trigger, inputs, expected context, numbered procedure, tools/permissions, safety constraints, output format, evidence requirements, failure handling, and clear definition of done. Make it portable across projects by using placeholders and project-specific configuration. Include a worked example and a validation checklist. The skill must not auto-commit, push, deploy, delete data, or bypass approval gates. Produce a reviewable skill document before installation.

**Exit artifact:** Reusable skill specification and validation checklist.

# Standard stage completion checklist

- The input requirement and approved scope are explicitly identified.

- The agent explains which files or evidence it actually inspected.

- Changes remain within the agreed slice; unrelated code is left alone.

- Relevant automated checks are run, with pass/fail/not-run recorded truthfully.

- Security, authorization, and data integrity concerns are evaluated when applicable.

- The diff, risks, and unresolved decisions are presented for human review.

- No automatic commit, push, deployment, or destructive operation occurs.

# Suggested project-specific invocation

“Follow the Agentic Software Engineering Playbook for \[PROJECT\]. We are at stage \[NUMBER\] for slice \[NAME\]. Read the approved PRD, current spec, architecture, and repository instructions. Work only within this slice. Deliver the stated exit artifact and verification evidence. Do not proceed to the next stage until I approve.”

# Source references

User-supplied screenshots from a LinkedIn post by Arif Alam discussing a “15 Vibe Coding Prompts” Claude Code cheat sheet. The accompanying post provides the lifecycle framing, stresses testing and verification, and recommends turning repeated actions into reusable skills. No external source was used to reconstruct the prompts.
