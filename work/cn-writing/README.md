# cn-writing

一个同时适用于 Codex 与 Claude Code 的中文写作 skill。它把信息边界、UI 文案、技术写作、解释型网页、自然中文审校和术语治理放在同一个入口中，再按任务读取对应 reference。

## 目录

```text
cn-writing/
├── SKILL.md
├── README.md
├── LICENSE
├── THIRD_PARTY_NOTICES.md
└── references/
    ├── content-boundary.md
    ├── ui-copy.md
    ├── technical-writing.md
    ├── explainer-page.md
    ├── natural-chinese.md
    └── terminology.md
```

## 安装

### Codex

个人范围：

```bash
mkdir -p ~/.agents/skills
cp -R cn-writing ~/.agents/skills/cn-writing
```

项目范围：

```bash
mkdir -p .agents/skills
cp -R cn-writing .agents/skills/cn-writing
```

### Claude Code

个人范围：

```bash
mkdir -p ~/.claude/skills
cp -R cn-writing ~/.claude/skills/cn-writing
```

项目范围：

```bash
mkdir -p .claude/skills
cp -R cn-writing .claude/skills/cn-writing
```

同一份目录可以通过符号链接同时提供给两者：

```bash
mkdir -p ~/.agents/skills ~/.claude/skills ~/agent-skills
cp -R cn-writing ~/agent-skills/cn-writing
ln -s ~/agent-skills/cn-writing ~/.agents/skills/cn-writing
ln -s ~/agent-skills/cn-writing ~/.claude/skills/cn-writing
```

目标位置已存在时，先删除旧目录或改用其他存放位置。

## 调用

Claude Code 可以显式调用：

```text
/cn-writing
```

Codex 可以通过 skill 选择器或 `$cn-writing` 显式指定。任务与 `description` 匹配时，两者也可以自动加载。

## 建议的全局规则

可在 `AGENTS.md` 或 `CLAUDE.md` 中保留一句触发规则，无需复制完整写作规范：

```md
生成或修改中文 UI、技术文档、代码注释、说明网页等用户或读者可见内容时，使用 cn-writing skill，并只提交最终有效内容。
```

## 项目定制

优先修改 `references/terminology.md`，加入项目已有的中英文术语、禁用简称和适用范围。需要固定产品语气时，可以在相应 reference 中增加少量真实成稿，但不要把所有项目规则都堆进 `SKILL.md`。

主文件负责路由和工作流，references 负责具体载体。这样保持一个 skill 入口，同时避免每次任务都加载全部规则。
