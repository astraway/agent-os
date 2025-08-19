# Tech Stack

## Context

Global tech stack defaults for Agent OS projects, overridable in project-specific `.agent-os/product/tech-stack.md`.

- App Framework: FastAPI latest
- Language: Python 3.11+
- Data Validation: Pydantic v2
- Primary Database: SQLite (local development)
- ORM: SQLModel 
- AI Tools: FastMCP
- AI Framework: LangChain latest
- AI Workflow: LangGraph for complex chains
- AI Evaluation: OpenEvals for model testing
- Local LLM: Qwen3-Coder via Qwen Code CLI
- Model Format: GGUF quantized models
- Asset Storage: Amazon S3
- Production Environment: main branch
- Package Management: uv (preferred over pip for 10-100x faster performance)