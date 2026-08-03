# Run Sol + Luna

由 **Yue** 创建的 Codex 省额度工作流：让 Sol 负责规划、风险判断和最终验收，让 Luna Max 执行边界清晰、可以独立验证的子任务。

这是 Yue 的个人数字资产，现以 MIT License 向社区开放。

## 它解决什么问题

当强模型额度有限时，不必把整个任务切换给较弱模型。这个 Skill 会让当前主任务继续担任控制者，只把适合委派的工作交给 Luna Max，再由主任务回看文件、测试和运行证据后给出最终结论。

默认策略：

- Sol high 负责常规规划与验收；
- 1 个 Luna Max worker 负责执行；
- 只有两个任务真正独立且分别可验证时，才使用第 2 个 worker；
- 生产、部署、安全恢复、真实外发和最终高风险裁决不交给 Luna。

## 使用前提

- 使用支持 Skills 和原生子 Agent 协作的 Codex 版本；
- 账号或工作区能够使用 `gpt-5.6-luna`；
- 主任务模型由使用者自己选择，Skill 不会自动把主模型切换成 Sol；
- 推荐日常任务选择 Sol high，简单只读任务可用 medium，高风险任务才使用 xhigh。

如果当前任务没有原生子 Agent 工具，Skill 会报告 `PARTIAL` 或 `NOT_VERIFIED`，不会用额外 CLI 进程伪装成 Luna 子 Agent。

## 安装

### 使用 Skill Installer

在 Codex 中调用 `$skill-installer`，并让它安装：

```text
https://github.com/Yue-ai-ops/run-sol-luna/tree/main/skills/run-sol-luna
```

### 手动安装

```bash
git clone https://github.com/Yue-ai-ops/run-sol-luna.git
mkdir -p ~/.agents/skills
cp -R run-sol-luna/skills/run-sol-luna ~/.agents/skills/run-sol-luna
```

如果安装后没有立即出现，重启 Codex。

## 使用

最短触发方式：

```text
省额度
```

可以直接放进任务里：

```text
省额度，检查这个项目当前状态并告诉我唯一下一步。
```

也可以显式调用：

```text
$run-sol-luna 修复这个测试失败，完成后由主任务独立验收。
```

## 适合的任务

- 状态审计、证据提取和材料对账；
- 日报、周报和结构化汇报初稿；
- 重复测试、日志分析和批量检查；
- 边界明确、修改范围固定并且有客观测试的编码任务；
- 两个互不写同一文件、能够独立验收的并行子任务。

不适合直接委派的任务：架构最终决策、跨主机或运行时身份判断、生产部署、重启、安全恢复、密钥处理、不可逆操作、真实外发和最终验收。

## 工作原则

子 Agent 的“完成”只是待核验的汇报，不是事实。主任务必须回看当前文件、Git 状态、测试、回执或运行时证据，才能宣布任务完成。

## 作者与许可

Original workflow by **Yue**. Public reusable edition maintained as part of Yue's personal digital assets.

Released under the [MIT License](LICENSE).
