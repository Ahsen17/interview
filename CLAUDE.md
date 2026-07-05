# Repository Guidelines

## Project Structure & Module Organization

This repository is an interview and resume preparation knowledge base with a minimal Python 3.12 `uv` project skeleton. The main content is Markdown.

Root files:

- `README.md`: repository overview and recommended workflow.
- `CLAUDE / AGENTS.md`: rules for Codex and other agents working in this repository.
- `pyproject.toml`, `uv.lock`, `.python-version`: Python environment metadata.

Primary content directories:

- `个人简历/`: work experience, project experience, and targeted resume drafts.
- `岗位要求/`: target company and role materials, organized as `岗位要求/公司/职位/岗位介绍.md` and `岗位要求.md`.
- `网络面经/`: collected interview experiences and question patterns, named by company-role or generic role.
- `知识题库/`: technical study material, interview QA, and review paths.
- `面试模拟/`: company-role mock interview questions and post-answer evaluations.

Read the `README.md` in the relevant directory before adding or restructuring content.

## Knowledge Base Layout

`知识题库/` is split by usage:

- `知识题库/知识点/`: systematic study notes, including concepts, principles, implementations, tradeoffs, failure modes, and project landing details.
- `知识题库/面试QA/`: question-focused interview material, including high-frequency questions, answer scripts, follow-ups, scoring points, and common mistakes.
- `知识题库/复习路径/`: reading order, P0/P1/P2 priorities, sprint plans, and mappings from interview questions to local material.
- `知识题库/知识题库阅读索引.md`: the main reading entry point. Keep ordering here instead of using numeric filename prefixes.

Current topic groups include backend engineering, LLM/RAG/Agent, AIGC and data governance, and role/project validation.

## Content Placement Rules

- Put new resume facts, project details, and work history in `个人简历/`.
- Put raw job descriptions and analyzed role requirements in `岗位要求/公司/职位/`.
- Put interview experiences, external question collections, and candidate retrospectives in `网络面经/`.
- Put systematic technical explanations in `知识题库/知识点/`.
- Put interview questions, follow-ups, and answer scripts in `知识题库/面试QA/`.
- Put study sequence, priority, and question-to-material mappings in `知识题库/复习路径/`.
- Put generated mock interviews and evaluations in `面试模拟/`.

Do not use numeric order prefixes in Markdown filenames. Express reading order in `知识题库/知识题库阅读索引.md` or files under `知识题库/复习路径/`.

## Naming Conventions

- Job introduction: `岗位要求/公司/职位/岗位介绍.md`
- Job analysis: `岗位要求/公司/职位/岗位要求.md`
- Targeted resume: `个人简历/职位-公司-简历.md`
- Company-role interview experience: `网络面经/公司-职位.md`
- Generic role interview experience: `网络面经/职位.md`
- Mock interview: `面试模拟/职位-公司-yyyyMMdd-HHmmss.md`
- Mock interview evaluation: update the original mock file or create `面试模拟/职位-公司-yyyyMMdd-HHmmss-评估.md`

Chinese filenames are expected and should stay consistent with the surrounding directory.

## Agent Content Rules

Agents must ground generated content in local repository material. Do not invent personal experience, project metrics, technology usage, interview sources, or job requirements. If a useful enhancement lacks evidence, mark it as `待用户确认`.

When generating a company-role mock interview:

- First list available company-role options from `岗位要求/`.
- Use the selected role's `岗位要求.md` as the boundary for the question scope.
- Each question must point back to a concrete requirement, bonus point, hidden interview signal, or high-probability topic in that `岗位要求.md`.
- `网络面经/`, `个人简历/`, and `知识题库/` may enrich wording, evidence, follow-up depth, and scoring criteria, but must not introduce questions outside the selected role's requirements.
- The initial mock interview should provide question-side information only; add reference answers during evaluation after the user answers.

When evaluating answers, add reference answers, score, strengths, gaps, corrections, better phrasing, and recommended review material.

## Build, Test, and Development Commands

- `uv venv`: create virtual environment by using uv.
- `uv sync`: install the Python 3.12 environment from `pyproject.toml` and `uv.lock`.

There is no Markdown build step. Review Markdown changes directly in an editor or previewer before committing.

## Commit & Pull Request Guidelines

Prefer descriptive imperative commit subjects, such as `Add RAG interview notes` or `Update resume project summary`.

Pull requests should include a short summary, changed directories, commands run, and screenshots or rendered previews for formatting-heavy Markdown changes. Link related job descriptions, issues, or interview targets when applicable.
