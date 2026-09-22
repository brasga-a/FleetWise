# 02 — User Stories

As User Stories descrevem necessidades do ponto de vista de quem utiliza ou se beneficia da solução.

## US01 — Consolidar custos

**Como gestor de frota, quero visualizar todos os custos da operação em um único ambiente para compreender o custo total da frota.**

### Resposta proposta
O sistema armazenará despesas normalizadas por categoria, veículo, período e origem, permitindo agregações e visualizações consolidadas.

---

## US02 — Importar diferentes fontes

**Como gestor de frota, quero enviar planilhas, PDFs, imagens e outros documentos para evitar o cadastro manual de cada despesa.**

### Resposta proposta
A camada de ingestão reconhecerá o formato recebido e encaminhará o conteúdo para o mecanismo adequado de extração.

---

## US03 — Identificar desperdícios

**Como gestor de frota, quero identificar quais categorias e veículos possuem maior impacto financeiro para priorizar oportunidades de redução de custos.**

### Resposta proposta
O módulo de diagnóstico calculará indicadores e desvios em relação ao histórico, veículos semelhantes e benchmarks disponíveis.

---

## US04 — Comparar benchmarks

**Como gestor de frota, quero comparar meus indicadores com referências para identificar custos fora do comportamento esperado.**

### Resposta proposta
Cada indicador poderá possuir uma referência e um intervalo esperado. Quando o resultado exceder os limites definidos, o sistema sinalizará a ocorrência para análise.

---

## US05 — Recomendações

**Como gestor de frota, quero receber recomendações baseadas no diagnóstico para saber quais ações devo investigar primeiro.**

### Resposta proposta
As recomendações serão geradas a partir de regras de negócio, indicadores e contexto da operação. IA generativa poderá ajudar na explicação, mas não será responsável pelos cálculos financeiros.

---

## US06 — Impacto financeiro

**Como CFO, quero visualizar a economia potencial em reais para compreender o impacto financeiro das oportunidades encontradas.**

### Resposta proposta
O sistema apresentará estimativas acompanhadas das premissas utilizadas no cálculo.

---

## US07 — Comparação de fretes

**Como gestor de frota, quero comparar alternativas de frete para identificar quais possuem maior adequação às necessidades da operação.**

### Resposta proposta
As alternativas serão avaliadas utilizando variáveis como custo, distância, prazo, pedágio, capacidade, consumo e histórico.

Enquanto não houver dados históricos rotulados suficientes para calibrar probabilidades, o resultado será apresentado como **score de adequação**, e não como probabilidade estatística.

## Critérios gerais de aceite

Uma User Story será considerada atendida quando:

- sua entrada de dados estiver definida;
- existir uma regra clara de processamento;
- a saída esperada estiver especificada;
- for possível relacioná-la a um componente da arquitetura;
- o resultado puder ser explicado ao usuário.
