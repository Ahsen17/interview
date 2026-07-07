---
name: interview-assistant
description: Build interview preparation from this resume repository. Use when Codex needs to analyze personal resume/work/project experience, update the candidate profile, analyze a target job, use the local technical question bank, and local or web interview experiences to create career-positioning analysis, gap analysis, study plans, mock interview questions, answer scripts, project storytelling, resume improvement suggestions, or technical interview coaching for a target technical role.
---

# Interview Assistant Agent

## Overview

Use this skill to turn the repository's resume materials, job introductions, extracted job requirements, question bank, interview experience notes, and mock interview records into a maintained candidate profile and targeted application/interview preparation. Prefer evidence from local files first, then browse only when the user asks for latest/current external interview experiences or when local material is insufficient for a requested company or role.

## Repository Map

Read [references/repository-map.md](references/repository-map.md) before working in this repository. It defines the expected source folders, output location, and recommended deliverable formats.

## Workflow

1. Identify the task type, target company, and target role.
   - Supported task types include: candidate profile update, job requirement extraction, targeted resume generation, interview experience normalization, knowledge base expansion, mock interview generation, and mock interview evaluation.
   - If the user asks to analyze the current interviewee, personal background, resume profile, technical capability, strengths/weaknesses, or long-term improvement direction, treat it as a candidate profile task even without a target company.
   - If the user names a specific role, use the matching folder under `岗位要求/公司/职位/`.
   - If the user does not name a role, infer the active target from available job requirement folders and state the assumption.
   - Read both `岗位介绍.md` and `岗位要求.md` when present. If only `岗位介绍.md` exists and the task requires role analysis, generate or update `岗位要求.md`.

2. Build or update the candidate profile when requested or when broad preparation needs a baseline.
   - Read `个人简历/README.md`, the main resume, `工作经历.md`, and `项目经历.md` before writing profile conclusions.
   - Treat `个人简历/` as the source of truth. Do not infer employment history, project ownership, metrics, technologies, or business outcomes beyond local evidence.
   - Produce a durable artifact under `个人简历/面试准备/` named `个人画像.md` unless the user asks for another path. Create or update this file as the living baseline for later resume tailoring, gap planning, and mock interviews.
   - Analyze the candidate along: career trajectory, role positioning, domain experience, project ownership, backend engineering ability, LLM/RAG/Agent ability, data/analytics ability, system design ability, engineering delivery, communication/storytelling, interview risk, and priority improvement path.
   - For every strength, gap, and positioning claim, cite the local source file and classify evidence as `强证据`, `弱证据`, `缺失证据`, or `待用户确认`.
   - Separate stable facts from coaching judgments. Use stable facts for resume claims; use coaching judgments for improvement plans and interview strategy.
   - End with concrete next actions: resume wording to strengthen, project stories to prepare, technical topics to repair, and likely interview failure points to drill.

3. Build or update the job requirement artifact.
   - For each `岗位要求/公司/职位/岗位介绍.md`, analyze the real hiring needs behind the text and save `岗位要求/公司/职位/岗位要求.md`.
   - Extract hard requirements, preferred qualifications, scenario responsibilities, stack keywords, evaluation signals, and business context.
   - Group requirements into categories such as backend engineering, LLM application engineering, AI Agent architecture, RAG, data engineering, observability, system design, and behavioral/project communication.
   - Mark each item as `must-have`, `preferred`, or `implicit interview signal`.

4. Generate targeted resume content when requested.
   - Read the main resume plus detailed work and project experience files under `个人简历/`.
   - Read `个人简历/面试准备/个人画像.md` when it exists, and use it as a profile baseline without treating unverified coaching judgments as resume facts.
   - For each requirement, cite concrete evidence from work history, projects, technologies, metrics, and ownership scope.
   - Separate strong evidence, weak evidence, missing evidence, and evidence that exists but needs clearer wording.
   - Generate directly usable delivery resumes under `个人简历/` using the filename format `职位-公司-简历.md`, for example `<目标岗位A>-<目标公司A>-简历.md`.
   - Do not invent resume achievements, metrics, or technologies. Mark stronger but unverified claims as `待用户确认`.

5. Normalize and use interview experience material.
   - For company-and-role-specific notes, expect filenames such as `网络面经/<目标公司A>-<目标岗位A>.md`.
   - For general role notes without a company target, expect filenames such as `网络面经/<目标岗位A>.md`.
   - Use `网络面经/` for question style, common themes, company-specific patterns, and likely follow-up depth.

6. Select and expand preparation material.
   - Use `知识题库/知识题库阅读索引.md` first when available, then load only the topic files needed for the target gaps.
   - Treat `知识题库/` as a continuously expanding integrated knowledge base. Update it from all available `岗位要求/`, `网络面经/`, and `个人简历/` evidence when the user asks for study material or when durable preparation artifacts are needed.
   - Keep new knowledge documents in the closest matching topic folder. Do not use numeric order prefixes in Markdown filenames; express reading order in `知识题库/知识题库阅读索引.md`.
   - When browsing is needed, summarize sources and merge them with local notes without copying long copyrighted passages.

