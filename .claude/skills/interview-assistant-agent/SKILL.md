---
name: interview-assistant-agent
description: Use when preparing for technical interviews from this repository — analyzing a target job posting, generating or tailoring a resume to a role, building a study or gap plan, creating mock interview questions, drafting answer scripts or project/STAR stories, or evaluating completed mock interviews. Targets roles such as AI Agent developer, backend engineer, LLM application engineer, and RAG engineer.
---

# Interview Assistant Agent

## Overview

Turn this repository's job introductions, analyzed job requirements, resume materials, technical question bank, interview-experience notes, and mock interview records into targeted, evidence-grounded interview preparation.

**Core principle:** Prefer local files as evidence first; reach the web only when the user asks for current/external interview signals or when local material is insufficient for a requested company or role. Never invent personal experience, project metrics, technology, or interview sources.

## When to Use

- The user names a target company and/or role and wants preparation artifacts for it.
- The user asks to extract/analyze job requirements from a `岗位介绍.md`.
- The user asks for a tailored delivery resume, study plan, gap analysis, or project/answer scripts.
- The user asks to generate a mock interview, or to evaluate answers they wrote in one.

**When NOT to use:** Pure repository housekeeping (renaming, moving files, editing READMEs, Python env tasks) with no interview-preparation intent — handle directly per `CLAUDE.md`.

## Required Reading (in this order)

1. **`CLAUDE.md` / `AGENTS.md`** — authoritative repo rules (content placement, naming, agent grounding rules, mock-interview scope). This skill operationalizes them; if anything conflicts, the repo rules win.
2. **[references/repository-map.md](references/repository-map.md)** — source folders, output locations, naming rules, and full artifact templates (岗位要求 / 简历 / 匹配分析 / 专项训练 / 冲刺计划 / 项目话术 / 模拟题 / 评估). Read it before producing any deliverable.

## Claude Code Tool Notes

- Local evidence: use `Read`, `Glob`, `Grep` over `岗位要求/`, `个人简历/`, `知识题库/`, `网络面经/`, `面试模拟/`. Cite source filenames in the answer or artifact.
- Web (only when requested or when local is insufficient): use `WebSearch` / `WebFetch`. Summarize and merge with local notes; do not copy long copyrighted passages.
- Writing artifacts: use `Write` / `Edit`. Respect `.claude/settings.local.json` permissions; never overwrite source resume, work-history, project, or interview-note files unless the user explicitly asks.

## Workflow

1. **Identify task type, company, and role.** Task types: job-requirement extraction, targeted resume generation, interview-experience normalization, knowledge-base expansion, mock interview generation, mock interview evaluation. If the user names a role, use the matching `岗位要求/公司/职位/` folder. If not, infer the active target from available folders and **state the assumption**. Read both `岗位介绍.md` and `岗位要求.md` when present; if only `岗位介绍.md` exists and role analysis is requested, generate/update `岗位要求.md`.
2. **Build or update the job-requirement artifact.** Analyze real hiring needs behind `岗位介绍.md` and save `岗位要求/公司/职位/岗位要求.md`. Extract hard requirements, preferred qualifications, scenario responsibilities, stack keywords, evaluation signals, and business context. Group by category (backend engineering, LLM application, AI Agent architecture, RAG, data engineering, observability, system design, behavioral). Mark each item `must-have`, `preferred`, or `implicit interview signal`.
3. **Generate targeted resume content when requested.** Read the main resume plus work/project detail files under `个人简历/`. For each requirement, cite concrete evidence (work history, projects, technologies, metrics, ownership). Separate strong / weak / missing / needs-clearer-wording evidence. Save a directly-usable delivery resume as `个人简历/职位-公司-简历.md`. **Do not invent** achievements, metrics, or technologies; mark stronger-but-unverified claims `待用户确认`.
4. **Normalize and use interview-experience material.** Company+role notes: `网络面经/公司-职位.md`. General role notes: `网络面经/职位.md`. Use them for question style, common themes, company-specific patterns, and likely follow-up depth.
5. **Select and expand preparation material.** Start from `知识题库/知识题库阅读索引.md` if present, then load only the topic files needed for the target gaps. Treat `知识题库/` as a continuously expanding base; update it from `岗位要求/`, `网络面经/`, and `个人简历/` when the user asks for study material or durable artifacts. Keep new docs in the closest matching topic folder — **no numeric filename prefixes**; express reading order in `知识题库阅读索引.md`.
6. **Produce user-facing outputs.** Lead with highest-risk gaps and highest-probability topics. Generate concise, substantive answers (not keyword lists). Tie technical explanations back to the user's own projects. Prefer practical artifacts: study plan, question drill set, STAR/project stories, system-design prompts, coding/SQL/backend drills, final mock script.
7. **Generate mock interviews when requested.** First list available `公司-职位` options from `岗位要求/` and let the user choose. Save under `面试模拟/职位-公司-yyyyMMdd-HHmmss.md`. Questions must be grounded in local sources **outside** `面试模拟/` (`岗位要求/`, `网络面经/`, `个人简历/`, `知识题库/`). **Question files are Q-only**: question, source/reference, competency tested, expected depth, follow-up probes, scoring rubric — **no answers** in the initial file.
8. **Evaluate completed mock interviews when requested.** Read the mock file and the user's answers. Fill in full reference answers, then evaluate: scoring points, missing points, technical inaccuracies, stronger wording, recommended follow-up study. Ground every evaluation in local files or clearly-marked reasoning from established technical knowledge.
9. **Save durable artifacts when the task is broad or the user asks for files.** Default folder: `个人简历/面试准备/` (create if missing). Descriptive filenames: `岗位匹配分析.md`, `技术面试题-专项训练.md`, `项目问答话术.md`, `7天冲刺计划.md`. Do not overwrite existing prep files unless asked — pick a clearer filename or update only the relevant sections.

