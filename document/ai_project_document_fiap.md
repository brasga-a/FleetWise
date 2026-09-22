<img src="../assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Administração Paulista" border="0" width="30%" height="30%">

# AI Project Document — Sprint 1

## FleetWise

Este documento complementa o [README principal](../README.md). O README concentra a visão geral do projeto; os documentos técnicos em document/ detalham cada área.

## 1. Introdução

### 1.1 Escopo

O FleetWise propõe uma plataforma para consolidação, diagnóstico e redução de custos de frota.

O problema abordado é a fragmentação de dados de combustível, manutenção, pedágio, multas, impostos e fretes em diferentes fontes e formatos.

A Sprint 1 possui caráter de planejamento. Não existe requisito de modelo treinado ou aplicação funcional.

### 1.2 Solução proposta

A solução deverá receber diferentes fontes de dados, normalizá-las, armazená-las em uma estrutura comum e utilizar regras de negócio, indicadores, benchmarks e modelos analíticos para produzir diagnósticos e recomendações.

Leia: [Problema, contexto e usuários](01-problema-e-usuarios.md)

## 2. Visão geral

### 2.1 Objetivos

- consolidar custos;
- identificar possíveis ineficiências;
- comparar indicadores;
- estimar oportunidades de economia;
- orientar o usuário sobre dados ausentes;
- apresentar recomendações acionáveis.

### 2.2 Público-alvo

- Gestor de Frota;
- CFO / Liderança;
- Sem Parar Empresas.

### 2.3 User Stories

As histórias escolhidas e suas respostas propostas estão documentadas em [User Stories](02-user-stories.md).

## 3. Desenvolvimento proposto

### 3.1 Dados

A solução poderá receber CSV, XLSX, PDFs, imagens, textos, extratos e, futuramente, APIs.

Leia: [Dados, ingestão e normalização](03-dados-e-ingestao.md)

### 3.2 Tecnologias

Stack inicial sugerida:

- React + TypeScript;
- Python + FastAPI;
- PostgreSQL;
- Pandas;
- Scikit-learn;
- Docker;
- GitHub Actions.

### 3.3 Modelagem e IA

A estratégia proposta combina:

- regras determinísticas;
- análise estatística;
- modelos de ML quando justificados;
- IA generativa para extração e explicação.

Cálculos financeiros não deverão depender diretamente de respostas generativas.

Leia: [Diagnóstico, regras de negócio e IA](04-diagnostico-e-ia.md)

### 3.4 Arquitetura

A aplicação será dividida em frontend, API, ingestão, analytics, recomendações e persistência.

Leia: [Arquitetura da solução](05-arquitetura.md)

## 4. Segurança

O projeto prevê autenticação, autorização, isolamento de dados, rastreabilidade e princípios de LGPD.

Leia: [Segurança, privacidade e LGPD](06-seguranca-e-lgpd.md)

## 5. Resultados esperados

Como esta é a Sprint 1, não existem resultados experimentais ou métricas de modelo.

Os resultados esperados para as próximas Sprints incluem:

- ingestão de dados simulados;
- cálculo de KPIs;
- comparação de benchmarks;
- identificação de sinais de ineficiência;
- scoring de alternativas;
- dashboard e relatório.

## 6. Trabalhos futuros

O desenvolvimento será realizado incrementalmente, começando pela fundação de dados e backend e avançando para analytics, IA e interface.

Leia: [Roadmap e organização](07-roadmap.md)

## 7. Índice técnico

- [Problema, contexto e usuários](01-problema-e-usuarios.md)
- [User Stories](02-user-stories.md)
- [Dados, ingestão e normalização](03-dados-e-ingestao.md)
- [Diagnóstico, regras de negócio e IA](04-diagnostico-e-ia.md)
- [Arquitetura](05-arquitetura.md)
- [Segurança e LGPD](06-seguranca-e-lgpd.md)
- [Roadmap](07-roadmap.md)
