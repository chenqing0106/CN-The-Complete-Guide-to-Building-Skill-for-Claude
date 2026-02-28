# CN-The-Complete-Guide-to-Building-Skill-for-Claude
本仓库包含Claude官方发布的[《The-Complete-Guide-to-Building-Skill-for-Claude》](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf?hsLang=en)的中文翻译与排版稿，详细介绍 Skill 结构、设计模式、测试迭代、分发方案及故障排查。适合希望快速上手 Claude Skill 开发的个人和团队。

## 核心内容总结

**Skill 是什么**：一个文件夹，核心是 `SKILL.md`，告诉 Claude 什么时候用、怎么用某个工作流。类似"给 Agent 装插件"，但比插件更轻量——本质是结构化的 Prompt + 工具调用指南。

**三层渐进式设计**是最聪明的地方：YAML frontmatter 常驻系统提示词（决定"要不要触发"），SKILL.md 正文按需加载（决定"怎么做"），references/ 文件夹按需读取（决定"查什么资料"）。这直接解决了 Token 浪费问题。

**五种核心模式**：顺序工作流、多 MCP 协调、迭代精炼、上下文感知工具选择、领域专业知识嵌入。覆盖了绝大多数实际场景。

---

## 评价(来自于Claude)

**优点**

写得非常务实，没有学术腔。尤其两个地方特别好：一是"先在单个任务上迭代直到成功，再提取成 Skill"的建议，这是真正踩过坑得出的结论。二是 Troubleshooting 章节，把"触发太少、触发太多、指令不被遵守"这三类最常见问题都给了具体的诊断路径，不是泛泛而谈。

**局限性**

有两点值得警惕：

第一，**评估体系还很粗糙**。文档自己也承认"接受 vibes-based assessment"，量化指标（90% 触发率、0 次 API 失败）只是目标，没有提供真正的测量工具。对于认真做 Agent 的人来说，这块还需要自己补。

第二，**MCP 依赖还比较重**。很多模式都预设了你已经有 MCP Server，对于刚入门的开发者，前置成本不低。
