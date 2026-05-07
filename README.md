# ERP_system — 医疗耗材验收系统

> 一个分阶段演进的全栈学习项目。
> 从本地 Excel 工具,逐步演进为生产级 Web 系统。

## 当前阶段

**阶段 1(W1-W6):本地 Excel 作业台**

技术栈:HTML + CSS + 原生 JavaScript + FastAPI + openpyxl

目标:浏览器扫码 → 查询订单 → 整单验收的完整闭环。

## 项目结构
ERP/
├── app/                          # 主应用包
│   ├── constants.py              # 集中管理固定字段(Excel 表头、状态值)
│   ├── main.py                   # FastAPI 入口(路由 + 异常捕获)
│   ├── repositories/             # 数据访问层(唯一能读写 Excel 的地方)
│   │   └── excel_order_repository.py
│   └── services/                 # 业务逻辑层
│       └── order_service.py
├── requirements.txt              # Python 依赖清单
├── .gitignore                    # Git 忽略规则
└── README.md                     # 本文件

## 如何启动

(W4 完成后填写,当前为占位)

## 学习路线

详见 `LEARNING_ROADMAP.md`(项目级文档,不在 Git 仓库)。

## 三层架构铁律

- `main.py` 不读数据
- `services/` 不读数据
- 只有 `repositories/` 能读写数据源
- 数据源会演进:Excel(阶段 1) → SQLite(阶段 1.5) → PostgreSQL(阶段 2)
- 每次升级,只换 repositories 层,前端和 services 不动