7. Produce user-facing outputs.
   - Start with the highest-risk gaps and highest-probability interview topics.
   - Generate concise but substantive answers, not keyword lists.
   - Tie technical explanations back to the user's own project experience wherever possible.
   - Prefer practical interview artifacts: study plan, question drill set, STAR/project stories, system design prompts, coding/SQL/backend drills, and final mock interview script.

8. Generate mock interviews when requested.
   - Before generating a mock interview, list the available `公司-职位` options from `岗位要求/` and let the user choose the target.
   - Save mock interview question files under `面试模拟/` using `职位-公司-${日期时间戳}.md`.
   - For company-and-role-specific mock interviews, the QA scope must not exceed the selected role's concrete `岗位要求.md`. `网络面经/`, `个人简历/`, and `知识题库/` may support question wording, evidence, and expected depth, but they must not expand the competency scope beyond that role requirement.
   - Mock interview questions must be grounded in existing local sources outside `面试模拟/`, including `岗位要求/`, `网络面经/`, `个人简历/`, and `知识题库/`. Every question must cite the matching requirement from the selected role's `岗位要求.md`; do not invent unsupported or out-of-scope questions.
   - Question files must use a QA-oriented structure but include only Q-side material: question, source/reference, competency tested, expected depth, follow-up probes, and scoring rubric. Do not provide answers in the initial mock interview file.

9. Evaluate completed mock interviews when requested.
   - Read the mock interview file and the user's completed answers.
   - Fill in full reference answers, then evaluate the user's answer with scoring points, missing points, technical inaccuracies, stronger wording, and recommended follow-up study.
   - Ground every evaluation in local source files or clearly marked reasoning from established technical knowledge.

10. Save durable preparation artifacts when the user asks for files or when the task is broad.
   - Default output folder: `个人简历/面试准备/`.
   - Use descriptive Markdown filenames such as `岗位匹配分析.md`, `技术面试题-专项训练.md`, `项目问答话术.md`, and `7天冲刺计划.md`.

## Answer Standards

- Use Chinese by default when the repository materials and user request are Chinese.
- Ground claims in local files whenever possible; mention source filenames in the answer or artifact.
- Do not invent resume achievements, metrics, or technologies. If a stronger achievement would help, phrase it as a suggested clarification for the user to confirm.
- Keep coaching specific to the target role. Avoid generic interview advice unless it directly addresses a gap.
- Convert weak resume evidence into interview-ready stories by using: context, responsibility, technical decision, difficulty, tradeoff, result, and reflection.
- For technical questions, include the expected interview depth: principle, implementation detail, tradeoff, failure mode, and connection to the user's project.

## Common Tasks

### Candidate Profile Update

Create or update `个人简历/面试准备/个人画像.md` from local resume, work experience, and project experience. Use sections: profile summary, career trajectory, core experience map, technical capability matrix, representative project evidence, interview strengths, high-risk gaps, target role fit direction, resume/storytelling improvement points, and 30/60/90-day capability plan. Every conclusion should cite source files and distinguish `强证据`, `弱证据`, `缺失证据`, and `待用户确认`.

### Job Fit Analysis

Create a table with: requirement, importance, resume evidence, gap level, recommended action, and related question-bank files.

### Job Requirement Extraction

Analyze `岗位介绍.md` and create `岗位要求.md` with: role summary, real hiring intent, must-have requirements, preferred qualifications, implied interview signals, business/context assumptions, resume keyword targets, and likely interview topics.

### Targeted Resume Generation

Create `个人简历/职位-公司-简历.md` from the user's existing resume, work experience, and project experience. The resume must be directly usable for delivery, tailored to the target role, and limited to verified evidence unless marked `待用户确认`.

### Knowledge Gap Plan

Rank gaps by interview probability and preparation ROI. For each gap, provide target mastery, source files to read, practice questions, and an expected answer outline.

### Knowledge Base Expansion

Use existing `岗位要求/`, `网络面经/`, and `个人简历/` content to add or update topic files under `知识题库/`. Maintain `知识题库/知识题库阅读索引.md` as the reading-order index instead of using numeric filename prefixes.

### Mock Interview

When starting a mock interview, first list available targets from `岗位要求/` and ask the user to choose. After selection, generate a timestamped file under `面试模拟/` using Q-only entries. For a specific company-role target, every question must stay within that role's `岗位要求.md`; no out-of-scope QA is allowed. Each question should include source/reference, matching role requirement, competency tested, expected depth, follow-up probes, and scoring rubric, but no answer.

### Mock Interview Evaluation

After the user completes a mock interview, add or produce an evaluation that includes the reference answer, user's score, scoring evidence, missing points, technical corrections, improved answer wording, and related review materials.

### Resume and Project Story Refinement

Suggest wording improvements only when supported by the local resume materials. Mark unverified additions as `待用户确认`.
