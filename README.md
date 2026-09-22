# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href="https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Administração Paulista" border="0" width="40%" height="40%"></a>
</p>

# FleetWise

> Plataforma inteligente para diagnóstico, consolidação e redução de custos de frotas.

## Grupo

**Nome do grupo:** PREENCHER

## 👨‍🎓 Integrantes

- Nome do integrante 1
- Nome do integrante 2
- Nome do integrante 3
- Nome do integrante 4
- Nome do integrante 5

## 👩‍🏫 Professores

### Tutor(a)
- Sabrina Otoni

### Coordenador(a)
- PREENCHER

---

## 📜 Visão geral

O **FleetWise** é uma proposta de solução para apoiar gestores de frota e lideranças financeiras na compreensão do custo real de suas operações.

Dados de combustível, manutenção, pedágio, multas, impostos e fretes podem estar distribuídos entre planilhas, PDFs, imagens, extratos e sistemas diferentes. O FleetWise propõe receber essas informações, transformá-las em dados padronizados e gerar uma visão consolidada dos custos.

A partir dessa base, a solução poderá:

- consolidar despesas;
- calcular indicadores;
- comparar resultados com benchmarks;
- identificar possíveis ineficiências;
- estimar oportunidades de economia;
- recomendar próximos passos;
- comparar alternativas de frete por score de adequação;
- gerar visualizações para gestores e liderança.

> **Status atual:** Sprint 1 — planejamento e arquitetura.  
> Nesta etapa, o objetivo é documentar o projeto. Não existe implementação funcional obrigatória.

---

## 🎯 Problema

Empresas com frotas podem possuir os dados necessários para uma análise financeira, mas ainda assim ter dificuldade para responder rapidamente:

- Quanto custa a operação?
- Qual categoria representa maior gasto?
- Quais veículos apresentam comportamento fora do padrão?
- Quais despesas devem ser tratadas primeiro?
- Quanto uma ação pode economizar?
- Quais informações ainda faltam para melhorar o diagnóstico?

O objetivo do projeto é transformar dados fragmentados em **diagnóstico + prioridade + ação**.

---

## 👥 Usuários

| Perfil | Necessidade principal |
|---|---|
| Gestor de Frota | acompanhar custos, veículos, desperdícios e prioridades |
| CFO / Liderança | visualizar impacto financeiro e economia potencial |
| Sem Parar Empresas | identificar oportunidades e necessidades relevantes dos clientes |

Detalhamento: [Problema, contexto e usuários](document/01-problema-e-usuarios.md)

---

## 🧩 User Stories

As User Stories selecionadas para este exemplo são:

| ID | Necessidade |
|---|---|
| US01 | consolidar todos os custos da operação |
| US02 | importar dados de diferentes fontes |
| US03 | identificar gastos e possíveis desperdícios |
| US04 | comparar indicadores com benchmarks |
| US05 | receber recomendações baseadas no diagnóstico |
| US06 | visualizar economia potencial em reais |
| US07 | comparar alternativas de frete |

Detalhamento e resposta técnica de cada história: [User Stories](document/02-user-stories.md)

---

## 💡 Solução proposta

Fluxo principal:

~~~text
Entrada de dados
      ↓
Extração
      ↓
Validação e normalização
      ↓
PostgreSQL
      ↓
Indicadores e regras de negócio
      ↓
Benchmarks / modelos analíticos
      ↓
Diagnóstico
      ↓
Recomendações
      ↓
Dashboard / relatório
~~~

Arquivos estruturados, como CSV e XLSX, poderão ser processados diretamente.

PDFs, imagens e outros formatos não estruturados poderão utilizar OCR ou modelos de IA para extração, sempre com uma etapa posterior de validação.

Mais detalhes: [Dados, ingestão e normalização](document/03-dados-e-ingestao.md)

---

## 📊 Diagnóstico

Indicadores iniciais previstos:

- custo total da frota;
- custo por veículo;
- custo por quilômetro;
- consumo médio;
- combustível por km;
- manutenção por km;
- pedágio por km;
- quantidade e custo de multas;
- custo médio de frete.

Um valor fora da referência será apresentado como **sinal para investigação**, não como conclusão automática de desperdício.

Exemplo:

~~~text
Veículo VH001

Combustível/km da empresa: R$ 0,82
Referência:                 R$ 0,64
Desvio:                     +28%
~~~

Detalhes: [Diagnóstico, regras de negócio e IA](document/04-diagnostico-e-ia.md)

---

## 🚚 Avaliação de fretes

O projeto poderá utilizar uma combinação de regras de negócio e modelos analíticos:

~~~text
Dados do frete
     +
Regras obrigatórias
     ↓
Filtragem
     ↓
Modelo / função de scoring
     ↓
Score de adequação
     ↓
Ranking explicado
~~~

Variáveis possíveis:

- preço;
- prazo;
- distância;
- pedágio;
- capacidade;
- consumo;
- histórico de atrasos;
- restrições operacionais.

Sem histórico rotulado suficiente, o sistema deverá apresentar **score de adequação**, evitando chamar o resultado de probabilidade estatística sem calibração.

---

## 🤖 IA e Data Science

IA será aplicada apenas onde houver ganho técnico claro.

Possíveis usos:

- extração de PDFs e imagens;
- classificação de despesas;
- detecção de padrões;
- identificação de anomalias;
- scoring;
- geração de explicações e recomendações.