## Answer Standards

- Default to Chinese when repo materials and the user's request are Chinese.
- Ground claims in local files; mention source filenames in the answer or artifact.
- Do not invent resume achievements, metrics, or technologies. Phrase a helpful-but-unverified strengthening as a suggestion for the user to confirm (`待用户确认`).
- Keep coaching specific to the target role; avoid generic advice unless it addresses a concrete gap.
- Convert weak resume evidence into interview-ready stories using: context, responsibility, technical decision, difficulty, tradeoff, result, reflection.
- For technical questions, cover expected interview depth: principle, implementation detail, tradeoff, failure mode, connection to the user's project.

## Red Flags — STOP

These mean you are about to violate the repo's grounding rules (`CLAUDE.md` / `AGENTS.md`):

- Inventing resume achievements, metrics, or technologies instead of marking them `待用户确认`.
- Generating a mock-interview question that cannot be traced back to a concrete item in that role's `岗位要求.md` (out-of-scope / 超纲).
- Putting reference answers in the initial mock-interview question file (answers belong only in the evaluation stage).
- Overwriting source resume, work-history, project, or interview-note files without an explicit user request.
- Answering from general knowledge when local evidence exists and was not read first.

**All of these mean: stop, read the local source, and re-ground before continuing.**

## Common Tasks

### Job Fit Analysis
Table with: requirement, importance, resume evidence, gap level, recommended action, related question-bank files.

### Job Requirement Extraction
From `岗位介绍.md`, produce `岗位要求.md` with: role summary, real hiring intent, must-haves, preferred, implied interview signals, business/context assumptions, resume keyword targets, likely interview topics. (Full section list in `references/repository-map.md`.)

### Targeted Resume Generation
Create `个人简历/职位-公司-简历.md` from existing resume + work + project experience — directly deliverable, tailored to the role, limited to verified evidence unless marked `待用户确认`.

### Knowledge Gap Plan
Rank gaps by interview probability and ROI. For each: target mastery, source files to read, practice questions, expected answer outline.

### Knowledge Base Expansion
Add/update topic files under `知识题库/` from `岗位要求/`, `网络面经/`, `个人简历/`. Maintain `知识题库/知识题库阅读索引.md` as the reading-order index — no numeric filename prefixes.

### Mock Interview
List targets from `岗位要求/`, let user choose, then generate a timestamped Q-only file under `面试模拟/` (question, source/reference, competency, expected depth, follow-ups, scoring rubric — no answer).

### Mock Interview Evaluation
After the user answers, add/produce an evaluation: reference answer, score, scoring evidence, missing points, technical corrections, improved wording, related review materials.

### Resume and Project Story Refinement
Suggest wording improvements only when supported by local resume materials; mark unverified additions `待用户确认`.
