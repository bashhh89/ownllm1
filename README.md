# OwnLLM — Custom AnythingLLM Fork

<p align="center">
  <b>OwnLLM</b> is a customized fork of <a href="https://anythingllm.com">AnythingLLM</a> by Mintplex Labs, extended into a full-stack <b>AI-powered proposal generation &amp; business document platform</b>.
</p>

<p align="center">
  <a href="./LICENSE">
    <img src="https://img.shields.io/static/v1?label=license&message=MIT&color=white" alt="License">
  </a>
  &nbsp;|&nbsp;
  <a href="./OWNLLM.md">OwnLLM Feature Docs</a>
  &nbsp;|&nbsp;
  <a href="./DEPLOYMENT_GUIDE.md">Deployment Guide</a>
  &nbsp;|&nbsp;
  <a href="./BACKEND_API_REFERENCE.md">API Reference</a>
</p>

---

## What is OwnLLM?

OwnLLM takes the powerful open-source [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) core and adds a suite of custom features to turn it into a **proposal generation and business intelligence platform** — letting you chat with your documents, build AI agents, and produce client-ready proposals and exports, all within a private, self-hosted environment.

---

## ✨ Custom Features (OwnLLM Additions)

### 🗒️ Thread Notes — Rich Editor
Each workspace thread now has a full **BlockNote** rich-text editor alongside the AI chat, with:
- Headings, lists, tables, and code blocks
- Auto-save to the database
- AI can insert content directly into notes
- Dark-theme styling

### 📄 PDF Export with Branding
Export your thread notes to professionally branded PDFs:
- Custom logo, colours, and fonts stored per workspace
- Header/footer text and custom CSS overrides
- Powered by the `pdf_templates` database table

### 📦 Products Manager
Define products and services per workspace so the AI can reference real pricing when generating proposals:
- Name, Category, Price, and Pricing Type
- Description and deliverables
- Stored as a JSON field on the workspace

### 💰 Rate Card Manager
Define roles with hourly rates for time-and-materials proposals:
- Role name, Hourly rate, and Category
- Injected into the AI system prompt automatically

### 🧩 Smart Plugins
Per-workspace plugins with custom schemas stored in the `smart_plugins` table.

### 📁 Artifacts Storage
Store AI-generated code artifacts (name, code, language) in the `artifacts` table.

### 🔁 Deep-Clone Workspaces
Full workspace duplication including documents, settings, products, and rate cards.

### 🏢 Multi-Tenant / SaaS-Ready
EasyPanel-based multi-tenant deployment with per-client isolation support.

---

## 🏗️ Architecture

This monorepo is built on the AnythingLLM stack:

| Directory | Purpose |
|-----------|---------|
| `frontend/` | Vite + React UI |
| `server/` | Node.js Express API + Prisma ORM (SQLite) |
| `collector/` | Document processing service |
| `docker/` | Docker build configuration |
| `embed/` | Embeddable chat widget (submodule) |
| `browser-extension/` | Chrome extension (submodule) |
| `RAG_KB/` | RAG knowledge base for this fork's documentation |
| `pdf_export_api/` | PDF export microservice |
| `plans/` | Feature planning documents |

---

## 🛳️ Self-Hosting & Deployment

| Docker | EasyPanel | Bare Metal |
|--------|-----------|------------|
| `docker compose up` | See [EASYPANEL_MULTI_TENANT_SAAS.md](./EASYPANEL_MULTI_TENANT_SAAS.md) | See [BARE_METAL.md](./BARE_METAL.md) |

Full deployment walkthrough: **[DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md)**

---

## 🚀 Development Setup

```bash
# 1. Fill in required .env files across all services
yarn setup

# 2. Run the backend server (port 3001)
yarn dev:server

# 3. Run the frontend (port 3000)
yarn dev:frontend

# 4. Run the document collector
yarn dev:collector
```

> Ensure `server/.env.development` is populated before starting.

---

## 📚 Key Documentation

| Document | Description |
|----------|-------------|
| [OWNLLM.md](./OWNLLM.md) | Full custom feature reference |
| [BACKEND_API_REFERENCE.md](./BACKEND_API_REFERENCE.md) | REST API docs |
| [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md) | Step-by-step deployment |
| [TESTING_AND_DEPLOYMENT_GUIDE.md](./TESTING_AND_DEPLOYMENT_GUIDE.md) | QA & testing guide |
| [FEATURE_TOGGLES_REFERENCE.md](./FEATURE_TOGGLES_REFERENCE.md) | Feature flag reference |
| [PROJECT_COMPREHENSIVE_OVERVIEW.md](./PROJECT_COMPREHENSIVE_OVERVIEW.md) | Full project overview |
| [ANC_ARCHITECTURE_DIAGRAMS.md](./ANC_ARCHITECTURE_DIAGRAMS.md) | Architecture diagrams |
| [MCP_CATALOG_COMPLETE.md](./MCP_CATALOG_COMPLETE.md) | MCP server catalog |
| [RAG_KB/README.md](./RAG_KB/README.md) | RAG knowledge base index |

---

## 🗄️ Custom Database Migrations

| Migration | Purpose |
|-----------|---------|
| `20251211100317_add_thread_notes` | Added `notes` field to threads |
| `20251211122132_init_artifacts` | Artifacts table for code storage |
| `20251211181413_add_pdf_templates` | PDF branding templates |
| `20251211210436_add_brand_manager_fields` | Extended branding options |
| `20251211222000_add_smart_plugins` | Plugin system |
| `20251211224500_smart_plugins_unique_per_workspace` | Plugin uniqueness constraint |

---

## 🤝 Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 📄 License

MIT © Mintplex Labs / khaledbashir  
Based on [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) — MIT Licensed.
