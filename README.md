# Bailian Agent Engineering Lab

一套基于阿里云百炼模型的 Agent 工程学习实验室，覆盖从手写 Agent Loop 到工具调用、MCP、LangGraph、记忆、Agentic RAG、多 Agent、评估、可观测性、部署和安全的完整路线。

## 内容

- Python 异步、Pydantic v2 与最小 Agent Loop
- Function Calling：天气、汇率、待办、日志和搜索
- 参数校验、调用超时、未知工具与循环防护
- FastMCP 安全文件系统 Server
- LangGraph 周末旅行规划工作流
- 工作记忆、会话记忆与长期记忆
- 百炼 Embedding 与 Agentic RAG
- Supervisor 多 Agent 写作团队
- 评估、Trace 与可靠性报告
- FastAPI、SSE、Guardrails 与成本路由

## 快速开始

要求 Python 3.11+。

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
$env:DASHSCOPE_API_KEY="你的百炼 API Key"
jupyter lab
```

打开 `bailian_agent_engineering_lab.ipynb`，从上到下运行。默认模型为 `qwen-plus`，默认使用百炼北京地域 OpenAI 兼容入口。

可选配置：

```powershell
$env:BAILIAN_BASE_URL="https://dashscope.aliyuncs.com/compatible-mode/v1"
$env:BAILIAN_MODEL="qwen-plus"
$env:BAILIAN_EMBEDDING_MODEL="text-embedding-v4"
```

## 安全说明

- 不要把 API Key 写入 Notebook 或提交到 Git。
- 文件系统 MCP 被限制在专用工作目录内，但生产部署仍需加入认证、租户隔离和审计。
- Notebook 中的 Prompt Injection 检查仅用于教学，不能代替权限控制、输入隔离和人工确认。
- 天气、汇率及 Wikipedia 接口适合学习；生产项目应选择具有正式 SLA 的数据服务。

## 项目状态

当前版本是单 Notebook 教学实现。建议学习完成后，把各章节拆分为独立 Python 包、测试与部署项目。

