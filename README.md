# Bailian Agent Engineering Lab

一套基于阿里云百炼模型的 Agent 工程学习实验室，覆盖从手写 Agent Loop 到工具调用、MCP、LangGraph、记忆、Agentic RAG、多 Agent、评估、可观测性、部署和安全的完整路线。

## 课程目录

课程已按知识节点拆成 12 个可独立运行的 Notebook，直接放在项目根目录：

| 课次 | Notebook | 主题 |
| --- | --- | --- |
| 00 | `00_环境安装与配置.ipynb` | Python、虚拟环境、Jupyter 与密钥安全 |
| 01 | `01_Python异步与Pydantic.ipynb` | 异步、类型注解和输入校验 |
| 02 | `02_最小Agent循环.ipynb` | 手写 Agent Loop 与循环防护 |
| 03 | `03_Function_Calling工具.ipynb` | 天气、汇率、待办、日志和搜索工具 |
| 04 | `04_MCP安全文件服务.ipynb` | FastMCP 与文件系统安全 |
| 05 | `05_LangGraph工作流.ipynb` | 状态、节点、条件边与 checkpoint |
| 06 | `06_三层记忆.ipynb` | 工作、会话与长期记忆 |
| 07 | `07_Agentic_RAG.ipynb` | 向量检索与自主检索 Agent |
| 08 | `08_多Agent协作.ipynb` | Supervisor 写作团队 |
| 09 | `09_评估与可观测性.ipynb` | Eval、Trace 与可靠性报告 |
| 10 | `10_API安全与部署.ipynb` | FastAPI、SSE、安全与成本路由 |
| 11 | `11_作品集项目与验收.ipynb` | 项目化、测试、部署与毕业验收 |

每课都按零基础节奏组织：

- 先用一个不调用模型的“最小热身”立即看到结果；
- 每课只要求完成三件事，并提供四个以内的术语卡片；
- 大段代码拆成多个小单元格，每格先说明输入、输出和观察重点；
- 第一次学习只要求运行和理解主流程，工程细节留到第二遍；
- 最后提供常见问题、练习、最低完成标准和一句话回顾。

## 快速开始

要求 Python 3.11+。

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
$env:DASHSCOPE_API_KEY="你的百炼 API Key"
jupyter lab
```

从 `00_环境安装与配置.ipynb` 开始，按编号学习。默认模型为 `qwen-plus`，默认使用百炼北京地域 OpenAI 兼容入口。Notebook 会通过 `python-dotenv` 自动读取项目根目录的 `.env`。

第一次使用建议在项目根目录注册虚拟环境为 Jupyter 内核：

```powershell
python -m ipykernel install --user --name agent-engineering-lab --display-name "Agent Engineering Lab"
```

随后在每个 Notebook 右上角选择 `Agent Engineering Lab` 内核。

可选配置：

```dotenv
DASHSCOPE_API_KEY="你的百炼 API Key"
BAILIAN_BASE_URL="https://dashscope.aliyuncs.com/compatible-mode/v1"
BAILIAN_MODEL="qwen-plus"
BAILIAN_EMBEDDING_MODEL="text-embedding-v4"
```

可以复制 `.env.example` 为 `.env` 后填写真实值。`.env` 已被 Git 忽略，不会提交到 GitHub。

## 安全说明

- 不要把 API Key 写入 Notebook 或提交到 Git。
- 文件系统 MCP 被限制在专用工作目录内，但生产部署仍需加入认证、租户隔离和审计。
- Notebook 中的 Prompt Injection 检查仅用于教学，不能代替权限控制、输入隔离和人工确认。
- 天气、汇率及 Wikipedia 接口适合学习；生产项目应选择具有正式 SLA 的数据服务。

## 项目状态

当前版本提供分课 Notebook 与完整母版。Notebook 为教学用途；学习完成后，建议选一个主题进一步拆成独立 Python 包、测试与部署项目。

