# 05 — Arquitetura da solução

## Visão geral

```text
                    ┌─────────────────────┐
                    │      Frontend       │
                    │ Dashboard / Upload  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │         API         │
                    └──────────┬──────────┘
                               │
             ┌─────────────────┼──────────────────┐
             │                 │                  │
             ▼                 ▼                  ▼
     ┌──────────────┐  ┌──────────────┐  ┌────────────────┐
     │   Ingestão   │  │  Analytics   │  │ Recomendações  │
     └──────┬───────┘  └──────┬───────┘  └───────┬────────┘
            │                 │                  │
            └─────────────────┼──────────────────┘
                              ▼
                     ┌──────────────────┐
                     │    PostgreSQL    │
                     └──────────────────┘
```

## Componentes

### Frontend

Responsabilidades:

- autenticação;
- upload de arquivos;
- acompanhamento de processamento;
- dashboards;
- visualização de recomendações;
- relatórios.

**Tecnologia sugerida:** React + TypeScript.

### API

Responsabilidades:

- receber requisições;
- validar permissões;
- coordenar serviços;
- expor dados para o frontend.

**Tecnologia sugerida:** Python + FastAPI.

### Serviço de ingestão

Responsabilidades:

- detectar formatos;
- extrair conteúdo;
- normalizar campos;
- validar registros;
- registrar origem.

### Analytics

Responsabilidades:

- agregações;
- indicadores;
- benchmarks;
- regras de negócio;
- scores;
- detecção de anomalias.

### Recomendações

Responsabilidades:

- transformar sinais do módulo Analytics em ações;
- aplicar regras;
- relacionar oportunidades ao contexto da empresa;
- gerar explicações.

### Banco de dados

**PostgreSQL** será o banco principal por causa da natureza relacional dos dados e da necessidade de agregações financeiras.

Entidades iniciais:

```text
Company
 ├── Fleet
 │    ├── Vehicle
 │    ├── Expense
 │    ├── Trip
 │    └── Maintenance
 ├── Freight
 ├── Diagnostic
 └── Recommendation
```

## Por que não MongoDB como banco principal?

A maior parte dos dados relevantes possui relações bem definidas e será utilizada em consultas analíticas, somas, agrupamentos e comparações.

Documentos brutos podem ser armazenados em object storage ou em uma área de ingestão, mas os dados normalizados devem preferencialmente seguir um schema relacional.

## Infraestrutura futura

Possíveis componentes:

- Docker;
- GitHub Actions;
- object storage para arquivos;
- fila para processamento assíncrono;
- PostgreSQL gerenciado;
- observabilidade e logs.

A infraestrutura definitiva será definida nas próximas Sprints.
