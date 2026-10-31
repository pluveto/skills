“PR 描述本质上不是一份技术规格文档，而是一页针对 Reviewer 的‘产品推介（Pitch Deck）’与‘转化落地页（Landing Page）’。”
目标用户（Target Audience）：疲惫、忙碌、时间碎片化的 Reviewer 同事。
核心转化目标（Conversion Goal）：让他们无痛、迅速、心甘情愿地点下那个绿色的 Approve 和 Merge 按钮。
核心逻辑：降低认知负荷，讲清楚业务价值（Benefit），做好风险兜底，情绪价值拉满。

参考下面的格式。如果项目自己规定了格式，则用规定的。

### 🎯 TL;DR 
<!-- 30 秒电梯演讲 -->
> **一句话总结**：(AEA Takeaway 句式）
- **关联需求/Bug**：Fixes #1024
- **本次改动性质**：（分类）

## 💡 为什么做这个改动？ (Why)
<!-- 描述问题背景：目前系统有什么问题？为什么要在这个时间点解决？ -->


## 🛠 做了哪些变更？ (What & How)
<!-- 列出核心改动点，突出架构/逻辑决策，而非照抄代码 -->


## 🧪 如何验证？ (How to test)

验证步骤：
<!-- 给出具体的复现/测试步骤，方便 Reviewer 验证 -->
1. 本地启动服务并运行 Redis 容器：`docker-compose up -d redis`
2. 运行单元测试：`pnpm test:auth`
3. 执行手动验证脚本：`curl -X POST http://localhost:3000/api/v2/login ...`
4. 预期结果：返回状态码 200 并携带刷新后的 Token。

自测结果：
<!-- 介绍我们自己验证的结果，以便 Reviewer 可对照 -->

## 📸 效果展示 (Screenshots / UI Changes / Perf Changes...)
<!-- 前端/UI 改动强烈建议提供前后对比截图、GIF 或短视频，优化则体现具体数字。表格格式可自定义。 -->
| Before | After |
| :---: | :---: |
| ![before](url) | ![after](url) |

## ⚠️ 注意事项 / 破坏性变更 (Breaking Changes & Notes)
- [ ] 是否包含破坏性变更
<!-- 是否包含数据库变更、环境变量变动、API 破坏性改动？以及这个PR可能涉及哪些隐患，你怎么做的 -->
- [ ] 需要运行数据库迁移脚本：`npm run migrate`
- [ ] 新增环境变量 `REDIS_PASSWORD`，已更新 `.env.example`。

## ✅ 检查清单 (Checklist)

- [x] 我的代码符合项目的代码规范
- [x] 我已经做过了本地自测（Self-review）
- [x] 我添加了必要的单元测试/集成测试
- [ ] 相关文档已同步更新
- [ ] （如需要）已经过测试环境实测
