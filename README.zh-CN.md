# java-general-standards

`java-general-standards` 是一个可复用的通用 Java 规范 skill，用于代码评审、重构和规范化整理。

## 适用范围

这个 skill 关注的是跨项目可复用的 Java 通用工程规范，包括：

1. 命名、常量、枚举和魔法值治理
2. 代码风格、对象和值处理、集合、并发、控制流
3. 异常边界、错误码、日志规则
4. 单元测试要求和 review 信号
5. MySQL、SQL、ORM 映射约束
6. 工程结构术语、文档与设计信号

它刻意不承载项目专属的后端分层约束。若某个项目还要求严格的 `Controller -> Service -> BizMapper -> Mapper` 调用链，应与 `java-backend-standards` 一起使用。

## 仓库结构

```text
.
├── SKILL.md
├── README.md
├── README.zh-CN.md
├── agents/
│   └── openai.yaml
└── references/
    ├── checklist.md
    ├── code-and-runtime-rules.md
    ├── engineering-structure.md
    ├── exceptions-and-logging.md
    ├── mysql-sql-orm.md
    ├── naming-and-constants.md
    └── unit-testing.md
```

## 内置参考

- `references/naming-and-constants.md`：命名、常量、枚举、魔法值
- `references/code-and-runtime-rules.md`：代码风格、对象/值规则、集合、并发、控制流
- `references/exceptions-and-logging.md`：错误码边界、异常处理、日志规则
- `references/unit-testing.md`：单元测试要求与 review 信号
- `references/mysql-sql-orm.md`：MySQL、SQL、ORM 映射规范
- `references/engineering-structure.md`：模型/分层术语、文档与设计评审信号
- `references/checklist.md`：快速 review 检查单

## 使用方式

将该 skill 安装或复制到 Codex skills 目录，或通过内部 skill 分发流程使用。

当任务关注的是通用 Java 工程质量，而不是某个项目专属的后端分层规范时，优先使用这个 skill。