A arquitetura proposta é híbrida:

~~~text
Regras determinísticas
        +
Modelos estatísticos / ML
        +
IA generativa para explicação
~~~

A IA generativa não será responsável pelos cálculos financeiros.

Detalhes: [Diagnóstico, regras de negócio e IA](document/04-diagnostico-e-ia.md)

---

## 🏗️ Arquitetura

~~~text
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
~~~

Detalhes completos: [Arquitetura da solução](document/05-arquitetura.md)

---

## 🛠️ Stack proposta

| Camada | Tecnologia sugerida |
|---|---|
| Frontend | React + TypeScript |
| Backend | Python + FastAPI |
| Banco | PostgreSQL |
| Dados | Pandas |
| ML | Scikit-learn / modelos open source |
| Documentos | OCR / modelos multimodais quando necessário |
| Infraestrutura | Docker + GitHub Actions |

A stack poderá ser revisada nas próximas Sprints conforme requisitos e testes.

---

## 🔐 Segurança e privacidade

A proposta considera desde o início:

- autenticação;
- autorização;
- isolamento entre empresas;
- princípio do menor privilégio;
- validação de uploads;
- rastreabilidade dos dados;
- proteção de informações confidenciais;
- princípios de LGPD.

Detalhes: [Segurança, privacidade e LGPD](document/06-seguranca-e-lgpd.md)

---

## 🗺️ Roadmap

| Sprint | Objetivo |
|---|---|
| Sprint 1 | planejamento, User Stories, dados e arquitetura |
| Sprint 2 | banco, API, ingestão inicial e dataset simulado |
| Sprint 3 | indicadores, regras e benchmarks |
| Sprint 4 | automação, IA, scoring e recomendações |
| Sprint 5 | dashboard, integração, testes e apresentação |

Planejamento completo: [Roadmap e organização](document/07-roadmap.md)

---

## 👨‍💻 Divisão da equipe

| Pessoa | Área principal |
|---|---|
| Pessoa 1 | Produto, problema e User Stories |
| Pessoa 2 | Dados, ingestão e normalização |
| Pessoa 3 | Analytics, IA, benchmarks e scoring |
| Pessoa 4 | Arquitetura, backend, banco e segurança |
| Pessoa 5 | UX, documentação, vídeo e integração da entrega |

---

## 📚 Documentação

O README é o documento principal do projeto. Os arquivos abaixo aprofundam cada decisão técnica:

1. [Problema, contexto e usuários](document/01-problema-e-usuarios.md)
2. [User Stories](document/02-user-stories.md)
3. [Dados, ingestão e normalização](document/03-dados-e-ingestao.md)
4. [Diagnóstico, regras de negócio e IA](document/04-diagnostico-e-ia.md)
5. [Arquitetura da solução](document/05-arquitetura.md)
6. [Segurança, privacidade e LGPD](document/06-seguranca-e-lgpd.md)
7. [Roadmap e organização](document/07-roadmap.md)
8. [Documento acadêmico FIAP](document/ai_project_document_fiap.md)

---

## 📁 Estrutura de pastas

~~~text
.
├── .github/
├── assets/
├── config/
├── document/
│   ├── 01-problema-e-usuarios.md
│   ├── 02-user-stories.md
│   ├── 03-dados-e-ingestao.md
│   ├── 04-diagnostico-e-ia.md
│   ├── 05-arquitetura.md
│   ├── 06-seguranca-e-lgpd.md
│   ├── 07-roadmap.md
│   ├── ai_project_document_fiap.md
│   └── other/
├── scripts/
├── src/
└── README.md
~~~

### Pastas

- **assets:** imagens e recursos visuais.
- **config:** configurações futuras do projeto.
- **document:** documentação técnica e acadêmica.
- **scripts:** scripts auxiliares futuros.
- **src:** código-fonte das próximas Sprints.
- **README.md:** documento principal e ponto de entrada do projeto.

---

## 🔧 Como executar

A Sprint 1 não possui código funcional obrigatório.

Quando a implementação começar, esta seção deverá ser atualizada com:

- versões das ferramentas;
- instalação;
- variáveis de ambiente;
- banco de dados;
- execução do backend;
- execução do frontend;
- testes.

---

## 🎥 Vídeo

Link da apresentação:

ADICIONAR_LINK_DO_VIDEO_NAO_LISTADO

O vídeo deverá apresentar:

1. problema;
2. User Stories;
3. solução proposta;
4. dados utilizados;
5. arquitetura;
6. próximos passos.

---

## ✅ Critérios de sucesso

O projeto pretende chegar a um protótipo capaz de:

1. receber diferentes fontes de dados;
2. transformá-las em uma estrutura comum;
3. consolidar custos;
4. calcular indicadores;
5. identificar sinais de ineficiência;
6. comparar benchmarks;
7. estimar oportunidades financeiras;
8. recomendar próximos passos;
9. indicar quais dados adicionais podem melhorar o diagnóstico.

---

## 🗃 Histórico

### 0.1.0 — Sprint 1

- definição do problema;
- User Stories;
- proposta de dados;
- diagnóstico;
- arquitetura;
- segurança;
- roadmap;
- documentação técnica inicial.

---

## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/agodoi/template">MODELO GIT FIAP</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">FIAP</a> está licenciado sob <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>
