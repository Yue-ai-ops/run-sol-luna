# Run Sol + Budget Worker

由 **Yue** 创建的 Codex 省额度工作流：把 Luna Max 当作默认执行者，Sol 只处理真正需要强判断的高风险问题。目标是用最少的强模型消耗获得真实结果，而不是制造编排仪式。

这是 Yue 的个人数字资产，现以 MIT License 向社区开放。

## 默认路线

- 当前任务本来就是 Luna Max：直接跑到目标完成，不额外套一层 Agent 或 Sol 复核；
- 当前任务是 Sol，且原生接口支持 Luna 子 Agent：先生成当前目标的交接，再明确启动 `gpt-5.6-luna + max`；
- Luna Max 被接口拒绝：不反复重试、不使用其他 Luna 推理档，也不自动改用 Terra；建议直接把当前任务切换到 Luna Max；
- Terra 只在使用者明确指定时使用。

无论额度充足还是紧张，执行默认交给 Luna Max。Sol medium 只在当前任务已经由 Sol 开启时充当启动器；high/xhigh 只留给真实存在的复杂高风险决定，不为普通工作预先设计证据门。

## 为什么这样设计

子 Agent 会产生自己的上下文和工具消耗，多 Agent 并不天然省额度。当前已经是 Luna Max 时直接执行最省；必须从 Sol 启动时，只开一个 Luna Max，并把“用户真正要完成什么、已经完成什么、下一步是什么”交接过去。Luna 自己做正常验证，Sol 不再重复检查，除非 Luna 明确遇到高风险冲突。

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

Skill 不会自动切换当前任务的主模型，也不能绕过接口对 Luna 子 Agent 的限制。它只接受 `gpt-5.6-luna + max`，并选择以下七条路线之一：`LUNA_MAX_DIRECT`、`SOL_HANDOFF_TO_LUNA_MAX`、`LUNA_WITH_SOL_ADVICE`、`MODEL_SWITCH_RECOVERY`、`SWITCHBACK_GAP_RECOVERY`、`LUNA_MAX_UNAVAILABLE`、`TERRA_EXPLICIT`。

## 中途切换与交接

模型切换不是重新开工。切换时只做一次最小现场刷新：当前目标和验收、项目/工作区与分支、相关主机或运行时、已验证事实、未验证事项和下一步动作。

- Sol → Luna：Sol 先交接，Luna Max 成为唯一执行者；不把完整目标缩成一张局部证据清单。
- Luna → Sol：只有一个具体高风险问题才请 Sol 给建议；Sol 只回答取舍，不改文件、不运行、不接管任务。
- Sol → Luna → Sol：使用 T0（最后可信的 Sol 状态）、T1（Luna 实际完成的工作）、T2（当前现场）对账，并逐项标记 `KEEP`、`VERIFY`、`REWORK` 或 `DROP`。
- 直接在模型选择器切换：先恢复最近交接，继续有效工作，不因换模型重新规划整个项目。

Skill 优先更新已有项目交接文件；只有长周期项目没有合适位置时才创建一个 `AGENT_HANDOFF.md`，不会每次切换都生成新文件。

## 适合的任务

- 状态审计、证据提取、日报周报和方案材料；
- 重复测试、日志分析、固定问集、批量检查；
- 浏览器录入、后台配置、可恢复的服务联调；
- 范围明确且有客观测试的编码和多文件实现；
- 长时间但目标清楚、允许按证据逐步推进的执行任务。

需要 Sol 保留最终判断的事项包括：架构承诺、冲突中的主机或运行时身份、生产部署和重启、安全恢复、Secrets、不可逆操作、重要真实外发及最终高风险验收。

## 工作纪律

流程不写固定六行任务卡，也不要求 Sol 重做普通任务。交接保存状态而不是重写计划；Luna 继承可用上下文、自主执行并完成正常验证；现有项目、权限和安全边界继续有效，但不再被重复包装成一套新证据门。

## 作者与许可

Original workflow by **Yue**. Public reusable edition maintained as part of Yue's personal digital assets.

Released under the [MIT License](LICENSE).
