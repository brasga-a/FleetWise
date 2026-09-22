# 06 — Segurança, privacidade e LGPD

## Princípios

A solução trabalhará com informações operacionais e financeiras de empresas. Por isso, segurança não deve ser adicionada apenas no final do projeto.

## Autenticação e autorização

A arquitetura deverá prever:

- autenticação de usuários;
- autorização baseada em permissões;
- separação entre empresas;
- princípio do menor privilégio.

## Isolamento de dados

Um usuário de uma empresa não deverá conseguir consultar informações pertencentes a outra organização.

Toda consulta deverá possuir contexto de empresa ou tenant validado pelo backend.

## Proteção de arquivos

Uploads deverão possuir:

- validação de formato;
- limites de tamanho;
- nomes internos seguros;
- armazenamento não público;
- análise de conteúdo quando necessário.

## Integridade

Dados utilizados em diagnósticos deverão manter:

- origem;
- data de ingestão;
- histórico de processamento;
- status de validação.

Isso permite rastrear de onde uma recomendação surgiu.

## LGPD

O projeto deverá considerar, no mínimo:

- **finalidade:** coletar apenas dados necessários ao serviço;
- **adequação:** utilizar os dados de acordo com a finalidade informada;
- **necessidade:** evitar coleta excessiva;
- **segurança:** proteger acesso e armazenamento;
- **transparência:** deixar claro como os dados são utilizados.

## IA e privacidade

Antes de enviar dados para APIs externas de IA, será necessário avaliar:

- quais campos estão sendo compartilhados;
- se existem dados pessoais ou confidenciais;
- política de retenção do fornecedor;
- possibilidade de anonimização;
- necessidade real de utilizar serviço externo.

Sempre que possível, cálculos e regras de negócio permanecerão em componentes determinísticos controlados pela aplicação.
