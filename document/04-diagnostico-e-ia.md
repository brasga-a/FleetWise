# 04 — Diagnóstico, regras de negócio e IA

## Princípio

O sistema será híbrido:

```text
Dados normalizados
       +
Regras de negócio
       +
Modelos estatísticos / ML
       +
IA generativa para explicação
       ↓
Diagnóstico e recomendações
```

IA generativa não será utilizada como fonte direta de cálculos financeiros.

## Indicadores iniciais

- custo total da frota;
- custo por veículo;
- custo por quilômetro;
- consumo médio;
- custo de combustível por km;
- custo de manutenção por km;
- custo de pedágio por km;
- quantidade e custo de multas;
- custo médio por frete.

## Detecção de ineficiência

Exemplo:

```text
Veículo VH001

Combustível/km da empresa: R$ 0,82
Referência:                 R$ 0,64
Desvio:                     +28%
```

O sistema não deverá concluir automaticamente que existe desperdício. O resultado será tratado como um **sinal para investigação**, pois diferenças podem ser justificadas por rota, carga, veículo ou outras condições operacionais.

## Benchmarks

Podem vir de:

1. histórico da própria empresa;
2. veículos semelhantes da mesma frota;
3. dados agregados;
4. referências públicas;
5. dados fornecidos pela Sem Parar.

Cada benchmark deverá registrar sua origem e contexto.

## Avaliação de fretes

Variáveis possíveis:

- preço;
- distância;
- prazo;
- pedágio;
- consumo estimado;
- capacidade;
- histórico de atrasos;
- restrições de operação.

Fluxo:

```text
Dados do frete
     +
Regras obrigatórias
     ↓
Filtragem de opções inválidas
     ↓
Modelo / função de scoring
     ↓
Score de adequação
     ↓
Ranking explicado
```

Exemplo:

| Opção | Score | Observação |
|---|---:|---|
| Frete A | 0,82 | menor custo e prazo aceitável |
| Frete B | 0,71 | prazo melhor, custo superior |
| Frete C | 0,54 | custo elevado para o cenário |

## Onde IA pode ser útil

### Extração
Interpretar documentos e transformar conteúdo em campos estruturados.

### Classificação
Classificar despesas automaticamente.

### Detecção de anomalias
Identificar registros muito diferentes do padrão histórico.

### Recomendação
Relacionar diagnóstico, regras de negócio e possíveis ações.

### Explicação
Gerar textos claros para gestores e liderança com base em resultados já calculados.

## Modelos

Nesta fase, não há modelo definido como obrigatório.

A implementação poderá começar com:

- regras determinísticas;
- modelos estatísticos simples;
- Scikit-learn;
- modelos open source especializados;
- soluções mais experimentais, como arquiteturas probabilísticas, apenas se houver dados e métrica capazes de justificar seu uso.

A escolha do modelo deverá ser consequência do problema e dos dados, não o contrário.
