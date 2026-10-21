# 11 - AGENDA (Appione)

> **Documentação de Arquitetura, Regras de Produto e Guia Operacional da Plataforma AGENDA (Appione)**

Repositório dedicado às especificações do **Appione**, SaaS *whitelabel* de gestão de clínicas de saúde e psicologia.

---

## 📚 Documentos Disponíveis

- **[Guia Operacional e Regras de Produto](agenda-product-rules-and-operational-guide.md)** (`agenda-product-rules-and-operational-guide.md`)
  - Perfis de usuário (Recepcionista, Profissional, Administrador de Clínica, Administrador da Plataforma)
  - Regras de negócio puras (agendamentos, faltas, cancelamentos, convênios)
  - Diagramas C4 de arquitetura e fluxogramas BPMN/Mermaid
  - Procedimentos operacionais e rotas de navegação
- **[Visão Geral do Produto e Topologia](00%20-%20Visão%20Geral%20do%20Appione%20(AGENDA).md)** (`00 - Visão Geral do Appione (AGENDA).md`)
  - Stack tecnológico: React 19, Tailwind CSS v4, Motion, Vite, Cloudflare Workers, Cloudflare D1, KV
  - Topologia da arquitetura monorepo e modos de persistência (IndexedDB vs Cloudflare D1)
- **[Arquitetura e Engenharia Cloudflare](01%20-%20Arquitetura,%20Tecnologias%20e%20Cloudflare.md)** (`01 - Arquitetura, Tecnologias e Cloudflare.md`)
  - Camadas arquiteturais no frontend (Injeção de dependências e repositórios reativos observáveis)
  - Borda Cloudflare, Workers Functions, D1 sharding por clínica (`DB_CLINIC`) e plataforma (`DB_PLATFORM`)
- **[Cópia Docs](docs/agenda-product-rules-and-operational-guide.md)** (`docs/agenda-product-rules-and-operational-guide.md`)

---

## 🛠️ Tecnologias

- **Frontend:** React 19, Tailwind CSS v4, Motion, Vite, Vitest, Playwright
- **Backend / Borda:** Cloudflare Workers, Pages Functions
- **Banco de Dados:** Cloudflare D1 (SQLite na borda), Cloudflare KV, IndexedDB (desenvolvimento/offline)
- **Design / Whitelabel:** Multi-tenant dinâmico por marca
