# Yue Task Routing · 省额度

Original workflow by **Yue**. Yue 的个人数字资产，MIT 开源。

由 `run-sol-budget-worker` / `run-sol-luna` 升级而来。仓库地址不变；Skill 改名为 `yue-task-routing`，以后换模型不再换流程名字。

## 怎么用

最短口令仍是 **省额度**，或显式调用：

```text
$yue-task-routing 完成当前目标，优先直接执行，需要具体外援时再调用。
```

- 已选 Astra：可以直接把复杂工作做完，不强制退回 Sol 规划、Luna 执行。
- 日常省额度：Luna Max 保留为已有实测支持的经济选项；不把另一档 Luna 当成 Max。
- Terra、Sol：尊重用户选择；Terra 不再锁死 xhigh，也不自动充当 Luna 替代品。
- 独立子任务才考虑委派，具体难题才咨询；子 Agent 返回结果不等于父任务已完成。
- 中途换模型：恢复目标、有效工作和一个下一步，不重做普通测试。
- **额度即将重置**：只做已有且已授权的高价值任务，没有任务就停。Fast 需明确要求并实际可用。

默认保持当前执行者。模型推荐与推理投入分开判断，Ultra 不与并行数量绑定。Skill 不能自动切换主模型、启用 Fast、绕过原生接口限制，也不保证多 Agent 比单模型省。

## 安装与升级

本次发布在功能分支，尚未合入 main。让 `$skill-installer` 安装以下目录：

```text
https://github.com/Yue-ai-ops/run-sol-luna/tree/codex/rename-budget-worker-skill/skills/yue-task-routing
```

也可将该分支的 `skills/yue-task-routing` 复制到个人 `~/.agents/skills/`。升级时只保留一个有效安装：移走旧 `run-sol-luna` 或 `run-sol-budget-worker` 安装，避免同时加载旧规则。保留自己的未同步修改，不盲目覆盖。新任务中检查 `$yue-task-routing`；列表未刷新时重新打开应用。旧名称仍可作为自然语言线索，不保证旧 `$` 选择器别名有效。

## 为什么没有更多流程

入口只规定目标、责任、委派和交接；[模型建议](skills/yue-task-routing/references/model-choices.md)单独更新。交接和重置细则按需读取。不给每个模型建立角色层，不给普通任务增加审批或重复审查。安全、数据保护和真实生产授权仍遵循项目规则。

采用 [OpenAI agent patterns](https://github.com/openai/openai-agents-python/blob/main/examples/agent_patterns/README.md) 中“有界调用”和“真正交接”的区别；无需安装新 Agent 框架。

公开费用和模型定位不是 Yue 工作现场的胜负结论。小样本验证不等于生产验收，也不能推算共享周额度；具体推荐保留实验性质。

Released under the [MIT License](LICENSE). Original workflow by **Yue**.
