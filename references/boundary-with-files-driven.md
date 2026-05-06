# ProductEngineer 与 files-driven 的边界矩阵

## 一句话分工

- `files-driven` 管“怎么稳住项目协作秩序”。
- `ProductEngineer` 管“这个具体产品或功能到底做什么、怎么做、做到什么程度算过线”。

## 默认站位

- 把 `ProductEngineer` 放在 `project_scope`，作为下游项目里的业务能力或叶子 skill。
- 让 `files-driven` 继续站在 `capability_scope`，负责判路、定真源、控写权、做恢复和审计。
- 当产品本身是 Agent-Native 对象，`ProductEngineer` 仍负责产品语义：谁用、替谁降熵、上下文如何被获取和恢复、Agent Architecture / Skills / Rules / Gates 如何构成完整能力、agent 稳定能做什么、状态和证据怎么被用户理解、handoff / recovery 如何成为产品体验。
- 同一场景下，`files-driven` 仍负责治理控制：真源、写权、schema、validator、route contract、projection、runtime / adoption audit 和 release gate。

## 适合放进 ProductEngineer 的能力

- `PRD`
- `feature plan`
- `product architecture`
- `refactor proposal`
- `domain audit`

这些能力都在回答“项目内容应该长成什么样”。

## 继续留在 files-driven 的能力

- 判定哪份文件是真源，哪份只是投影或展示。
- 判定当前在 `capability_scope / project_scope / runtime_scope` 哪一层说话。
- 判定 `PRD / PLAN / ADR / task / decision / BOUNDARY` 应该分别落在哪类资产。
- 判定谁能写、什么时候能写、能写哪些路径。
- 判定什么时候该 `install / register / repair / audit`。
- 做 governance audit、runtime audit、pack audit、adoption audit。
- 处理 self-hosting、intent routes、registry、workflow contract、恢复链和晋升链。

这些能力都在回答“协作秩序怎么稳住”。

## 最容易混淆的几组能力

### `plan`

- `ProductEngineer`：版本计划、功能计划、交付切片、依赖排序。
- `files-driven`：治理补完计划、repair plan、cutover plan、runner rollout plan。

### `audit`

- `ProductEngineer`：PRD 审计、需求覆盖审计、故事与验收闭环审计、实现偏题审计。
- `files-driven`：真源、写权、投影越权、pack、runtime、governance、adoption 审计。

### `architect`

- `ProductEngineer`：产品和系统方案，服务边界、模块边界、页面和信息架构。
- `files-driven`：repo、starter、control-plane、contract、route、harness 的治理架构。

### `agent-native`

- `ProductEngineer`：Agent-Native 产品定义、actor map、context spine、construction stack、agentic loop、能力边界、状态和证据对象、handoff / recovery 作为用户价值、agent-side user story、可感知 done line。
- `files-driven`：AI-Native 项目治理、scope 判定、入口真源、写权边界、工具投影、contract / schema / validator、runtime audit、pack audit、adoption audit。

### `refactor`

- `ProductEngineer`：代码和产品结构重构。
- `files-driven`：治理结构 realignment、文件归位、合同链补齐和边界修复。

## 实用判定线

先问一句：

- 如果核心问题是“这个产品该做什么、用户怎么用、怎样才算交付完成”，走 `ProductEngineer`。
- 如果核心问题是“哪份文件算数、谁有写权、这次该先停在哪个 gate、怎么避免漂移”，走 `files-driven`。
- 如果核心问题是“这个 agent / skill / workflow 到底应该替人和下游 agent 稳定完成什么闭环”，走 `ProductEngineer`。
- 如果核心问题是“这个 agent / skill / workflow 的真源、入口、投影、validator 或运行 gate 怎么稳住”，走 `files-driven`。

## 协作顺序

1. 让 `files-driven` 先定入口、真源、允许写入目标和一级 gate。
2. 让 `ProductEngineer` 在允许范围内产出 `PRD`、计划、架构说明、重构方案等项目资产内容。
3. 让 `files-driven` 在产出之后判断这些资产是否越权、是否需要注册、是否该进入后续 workflow 或 audit。

## 结构化控制面的反向协作请求

当 `ProductEngineer` 发现下游项目需要把需求链路追踪到开发、测试、证据和交付时，不自行发明 metadata、JSON schema、状态机、traceability index 或 validator。

当 Agent-Native 产品需要状态、证据、回执、handoff 或 recovery 成为长期可恢复对象时，也按同一规则处理：
`ProductEngineer` 只说明产品为什么需要这些对象、用户如何感知它们、最小字段应覆盖哪些产品语义；
`files-driven` 决定它们是否进入项目控制面，以及如何落成真源、schema、validator、注册和 gate。

当 Agent-Native 产品需要把上下文变成可恢复对象时，也同样处理：
`ProductEngineer` 说明 context spine 的产品语义和最小字段，例如 context source、trust level、compression note、exclusion reason、state binding、evidence binding 和 recovery focus；
`files-driven` 决定这些字段是否进入正式控制面。

当 Agent-Native 产品需要定义 `Agent Architecture + Skills + Rules + Gates` 时：
`ProductEngineer` 说明这四层为什么是完整产品构建方式，以及它们如何服务使用者熵减和交付质量；
`files-driven` 负责判定 rules / gate / validator / projection / runtime audit 的真源、写权、注册和执行生效方式。

此时它只能向 `files-driven` 提出 `files-driven collaboration request`，说明：

1. 需要哪类控制面：`metadata_profile / traceability_index / validator / downstream_adapter`。
2. 产品内容侧建议追踪哪些字段：例如 request id、architecture coupling verdict、dependency graph、acceptance signals、handoff surfaces 和 evidence needs。
3. 当前项目是否已有 intake / handoff profile；没有时是否需要先由 `files-driven` 建立最小 profile。
4. 缺少控制面时，产物应停在候选需求、PRD patch 还是不能继续 handoff。

`files-driven` 决定这些字段是否进入项目控制面，并负责 schema、状态词表、validator、写权、注册位置和失败时的 stop gate。

## 推荐定义

> `ProductEngineer` 面向下游项目的产品与工程设计工作，负责把边界明确的问题压成 PRD、计划、架构说明、验收标准和重构方案；它不判定治理真源、不改写项目级写权规则、不替代 files-driven 做 scope、route、contract 和 governance audit 判断。
