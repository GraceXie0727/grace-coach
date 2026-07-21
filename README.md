# grace-coach：个人知识积累教练

一个 Claude 的 Agent Skill：AI 给你连载学习文章，你读完**随便写**几句感想，它自动把你的理解和判断整理成知识卡片存进你自己的知识库——不用记格式、不用管归档，越学越厚的是**你自己的认知资产**，不是 AI 的二手总结。

适合想系统读书、学名人认知、搞懂陌生行业，但又坚持不下来、笔记散落一地的人。不需要会编程。

---

## 它和「直接问 AI」有什么区别

直接问 AI，聊完就散了。grace-coach 把学习做成一个闭环：

1. **为你定制的教材**：开课题时问一句你学这个想用在哪（创业？上班？写作？），经你同意还可以参考你的 CLAUDE.md / memory 里的背景——之后每篇文章的举例、反馈提示都贴着你的情况写。参考了什么明写在学习计划里，你随时可改；无关隐私绝不碰
2. **连载式教学**：一次只讲一小篇，根据你的反馈调整下一篇的难度和角度——看不懂就放慢补例子，掌握了就加深
3. **随便写，自动入库**：读完在文章末尾想到什么写什么，它自动切分成「读书笔记 / 个人判断 / 困惑」三类，整理成知识卡片。进卡片的永远是**你的原话**，AI 不擅自改写
4. **进卡前核实**：你记错了的概念，它先拦下来和你确认，不让错误知识进库
5. **认知点评**：下一篇开头，它会纠正你的事实错误、挑战你的判断、回应你的困惑——像教练，不像复读机
6. **教回来核对**：对照你「用自己的话讲一遍」的复述，检查你是真懂了还是以为自己懂了
7. **掌握进度**：每个核心概念的状态一目了然（🌱 刚讲 → 🌿 有困惑 → 🌳 已吃透）
8. **复习笔记**：每个课题自动维护一本汇总笔记，复习时从头看一遍就行

## 四种模式

| 模式 | 对它说 | 干什么 |
|---|---|---|
| 读书 | 「带我读《纳瓦尔宝典》」 | 把一本书拆成连载文章带你读 |
| 单人名人学习 | 「学纳瓦尔关于赚钱的认知」 | 深度学习一个人在一个主题上的思想 |
| 多人主题学习 | 「我想学关于赚钱的认知」 | 多位名人各讲一章，最后综合对比 |
| 行业/概念学习 | 「带我了解 AI 行业怎么运作」 | 联网搜最新信息，带你搞懂一个行业或概念 |

## 安装

前提：你在用 [Claude Code](https://claude.com/claude-code) 或其他支持 [Agent Skills](https://github.com/vercel-labs/skills) 的工具。方式一另需装 [Node.js](https://nodejs.org)。

### 方式一：一行命令（推荐）

```
npx skills add https://github.com/GraceXie0727/grace-coach --skill grace-coach
```

按提示选「global」和「symlink」，装完重启 Claude Code 即可。

### 方式二：把下面这段话发给 AI

复制粘贴给 Claude Code / Cursor / 任何有 shell 权限的 AI Agent，它会自动装好：

> 帮我安装 `grace-coach` 这个 Claude Code skill。请按下面步骤做：
> 1. 确保 `~/.claude/skills/` 目录存在（不存在就创建）
> 2. 执行 `git clone https://github.com/GraceXie0727/grace-coach.git ~/.claude/skills/grace-coach`
> 3. 验证：`ls ~/.claude/skills/grace-coach/` 应该看到 `SKILL.md`、`modes/` 两项
> 4. 告诉我装好了，之后我说「带我读《某本书》」就会触发这个 skill

### 方式三：手动命令行

```
git clone https://github.com/GraceXie0727/grace-coach.git ~/.claude/skills/grace-coach
```

装完重启 Claude Code。

## 开始使用

装好后，直接说：

- 「带我读《你想读的书》」
- 读完一篇，在文章末尾「学习反馈」区随便写几句，下次说「**继续下一篇**」

第一次使用时它会问你学习库建在哪（默认「文档/AI学习教练/」），以后你的所有学习文章、知识卡片、复习笔记都存在那里，是普通的 Markdown 文件——用 [Obsidian](https://obsidian.md) 打开还能看到概念之间的双链图谱，不用 Obsidian 也完全能用。

```
AI学习教练/
├── INDEX.md          ← 所有课题的进度索引
├── 课题/             ← 连载学习文章
├── 复习笔记/         ← 每课题一本，复习就看它
└── 知识卡片/
    ├── 概念/         ← 你对概念的理解（你的原话）
    └── 我的判断/     ← 你的个人判断（你的原话）
```

## 致谢与来源

- 本 skill 的连续学习循环（章节化学习文章 + 学习反馈区 + 自适应学习梯度 + 部分写作原则）基于 [dontbesilent](https://github.com/dontbesilent2025) 的开源 skill **dbs-learning**（[dontbesilent2025/dbskill](https://github.com/dontbesilent2025/dbskill)，CC BY-NC 4.0）改造。知识卡片入库、进卡前核实、认知点评、教回来核对、概念掌握进度、复习笔记、名人/行业学习模式为本项目的原创扩展。
- 「概念掌握进度」和「教回来核对」两个功能的设计思路，受到 [alexknowshtml/claude-skills](https://github.com/alexknowshtml/claude-skills) 中 teach skill 与 [GarethManning/education-agent-skills](https://github.com/GarethManning/education-agent-skills) 的启发，在此致谢。

## 授权

[CC BY-NC 4.0](LICENSE) © 2026 Grace

可自由使用、修改、分享，需保留署名；**禁止商业用途**——商用（如放进付费产品或课程出售）请先联系上游作者 [dontbesilent](https://github.com/dontbesilent2025) 授权。

---

作者：Grace（[X @Gracexie0727](https://x.com/Gracexie0727)）一个不会编程的文科生创业者。有问题欢迎提 [Issue](../../issues)。
