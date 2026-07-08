# Padrão de Histórias para Jira

Este documento define o padrão mínimo para histórias refinadas no PEOS.

## Estrutura da história

### Título

Deve ser claro, curto e orientado ao resultado.

Exemplo:

> Permitir que o usuário redefina a senha por e-mail

### Contexto

Explica por que a história existe, qual problema resolve e qual impacto esperado.

### User Story

Formato recomendado:

> Como [tipo de usuário], quero [ação ou capacidade], para [benefício ou resultado].

### Regras de negócio

Lista objetiva das regras aplicáveis.

Exemplo:

- O link de redefinição deve expirar em 30 minutos.
- O e-mail deve ser enviado apenas para contas ativas.
- A nova senha deve respeitar a política de segurança vigente.

### Critérios de aceite

Preferencialmente em Given/When/Then.

Exemplo:

```gherkin
Given que o usuário possui uma conta ativa
When solicitar a redefinição de senha
Then o sistema deve enviar um e-mail com link válido por 30 minutos
```

### Fora de escopo

Define claramente o que não será entregue nesta história.

### Dependências

Registra dependências técnicas, funcionais ou externas.

### Observações técnicas

Inclui orientações úteis para desenvolvimento, sem transformar a história em especificação de baixo nível desnecessária.

### Estimativa

Utilizar Story Points em Fibonacci: 1, 2, 3, 5, 8, 13.

Histórias acima de 13 pontos devem ser reavaliadas para quebra.

## Definition of Ready

Uma história está pronta para desenvolvimento quando:

- O objetivo está claro
- O escopo está definido
- Os critérios de aceite são testáveis
- As dependências estão registradas
- Os riscos relevantes foram identificados
- O time entende o comportamento esperado

## Definition of Done

Uma história está concluída quando:

- Código implementado
- Critérios de aceite atendidos
- Testes executados conforme necessidade
- Validação de QA concluída
- Documentação atualizada quando aplicável
- Nenhum bloqueio crítico conhecido permanece aberto
