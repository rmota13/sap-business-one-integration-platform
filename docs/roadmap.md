# Roadmap

## Fase 1: Integração comercial

- [x] Fundação da arquitetura.
- [x] Adaptador do SAP Business One.
- [x] Banco de controle e idempotência.
- [x] Integração do primeiro marketplace.
- [x] Integração do segundo canal.
- [x] Criação e resolução de Business Partners.
- [x] Criação de pedidos de venda.
- [x] Quarentena e reprocessamento.
- [x] Cancelamento automatizado.
- [x] Monitoramento operacional.

## Fase 2: Integração financeira

- [x] Tabela de controle financeiro.
- [x] Mapeamento de cartão e meio de pagamento.
- [x] Camada de domínio e repositório.
- [x] Serviço de adiantamento.
- [x] Serviço de recebimento.
- [x] Endpoint de orquestração financeira.
- [x] Teste isolado dos documentos no ambiente de testes.
- [x] Teste end-to-end com pedido real.
- [x] Validação com o financeiro.
- [x] Teste de retomada e idempotência.
- [x] Feature flag para produção.
- [x] Entrega técnica concluída.
- [ ] Encerrar janela de rollout e estabilização produtiva.

## Fase 3: Conciliação

- [x] Arquitetura e modelo de staging definidos.
- [x] Separação entre origem do pedido e origem da liquidação.
- [ ] Confirmar contratos de API ou arquivos por provedor.
- [ ] Implementar ingestão de liquidações.
- [ ] Implementar matching e tolerâncias.
- [ ] Classificar taxas e divergências.
- [ ] Integrar baixa ou ajuste ao SAP.
- [ ] Criar alertas de exceção.
- [ ] Homologar com o financeiro.
- [ ] Rollout produtivo controlado.

## Evoluções futuras

- Métricas de SLA por canal.
- Painel executivo de integrações.
- Gestão visual de reprocessamentos.
- Novos conectores.
- Configuração por empresa e arquitetura multi-tenant.
