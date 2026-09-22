# 07 — Roadmap e organização do projeto

## Sprint 1 — Planejamento

Objetivo: criar o blueprint técnico.

Entregas:

- problema e usuários;
- User Stories;
- estrutura de dados;
- estratégia de ingestão;
- diagnóstico;
- arquitetura;
- segurança;
- planejamento.

## Sprint 2 — Fundação

Objetivo: estabelecer a base técnica.

Possíveis atividades:

- criar schema do PostgreSQL;
- estruturar API;
- criar dataset simulado;
- implementar ingestão de CSV/XLSX;
- iniciar autenticação.

## Sprint 3 — Diagnóstico

Objetivo: transformar dados em indicadores.

Possíveis atividades:

- agregações;
- KPIs;
- regras de negócio;
- benchmarks internos;
- identificação de desvios.

## Sprint 4 — Inteligência

Objetivo: ampliar automação e análise.

Possíveis atividades:

- processamento de PDFs/imagens;
- classificação automática;
- detecção de anomalias;
- score de fretes;
- geração assistida de recomendações.

## Sprint 5 — Produto e demonstração

Objetivo: integrar a experiência.

Possíveis atividades:

- dashboard;
- relatórios;
- testes;
- refinamento de UX;
- integração dos módulos;
- preparação da apresentação.

## Divisão sugerida da equipe

| Pessoa | Área principal | Responsabilidades |
|---|---|---|
| 1 | Produto e User Stories | problema, usuários, requisitos e critérios |
| 2 | Dados | ingestão, schema, normalização e dataset |
| 3 | Analytics / IA | indicadores, benchmarks, scoring e recomendações |
| 4 | Arquitetura | backend, banco, segurança e integração |
| 5 | UX e documentação | dashboard, relatórios, README, vídeo e integração da entrega |

A divisão define responsáveis principais, não silos. Decisões que afetem contratos de dados e arquitetura devem ser revisadas pelo grupo.

## Kanban sugerido

Colunas:

```text
Backlog → Ready → In Progress → Review → Done
```

Cada card deve conter:

- descrição;
- responsável;
- critério de aceite;
- dependências;
- Sprint.
