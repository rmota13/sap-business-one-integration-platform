# Case de portfólio: SAP Commerce Integration Platform

## Contexto

Uma operação industrial de médio porte vendia por diferentes canais digitais, mas dependia de lançamentos e conferências manuais para levar pedidos ao SAP Business One e registrar o ciclo financeiro.

## Meu papel

Atuei como arquiteto e desenvolvedor principal da solução, conduzindo levantamento, modelagem, integração, testes, deploy, observabilidade e sustentação. Também coordenei dependências com áreas de negócio, financeiro, parceiro SAP e infraestrutura externa.

## Solução

A plataforma integra canais de e-commerce ao SAP Business One por meio de n8n, APIs e Service Layer. O fluxo normaliza pedidos, valida dados, resolve o cliente, cria o pedido de venda e executa o módulo financeiro com adiantamento, recebimento e referência de transação.

A terceira fase adiciona conciliação real por API ou arquivo, comparando liquidações externas aos documentos esperados no ERP e encaminhando somente divergências para análise.

## Decisões relevantes

- Separar regras de domínio da orquestração visual.
- Implementar idempotência desde o primeiro webhook.
- Usar o Service Layer como única fronteira de escrita no ERP.
- Criar banco de integração para estado, staging e auditoria.
- Ativar o módulo financeiro por feature flag.
- Tratar conciliação como fase independente.
- Alertar apenas exceções.

## Impacto

- Redução de lançamento manual.
- Maior velocidade entre venda e registro no ERP.
- Menor risco de pedido e documento financeiro duplicado.
- Rastreabilidade ponta a ponta.
- Exposição e correção de inconsistências cadastrais históricas.
- Base pronta para escalar canais sem replicar regras do ERP.

## Competências demonstradas

Arquitetura de integração, SAP Business One, Service Layer, APIs REST, n8n, SQL Server, Python/FastAPI, modelagem de domínio, idempotência, observabilidade, gestão de exceções e tradução de regras financeiras em software.
