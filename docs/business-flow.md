# Fluxos de negócio

## Pedido

1. O canal informa um pedido pago.
2. O orquestrador busca os dados completos.
3. O payload é convertido para um modelo canônico.
4. A plataforma valida cliente, documento, endereço, itens e entrega.
5. O Business Partner é resolvido ou criado.
6. O Pedido de Venda é criado no SAP Business One.
7. O resultado é registrado com correlation ID.

## Ciclo financeiro

1. A plataforma identifica o meio de pagamento do canal.
2. Resolve o código correspondente no ERP.
3. Cria o adiantamento vinculado ao pedido.
4. Cria o recebimento e registra a referência da transação.
5. Atualiza o estado da integração de forma idempotente.

## Erro e reprocessamento

Falhas temporárias seguem retry limitado. Falhas de negócio ou inconsistências cadastrais são enviadas para quarentena. Após correção, o registro pode ser reprocessado sem criar documentos duplicados.

## Conciliação

1. Liquidações são capturadas por API ou arquivo.
2. Os dados são persistidos em staging.
3. O motor procura o pedido, o recebimento e o valor esperado.
4. Casos dentro da tolerância são conciliados automaticamente.
5. Taxas e diferenças são classificadas.
6. Somente divergências são enviadas para análise.
