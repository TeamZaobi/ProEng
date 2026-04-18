# ProductEngineer 与 files-driven 的边界矩阵

## 一句话分工

- `files-driven` 管“怎么稳住项目协作秩序”。
- `ProductEngineer` 管“这个具体产品或功能到底做什么、怎么做、做到什么程度算过线”。

## 默认站位

- 把 `ProductEngineer` 放在 `project_scope`，作为下游项目里的业务能力或叶子 skill。
- 让 `files-driven` 继续站在 `capability_scope`，负责判路、定真源、控写权、做恢复和审计。

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

### `refactor`

- `ProductEngineer`：代码和产品结构重构。
- `files-driven`：治理结构 realignment、文件归位、合同链补齐和边界修复。

## 实用判定线

先问一句：

- 如果核心问题是“这个产品该做什么、用户怎么用、怎样才算交付完成”，走 `ProductEngineer`。
- 如果核心问题是“哪份文件算数、谁有写权、这次该先停在哪个 gate、怎么避免漂移”，走 `files-driven`。

## 协作顺序

1. 让 `files-driven` 先定入口、真源、允许写入目标和一级 gate。
2. 让 `ProductEngineer` 在允许范围内产出 `PRD`、计划、架构说明、重构方案等项目资产内容。
3. 让 `files-driven` 在产出之后判断这些资产是否越权、是否需要注册、是否该进入后续 workflow 或 audit。

## 推荐定义

> `ProductEngineer` 面向下游项目的产品与工程设计工作，负责把边界明确的问题压成 PRD、计划、架构说明、验收标准和重构方案；它不判定治理真源、不改写项目级写权规则、不替代 files-driven 做 scope、route、contract 和 governance audit 判断。
