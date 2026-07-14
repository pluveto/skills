  Epic 施工方式（通用）

  角色
  - 主 Agent：架构、plan/progress/decisions、worktree 生命周期、并行编排、
    合并与 epic 级 review 循环；99% 不写业务代码。
  - 施工小弟（Subagents）：只在分配的 worktree/path 内实现；遵循该仓 AGENTS.md 与项目规范；
    禁止改 progress.md；禁止扩 scope；禁止自建/销毁 worktree。
  - Reviewer：sub-task 1 轮审核一轮改；epic 多轮收敛；禁止超 scope。
  - 主 Agent:
    - 如果你是 Codex 环境，subagent 可能会花非常漫长的时间来完成。
      如果 subagent 持续运行中，禁止任何理由提前杀死。
    - 如果你是 Claude Code 等系统会在完成时通知你的环境，则耐心等待即可。

  工件（主 Agent 维护）
  - ~/.cache/docs/<epic>/plan.md
  - ~/.cache/docs/<epic>/progress.md  状态：todo|doing|in_review|changes_requested|blocked|done|cancelled
  - ~/.cache/docs/<epic>/decisions.md
  - ~/.cache/docs/<epic>/log.txt 用于追加执行轨迹，航海日志和大事记录。避免对话上下文丢失后主 agent 忘记发生了什么。

  分支与仓
  - 每个可独立发布的 git 仓：一条 epic 工作分支（或 gt stack）。
  - 集成/伞仓：只做集成（bump/指针/跨仓 CI），不直接改子模块业务源码。
  - main worktree 应当始终处于 clean 状态。分支集成、切出 epic 必须在单独的 epic-worktree 进行。禁止 main worktree 上直接切出分支。

  并行
  - plan 声明 path ownership 与 parallel waves。
  - wave 内最大并行；跨 wave 遵守依赖。
  - 同一 path 同时只允许一个 writer。

  质量门
  - 每个 sub-task 完成后：仅 1 轮 codex review（brief 含 allowed paths + DoD + non-goals）。
    失效时用 subagent review，同一 brief。
  - 全部 sub-task 粗完成后合入各仓 epic 分支，再 epic 级 review→request-change→rework，
    max_rounds 在 plan 中写死（默认 3，难 5–8）。
  - 收敛或达上限后停止；残留问题记入 open list，不扩 scope。

  合并
  - 需要 stacked PR 时用 gt；跨仓不进同一 stack。
  - 集成仓最后 bump。

  主 Agent 写码例外（仅）
  - plan/progress/decisions、合并冲突、最小 unblock；并记 progress。

  
