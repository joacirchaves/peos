# Fluxo de Refinamento PEOS

Este fluxo transforma uma entrada de negócio em histórias prontas para desenvolvimento.

## 1. Entrada da demanda

A entrada pode ser uma ideia, dor do usuário, solicitação do negócio, oportunidade, problema operacional, melhoria técnica ou necessidade regulatória.

A demanda deve conter, no mínimo:

- Problema observado
- Público ou usuário impactado
- Contexto atual
- Resultado esperado
- Restrições conhecidas

## 2. Entendimento do problema

Antes de falar em solução, o time deve responder:

- Qual problema estamos resolvendo?
- Quem é impactado?
- Qual impacto atual?
- O que acontece se nada for feito?
- Como saberemos que a solução funcionou?

## 3. Definição da solução

A solução deve explicar o comportamento esperado do produto, sem misturar detalhes desnecessários de implementação.

Deve conter:

- Escopo incluído
- Escopo excluído
- Regras de negócio
- Fluxos principais
- Exceções conhecidas
- Dados envolvidos
- Integrações necessárias

## 4. Quebra em histórias

A solução deve ser decomposta em histórias pequenas, independentes quando possível, orientadas a valor e com critérios de aceite claros.

Cada história deve ter:

- Título objetivo
- Contexto
- User Story
- Regras aplicáveis
- Critérios de aceite
- Dependências
- Fora de escopo
- Observações técnicas

## 5. Criação de subtarefas

No PEOS, os itens de execução no Jira devem ser subtarefas de desenvolvimento ligadas às histórias refinadas.

As subtarefas podem cobrir:

- Backend
- Frontend
- Banco de dados
- Integrações
- QA
- Observabilidade
- Documentação técnica

## 6. Estimativa

As histórias e subtarefas devem ser estimadas em Story Points usando Fibonacci.

A estimativa deve considerar:

- Complexidade técnica
- Incerteza
- Dependências
- Esforço de validação
- Risco de integração

## 7. Autoavaliação do refinamento

Antes de mover uma história para desenvolvimento, aplicar a verificação:

- O problema está claro?
- O escopo está delimitado?
- Os critérios de aceite são testáveis?
- As dependências estão visíveis?
- As dúvidas relevantes foram resolvidas ou registradas?
- O time consegue desenvolver sem interpretação subjetiva?

Se alguma resposta for negativa, a história deve voltar para refinamento.
