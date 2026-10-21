---
title: AGENDA — Arquitetura e Engenharia Cloudflare
created: 2026-10-13
project: AGENDA
component: Architecture
status: active
tags:
  - projeto/agenda
  - engenharia
  - cloudflare-d1
  - react19
---

# 🛠️ AGENDA (Appione) — Arquitetura de Software e Infraestrutura Cloudflare

## 🏛️ Camadas Arquiteturais no Frontend

O frontend não utiliza gerenciadores de estado globais acoplados (como Redux ou Zustand). Em vez disso, adota **Injeção de Dependências com Repositórios Reativos Observáveis**:

```
[View (React 19)] 
       ↓ 
[Container (Gerenciador de Ciclo de Vida)]
       ↓ 
[View Models Segmentados (Apresentação)]
       ↓ 
[Domain Layer (Regras de Negócio Puras em TS)]
       ↓ 
[Repository (Acesso e Cache de Entidades)]
       ↓ 
[Data Source (HTTP API ou IndexedDB)]
```

### Princípios Chave:
1. **Regras de Negócio Puras:** A pasta `src/domain/` não contém código React nem efeitos colaterais de DOM.
2. **Whitelabel Dinâmico:** Tema, terminologia de saúde e logos são injetados em tempo de compilação/execução via `src/theme/saasBrand.ts`.
3. **Motion + Tailwind v4:** Animações fluidas a 60fps para o calendário com arrasto de agendamentos.

---

## ☁️ Backend & Borda Cloudflare

A infraestrutura roda 100% serverless na Cloudflare:
- **`wrangler.jsonc`:** Configuração do Worker `agenda` conectado via Workers Builds ao GitHub.
- **Workers Functions (`functions/`):** Handlers de rotas HTTP para endpoints RESTful (`/api/pacientes`, `/api/profissionais`, `/api/agendamentos`).
- **Cloudflare D1:**
  - `DB_PLATFORM`: Base compartilhada de governança e autenticação.
  - `DB_CLINIC`: Shards isolados por clínica cliente, garantindo isolamento total por LGPD.
- **KV Session:** Sessões de alta performance com baixa latência e rate-limiting ativo.
