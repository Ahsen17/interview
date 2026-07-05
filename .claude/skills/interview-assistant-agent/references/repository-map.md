# Repository Map

Detailed reference for the interview-assistant-agent skill: source folders, default target, output locations, naming rules, and full artifact templates. Read this before producing any deliverable. Authoritative repo rules live in the root `CLAUDE.md` / `AGENTS.md`; if anything conflicts, those win.

## Source Folders

- `岗位要求/`: Target company and role requirements, organized as `岗位要求/公司/职位/岗位介绍.md`. Prefer the most specific nested role folder. Read `岗位介绍.md` and `岗位要求.md` together when both exist. If `岗位要求.md` is missing and role analysis is requested, create it from `岗位介绍.md`.
- `个人简历/`: Resume source material, including the main resume, work experience, and project experience. Treat these files as the source of truth for the candidate's background. Targeted delivery resumes should also be saved here as `职位-公司-简历.md`.
- `知识题库/`: Local technical knowledge base. Start from `知识题库阅读索引.md`, then load only relevant topic files. This folder is continuously expanded from `岗位要求/`, `网络面经/`, `个人简历/`, and confirmed mock interview evaluations.
- `网络面经/`: Local interview experience notes. Use these to estimate question style, common themes, and company-specific patterns. Company-role-specific notes use `公司-职位.md`; general role notes use `职位.md`.
- `面试模拟/`: Mock interview question and evaluation artifacts. Generate timestamped mock interview files here after the user selects a target company and role.

## Default Target In This Repository

When the user does not specify a target role, assume the current target is:

`岗位要求/XX 公司/后端开发工程师/`

State this assumption before producing role-specific analysis. Replace `XX 公司` with the actual company folder once the user names one.

## Recommended Output Folder

Write durable artifacts to:

`个人简历/面试准备/`

Create the folder if it does not exist. Do not overwrite existing preparation files unless the user asks for replacement; create a clearer filename or update only the relevant sections.

Task-specific outputs override this default:

- Job requirement extraction: `岗位要求/公司/职位/岗位要求.md`
- Targeted delivery resume: `个人简历/职位-公司-简历.md`
- Mock interview questions: `面试模拟/职位-公司-yyyyMMdd-HHmmss.md`
- Mock interview evaluation: update the corresponding mock file or create `面试模拟/职位-公司-yyyyMMdd-HHmmss-评估.md`, depending on the user's request.

Use timestamp format `yyyyMMdd-HHmmss` for mock interview filenames unless the user requests another format.

## Naming Rules

- Do not use numeric order prefixes in Markdown filenames. Express reading order in `知识题库/知识题库阅读索引.md`.
- Preserve existing Chinese directory and role names.
- For ByteDance/Douyin, use the company name already present in the folder when deriving filenames. If the user explicitly says `XX 公司`, use `XX 公司` in generated resume and mock filenames.
- Never overwrite source resume, work experience, project experience, or interview notes unless the user explicitly asks for an update.

## Useful Artifact Templates

### 岗位要求.md

Use sections:

1. 岗位定位
2. 真实招聘需求
3. 必备能力
4. 加分能力
5. 隐含面试信号
6. 技术关键词
7. 可映射的简历证据
8. 高概率面试主题
9. 待确认信息

For each requirement, include importance, evidence expectation, and likely interview probe.

### 职位-公司-简历.md

Use sections:

1. 个人信息
2. 求职意向
3. 个人优势
4. 技术栈
5. 工作经历
6. 项目经历
7. 教育经历
8. 待用户确认的增强点

Rules:

- Tailor wording to `岗位要求.md`.
- Use only verified evidence from `个人简历/` unless clearly marked `待用户确认`.
- Prefer impact, ownership, technical decision, and business/result language over keyword stuffing.

### 岗位匹配分析.md

Use sections:

1. 目标岗位摘要
2. 能力矩阵
3. 简历证据映射
4. 高风险差距
5. 简历与项目表达优化
6. 面试准备优先级

### 技术面试题-专项训练.md

Use sections:

1. 高频问题清单
2. AI Agent 与多 Agent
3. RAG 与检索优化
4. LLM Tool Calling 与 Prompt 工程
5. 后端系统设计与高可用
6. 数据建模、SQL 与成本治理
7. 项目追问与反问

For each question, include:

- 考察点
- 参考回答
- 结合个人项目的说法
- 追问方向
- 常见失分点

### 7天冲刺计划.md

Use a day-by-day plan with:

- 今日目标
- 必读本地材料
- 输出物
- 口述训练题
- 验收标准

### 项目问答话术.md

For each project, include:

- 30 秒介绍
- 2 分钟深挖版
- 技术架构
- 关键难点
- 取舍与替代方案
- 可量化结果或待确认指标
- 面试官可能追问

### 面试模拟题.md

Use Q-only entries. Do not provide answers in the initial mock interview artifact.

Recommended front matter:

```markdown
# 职位-公司-模拟面试题

- 生成时间：
- 目标公司：
- 目标岗位：
- 依据材料：
- 轮次设计：
- 使用说明：请直接在每道题的“我的回答”下作答；初版不提供参考答案，评估阶段再补充。
```

Recommended question block:

```markdown
## Q1. 问题标题

- 问题：
- 来源或参考：
- 考察点：
- 预期回答深度：
- 追问方向：
- 评分维度：
- 我的回答：
```

Suggested rounds:

1. 简历深挖
2. 项目架构与技术取舍
3. AI Agent/RAG/LLM 应用工程
4. 后端工程与系统设计
5. 数据、评估与成本治理
6. 行为面与协作复盘

### 面试模拟评估.md

For each completed question, include:

- 参考答案
- 用户回答评分
- 得分点
- 不足之处
- 技术纠错
- 更优表达
- 建议复习材料
