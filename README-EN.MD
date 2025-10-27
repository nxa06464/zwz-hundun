## Concept
The **Chaos MVC Pattern** is a discrete, plug-and-play development and deployment approach that uses AI as nodes to achieve unified invocation and deployment of discrete functional modules. The goal is to enable rapid integration of functionalities with minimal code development. New features only need to be registered to be recognized and invoked by the system.

**Developer Roles:**
- **Frontend**: Responsible for View development.
- **Backend**: Responsible for Controller and Model development.

The two groups can develop independently without communication or planning.

---

## Core Principles
- **Plug-and-Play**: Modules can be recognized by the system immediately after registration.
- **Unified Protocol**:
  - Frontend request and response formats are standardized (e.g., JSON).
  - MCP (Model Control Protocol) follows a unified input-output structure (e.g., JSON).
- **Language Independence**: Backend Controllers and Models do not depend on specific languages or frameworks; they only need to implement an MCP Server.

---

## Development Model
### Frontend
- Follows a unified request pattern; all requests and responses use a consistent format (e.g., JSON).

### Backend
- Controller receives requests from the Frontend, invokes the corresponding AI Agent or MCP.
- Agents specify MCP Servers and are not limited to a single MCP.
- Executes workflows, returns results to the Controller, which then sends them back to the Frontend.

---

## Development Workflow
Options:
- Frontend develops Views and provides standard Request-Response documentation. Backend implements Controllers based on the documentation.
- Backend develops MCP and Controllers, provides standard invocation documentation. Frontend implements corresponding Views based on the documentation.

---

## System Architecture
### Frontend
- **AI LLM Router**: Connects multiple Backend Controllers.
- The Router routes requests to the designated Controller and passes results to the corresponding View (e.g., JSP, PHP).

### Backend
- **Controller**:
  - Receives requests.
  - Invokes AI Agent or MCP.
  - Returns results to the Frontend.
- **Model**:
  - Executes workflows via MCP or Agent.

---

## Features
- **Modularity**: Functional modules are independent and usable upon registration.
- **Distributed**: AI Router and MCP can be deployed across multiple nodes.
- **Low Coupling**: Frontend and Backend interact through standard protocols without direct communication.
