# Documento de Especificação Funcional — Módulo de Atendimento e Faturamento ERP

## 1. Visão Geral do Módulo
Padronizar a entrada de pacientes/clientes, assegurando a validação de elegibilidade e amarração de procedimentos para faturamento automático sem inconsistências de tabela.

## 2. Requisitos Funcionais (RF)
* **RF01 - Validação de Convênio:** O sistema deve verificar a vigência do contrato da operadora e o rol de procedimentos autorizados antes de confirmar o agendamento.
* **RF02 - Parametrização por Subgrupo:** Todo procedimento clínico deve estar associado a um subgrupo específico para cálculo dinâmico do tempo de atendimento na grade de horários.
* **RF03 - Bloqueio de Faturamento Fora de Tabela:** O sistema deve impedir o fechamento de contas cujo valor cobrado divirja da tabela contratada sem aprovação de alçada de gerência.

## 3. Requisitos Não Funcionais (RNF)
* **RNF01 - Tempo de Resposta:** A busca de horários e especialidades no PWA/portal não deve exceder 2 segundos.
* **RNF02 - Rastreabilidade:** Toda alteração em tabelas de preços ou permissões de caixa geral deve gerar registro de log de auditoria com data, hora e usuário responsável.

## 4. Matriz de Critérios de Aceite
| ID | Cenário | Ação do Usuário | Resultado Esperado |
|---|---|---|---|
| CA01 | Agendamento via PWA | Usuário seleciona procedimento | Sistema aloca automaticamente o slot conforme tempo do subgrupo |
| CA02 | Fechamento de Conta | Faturista gera fatura com item não coberto | Sistema bloqueia envio e emite alerta de divergência de tabela |
