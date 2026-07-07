# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Primary Workflow Tool

**Use the `interview-assistant` skill for all interview preparation tasks.** This includes:
- Analyzing personal resume, work experience, and project materials
- Extracting and analyzing job requirements from job postings
- Generating targeted resumes for specific roles
- Creating candidate profiles and gap analyses
- Building study plans and technical review material
- Generating company-role mock interviews
- Evaluating completed mock interview answers

The skill enforces critical grounding requirements and workflow constraints described in this file.

## Repository Overview

This is an interview and resume preparation knowledge base with a minimal Python 3.12 `uv` project skeleton. The main content is Markdown documentation organized into a structured workflow: job requirements → resume preparation → knowledge review → mock interviews → evaluation and improvement.

## Directory Structure

```
.
├── 个人简历/          # Personal resume, work history, projects, targeted resumes
│   └── 面试准备/      # Interview preparation artifacts (profiles, plans, analyses)
├── 岗位要求/          # Job requirements organized as 公司/职位/
│   └── 公司/职位/     # Company/role folders containing:
│       ├── 岗位介绍.md   # Raw job posting
│       └── 岗位要求.md   # Analyzed requirements
├── 网络面经/          # Interview experiences (公司-职位.md or 职位.md)
├── 知识题库/          # Technical study material
│   ├── 知识点/        # Systematic study notes
│   ├── 面试QA/        # Interview Q&A scripts
│   ├── 复习路径/      # Study sequences and priorities
│   └── 知识题库阅读索引.md  # Main reading entry point
└── 面试模拟/          # Mock interviews and evaluations
```

Each directory contains its own README.md with specific guidance. Read the relevant README before adding or restructuring content.

## Critical Content Rules

### Grounding Requirement

**All generated content must be grounded in local repository material.** Agents must NOT invent:
- Personal work experience or employment history
- Project metrics, scale, or business outcomes
- Technology usage or technical decisions
- Interview question sources or company-specific patterns
- Job requirement claims not present in the job posting

If an enhancement would be valuable but lacks evidence in local files, mark it as `待用户确认` (pending user confirmation).

### Mock Interview Scope Constraint

When generating company-role mock interviews:

1. **List available options first:** Before generating, list all company-role combinations from `岗位要求/` and let the user select the target.

2. **Stay within role requirements:** Every question must map back to a concrete requirement, bonus qualification, implicit interview signal, or high-probability topic in that role's `岗位要求.md`.

3. **Supporting material only:** `网络面经/`, `个人简历/`, and `知识题库/` may enrich question wording, evidence examples, follow-up depth, and scoring criteria, but must NOT introduce questions outside the selected role's requirements.

4. **Question-only format:** Initial mock interview files contain only questions, source references, competency tested, expected depth, follow-up probes, and scoring rubrics. Add reference answers during evaluation after the user responds.

### Evidence Classification

When analyzing resume materials or generating content, classify evidence strength:
- `强证据` (strong evidence): Direct facts from resume/project files
- `弱证据` (weak evidence): Implied or indirect support
- `缺失证据` (missing evidence): Gap with no local support
- `待用户确认` (pending confirmation): Useful claim that needs verification

## File Naming Conventions

Use these exact patterns (Chinese filenames are expected):

- Job posting: `岗位要求/公司/职位/岗位介绍.md`
- Job analysis: `岗位要求/公司/职位/岗位要求.md`
- Targeted resume: `个人简历/职位-公司-简历.md`
- Company-role interview experience: `网络面经/公司-职位.md`
- Generic role interview experience: `网络面经/职位.md`
- Mock interview: `面试模拟/职位-公司-yyyyMMdd-HHmmss.md`
- Mock evaluation: Update original file or create `面试模拟/职位-公司-yyyyMMdd-HHmmss-评估.md`

**Do not use numeric prefixes for ordering.** Express reading order in `知识题库/知识题库阅读索引.md` or files under `知识题库/复习路径/`.

## Knowledge Base Organization

`知识题库/` is split by usage pattern:

- **知识点/**: Systematic study notes including concepts, principles, implementations, tradeoffs, failure modes, and project landing details.
- **面试QA/**: Question-focused interview material including high-frequency questions, answer scripts, follow-ups, scoring points, and common mistakes.
- **复习路径/**: Reading order, P0/P1/P2 priorities, sprint plans, and mappings from interview questions to local material.
- **知识题库阅读索引.md**: Main reading entry point. Maintain ordering here instead of using numeric filename prefixes.

Current topic groups include backend engineering, LLM/RAG/Agent systems, AIGC and data governance, and role/project validation.

## Development Commands

```bash
# Create virtual environment
uv venv

# Install Python 3.12 environment from pyproject.toml and uv.lock
uv sync

# Alternative: install all packages
uv sync --all-packages
```

There is no Markdown build step. Review Markdown changes directly in an editor or previewer before committing.

## Commit Guidelines

Use descriptive imperative commit subjects:
- `Add RAG interview notes`
- `Update resume project summary`
- `Generate mock interview for Backend-CompanyX`
- `Evaluate mock interview responses`

Pull requests should include:
- Short summary of changes
- Changed directories
- Commands run (if applicable)
- Screenshots or rendered previews for formatting-heavy Markdown changes
- Links to related job descriptions or interview targets when applicable
