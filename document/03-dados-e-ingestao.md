# 03 — Dados, ingestão e normalização

## Fontes previstas

A solução poderá receber:

- CSV;
- XLSX;
- PDFs;
- imagens e prints;
- textos;
- extratos;
- dados enviados por API em etapas futuras.

## Categorias iniciais

- combustível;
- manutenção;
- pedágio;
- multas;
- impostos;
- seguros;
- fretes;
- custos administrativos.

## Exemplo de registro normalizado

```json
{
  "vehicle_id": "VH001",
  "occurred_at": "2026-09-01",
  "category": "fuel",
  "amount": 520.40,
  "distance_km": 840,
  "fuel_liters": 110,
  "source": "spreadsheet"
}
```

## Pipeline de ingestão

```text
Arquivo / entrada
      ↓
Detecção de formato
      ↓
Extração
      ↓
Validação
      ↓
Classificação
      ↓
Normalização
      ↓
Persistência
```

### Dados estruturados

CSV, XLSX e JSON podem ser convertidos diretamente para o schema interno após validação.

### Dados não estruturados

PDFs e imagens podem exigir OCR ou modelos multimodais para extrair campos relevantes.

O resultado extraído deverá passar por validação antes de ser considerado dado confiável.

## Estratégia de qualidade

Cada registro poderá possuir metadados como:

- origem;
- data de importação;
- nível de confiança;
- campos ausentes;
- status de validação.

## Dados incompletos

A ausência de dados não impedirá necessariamente o diagnóstico.

O sistema deverá:

1. calcular o que for possível com os campos disponíveis;
2. indicar quais resultados possuem menor confiabilidade;
3. informar quais dados adicionais melhorariam a análise;
4. recalcular os indicadores quando novas informações forem fornecidas.

## Dataset simulado

Durante as primeiras Sprints, o grupo poderá gerar dados simulados de empresas com:

- tamanhos de frota diferentes;
- perfis de consumo diferentes;
- veículos eficientes e ineficientes;
- cenários com dados completos e incompletos.

Esses cenários permitirão validar regras antes da disponibilidade de dados reais.
