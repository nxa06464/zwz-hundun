# 混沌MVC模式

## 概念
**混沌MVC模式**是一种离散、即插即用的开发和部署方式，以 **AI** 为节点，实现对离散功能模块的统一调用和部署，目标是通过最少的代码开发，实现功能的快速集成。新功能只需注册即可被系统认知和调用。

开发人员分为两组：
- **Frontend**：负责视图（View）开发。
- **Backend**：负责控制器（Controller）和模型（Model）开发。

两组可以独立开发，无需沟通计划。

---

## 核心原则
1. **即插即用**：模块注册后即可被系统识别。
2. **统一协议**：
   - Frontend 请求和响应格式统一（如 JSON）。
   - MCP（Model Control Protocol）遵循统一的输入输出结构（如 JSON）。
3. **语言无关性**：Backend Controller 和 Model 不依赖特定语言或框架，只需实现 MCP Server。

---

## 开发模式
### Frontend
- 遵循统一请求模式，所有请求和响应格式一致（例如 JSON）。
- 可以：
  - frontend开发 View，提供标准Request-Response文档。Backend根据文档实现Controller。
  - Backend开发MCP，Controller。提供標準的調用文檔，frontend根据文實現对应的 View。

### Backend
- Controller 接收 Frontend 请求，调用相应的 **AI Agent** 或 MCP。
- Agent 指定 MCP Server，不局限于某一特定 MCP。
- 执行工作流，返回结果给 Controller，再返回给 Frontend。

---

## 系统架构
### Frontend
- **AI LLM Router**：连接多个 Backend Controller。
- Router 将请求路由到指定 Controller，并将结果传递给对应 View（如 JSP、PHP 等）。

### Backend
- **Controller**：
  - 接收请求。
  - 调用 AI Agent 或 MCP。
  - 返回结果给 Frontend。
- **Model**：
  - 由 MCP 或 Agent 执行工作流。

---

## 特点
- **模块化**：功能模块独立，注册后即可使用。
- **分布式**：AI Router 和 MCP 可分布在多个节点。
- **低耦合**：Frontend 与 Backend 通过标准协议交互，无需直接沟通。
