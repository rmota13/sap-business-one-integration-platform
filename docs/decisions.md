# Architecture Decision Records

## ADR-001: n8n como orquestrador

**Decisão:** usar n8n para webhooks, polling, agendamento, filas, controle do fluxo e integração operacional.

**Consequência:** maior velocidade de entrega sem concentrar regras de negócio sensíveis dentro dos workflows. A lógica principal permanece em serviços e contratos bem definidos.

## ADR-002: Service Layer como fronteira de escrita

**Decisão:** toda criação de documentos no SAP Business One passa pelo Service Layer.

**Motivo:** preservar validações da aplicação, reduzir risco de inconsistência e evitar escrita direta nas tabelas transacionais.

## ADR-003: banco de integração separado

**Decisão:** manter estado, logs, idempotência, staging e quarentena fora da base transacional do ERP.

**Consequência:** maior auditabilidade e reprocessamento seguro, sem transformar o SAP em banco de controle da integração.

## ADR-004: idempotência por chave externa

**Decisão:** usar a combinação canal + identificador externo como chave lógica única.

**Motivo:** webhooks podem ser reenviados e polling pode se sobrepor. Repetir a chamada não pode gerar um segundo documento.

## ADR-005: feature flags

**Decisão:** ativar canais e etapas financeiras progressivamente por configuração.

**Consequência:** rollback rápido sem interromper os canais já estáveis.

## ADR-006: quarentena de erros

**Decisão:** inconsistências não resolvíveis automaticamente são persistidas com contexto, payload sanitizado e correlation ID.

**Motivo:** impedir falha silenciosa e evitar retry infinito para erro de negócio.

## ADR-007: origem do pedido e liquidação separadas

**Decisão:** modelar separadamente o canal que originou a venda e o provedor responsável pela liquidação.

**Motivo:** em alguns cenários, a plataforma de loja e o gateway financeiro são empresas diferentes.

## ADR-008: conciliação como Fase 3

**Decisão:** implementar a conciliação após estabilizar a criação do pedido e o ciclo financeiro.

**Motivo:** o matching depende de referências consistentes produzidas pelas fases anteriores. Antecipar a conciliação aumentaria retrabalho e risco de falso positivo.
