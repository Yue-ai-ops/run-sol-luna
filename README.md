# Run Sol + Budget Worker

由 **Yue** 创建的 Codex 省额度工作流：把 Sol 当作稀缺的决策能力，把 Luna Max 当作默认执行能力。目标不是机械地“强模型规划、弱模型干活”，而是用最少的强模型消耗获得可验证结果。

这是 Yue 的个人数字资产，现以 MIT License 向社区开放。

## 默认路线

- 当前任务本来就是 Luna Max：直接完成边界清晰、可验证的工作，不额外套一层 Agent；
- 当前任务是 Sol，且原生接口支持 Luna 子 Agent：Sol 只做简短定向，Luna Max 负责实际执行；
- Luna 被接口拒绝：不反复重试，也不自动改用 Terra；小型任务可由当前 Sol 直接收尾，较长任务建议用交接卡转到新的 Luna Max 任务；
- Terra 只在使用者明确指定时使用。

Sol medium 足以承担日常规划。只有真正存在复杂歧义、重要取舍或高风险验收时才提高到 high；xhigh 留给极少数高风险工作。

额度充足时，可以让 Sol medium 对新的复杂目标做一次短规划，再交给 Luna Max 跑到底；额度开始紧张时，默认直接使用 Luna Max，只在未解决的关键取舍或高风险关口调用 Sol；靠代币点数过渡时，优先保持单个 Luna 任务连续执行，避免并行 Agent、重复复核和可选润色。

## 为什么这样设计

子 Agent 会产生自己的上下文和工具消耗，多 Agent 并不天然省额度。对于 Luna 已经能独立跑到底的任务，直接使用 Luna 往往更省；对于需要强判断的任务，Sol 只应出现在定方向、解冲突和最终高风险验收这些关键时刻。

核验也按风险分级：

- 绿色：Luna 执行并用客观证据自验，Sol 不重复做；
- 黄色：Luna 跑完整流程，Sol 只抽查关键证据与冲突；
- 红色：Sol 保留决策、授权和最终验收，Luna 仍可整理证据和执行可恢复步骤。

## 安装

在 Codex 中调用 `$skill-installer`，安装：

```text
https://github.com/Yue-ai-ops/run-sol-luna/tree/main/skills/run-sol-budget-worker
```

也可以手动复制：

```bash
git clone https://github.com/Yue-ai-ops/run-sol-luna.git
mkdir -p ~/.agents/skills
cp -R run-sol-luna/skills/run-sol-budget-worker ~/.agents/skills/run-sol-budget-worker
```

如果安装后没有立即出现，重启 Codex。

## 使用

最短触发方式：

```text
省额度
```

可以直接写进任务：

```text
省额度，把这个目标跑到验收通过；遇到生产、密钥或真实外发再找我。
```

也可以显式调用：

```text
$run-sol-budget-worker 修复这个测试失败并给出可复核证据。
```

Skill 不会自动切换当前任务的主模型，也不能绕过接口对 Luna 子 Agent 的限制。它会根据当前模型与可用能力选择 `LUNA_DIRECT`、`SOL_PLAN_LUNA_EXEC`、`LUNA_UNAVAILABLE` 或用户明确指定的 `TERRA_EXPLICIT`。

## 适合的任务

- 状态审计、证据提取、日报周报和方案材料；
- 重复测试、日志分析、固定问集、批量检查；
- 浏览器录入、后台配置、可恢复的服务联调；
- 范围明确且有客观测试的编码和多文件实现；
- 长时间但目标清楚、允许按证据逐步推进的执行任务。

需要 Sol 保留最终判断的事项包括：架构承诺、冲突中的主机或运行时身份、生产部署和重启、安全恢复、Secrets、不可逆操作、重要真实外发及最终高风险验收。

## 工作纪律

流程默认只写一张六行任务卡，不逐条播报工具调用，不为了显得工程化而制造额外文档、抽象或复核。达到验收条件即停止。任何 Agent 的“完成”都必须有文件、测试、回执或可见运行状态支持。

## 作者与许可

Original workflow by **Yue**. Public reusable edition maintained as part of Yue's personal digital assets.

Released under the [MIT License](LICENSE).
