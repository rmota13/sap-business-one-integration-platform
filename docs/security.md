# Segurança e sanitização

## Controles da arquitetura

- Credenciais resolvidas por variáveis de ambiente ou cofre de segredos.
- Privilégio mínimo para usuários de banco, APIs e ERP.
- Escrita no SAP exclusivamente pelo Service Layer.
- Validação de assinatura, segredo compartilhado ou token nos webhooks.
- Janela de tempo para reduzir risco de replay.
- Idempotência para impedir processamento duplicado.
- Mascaramento de CPF, CNPJ, e-mail, endereço e dados financeiros em logs.
- Separação entre ambientes de desenvolvimento, homologação e produção.

## O que foi removido da versão pública

- Tokens, senhas, cookies e credenciais.
- URLs, IPs, domínios e nomes de servidores internos.
- CNPJ, CPF, nomes de clientes e dados fiscais.
- Nomes reais de bancos e tabelas de controle proprietárias.
- Payloads produtivos e workflows com referências internas.
- Regras fiscais, comerciais e financeiras específicas da empresa.

## Publicação segura

Os exemplos usam canais, clientes e identificadores fictícios. Este repositório não deve receber exports brutos do n8n, dumps de banco, arquivos `.env`, logs reais ou capturas contendo dados operacionais.
