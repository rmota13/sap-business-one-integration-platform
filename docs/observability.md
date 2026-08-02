# Observabilidade

## Objetivos

A plataforma precisa responder rapidamente:

- Qual pedido falhou?
- Em qual etapa?
- A falha é temporária ou de negócio?
- Quantas tentativas ocorreram?
- Algum documento foi criado no SAP?
- O registro pode ser reprocessado com segurança?

## Padrão de log

Cada execução carrega um `correlation_id` e registra:

- canal;
- identificador externo;
- etapa;
- status;
- tentativa;
- duração;
- código de erro sanitizado;
- documentos SAP relacionados.

## Estados sugeridos

`received → validated → customer_resolved → order_created → down_payment_created → incoming_payment_created → completed`

Registros também podem assumir `retrying`, `quarantined` ou `failed_terminal`.

## Métricas

- Pedidos processados por canal.
- Taxa de sucesso e falha.
- Tempo médio por etapa.
- Tamanho da fila e da quarentena.
- Retries esgotados.
- Taxa de matching da conciliação.
- Divergência financeira por motivo.

## Alertas

O sucesso é registrado, mas não gera notificação individual. Alertas são reservados para crescimento da quarentena, falha terminal, indisponibilidade do ERP, esgotamento de retry e divergência financeira acima da tolerância.
