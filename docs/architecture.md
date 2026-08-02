# Arquitetura

## Princípios

A plataforma separa conectores, orquestração, regras de domínio, persistência de controle e integração com o ERP. O objetivo é permitir que novos canais sejam adicionados sem replicar regras críticas do SAP Business One.

## Componentes

| Componente | Responsabilidade |
|---|---|
| Marketplace Connectors | Receber eventos e consultar os dados completos de cada canal |
| Integration Orchestrator | Coordenar etapas, filas, retries, feature flags e reprocessamentos |
| Validation Layer | Validar schema, campos obrigatórios e consistência mínima |
| Domain Services | Aplicar regras de cliente, pedido, pagamento e conciliação |
| SAP Adapter | Gerenciar autenticação, sessão e contratos com o Service Layer |
| Integration Database | Manter estado, idempotência, staging, logs e quarentena |
| Monitoring | Consolidar métricas, logs e alertas operacionais |

## Fluxo comercial

```mermaid
sequenceDiagram
    participant C as Canal
    participant O as Orquestrador
    participant D as Domínio
    participant S as SAP Service Layer
    participant B as Banco de integração

    C->>O: Evento do pedido
    O->>C: Consulta dados completos
    O->>D: Payload normalizado
    D->>B: Reserva chave de idempotência
    D->>S: Resolve ou cria Business Partner
    D->>S: Cria pedido de venda
    S-->>D: DocEntry e DocNum
    D->>B: Grava resultado e auditoria
```

## Fluxo financeiro

```mermaid
sequenceDiagram
    participant O as Orquestrador
    participant F as Serviço financeiro
    participant S as SAP Service Layer
    participant B as Banco de integração

    O->>F: Pedido criado no SAP
    F->>B: Resolve meio de pagamento
    F->>S: Cria adiantamento
    S-->>F: Documento criado
    F->>S: Cria recebimento
    S-->>F: Recebimento confirmado
    F->>B: Registra ciclo financeiro concluído
```

## Conciliação

A conciliação é uma fase separada porque a origem do pedido e a origem da liquidação podem ser sistemas diferentes. Os dados externos pousam em staging, passam por normalização e matching e somente exceções exigem ação humana.
