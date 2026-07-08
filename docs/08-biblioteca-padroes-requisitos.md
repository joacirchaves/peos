# Biblioteca de Padrões de Requisitos — PEOS

Esta biblioteca reúne padrões reutilizáveis para escrever requisitos e critérios de aceite com mais clareza.

## 1. Padrão de requisito funcional

Use quando o sistema deve executar uma ação clara.

```text
O sistema deve [ação] quando [condição], para permitir [resultado].
```

### Exemplo

O sistema deve enviar um e-mail de recuperação quando o usuário solicitar redefinição de senha, para permitir a recuperação autônoma do acesso.

## 2. Padrão de regra de validação

Use quando há validação de campo, regra ou condição.

```text
O sistema deve validar [campo/regra] antes de permitir [ação].
```

### Exemplo

O sistema deve validar o formato do e-mail antes de permitir o envio da solicitação de recuperação.

## 3. Padrão de permissão

Use quando uma ação depende de perfil, papel ou autorização.

```text
Somente usuários com [perfil/permissão] podem [ação].
```

### Exemplo

Somente usuários administradores podem acessar a tela de gestão de permissões.

## 4. Padrão de exceção

Use quando há comportamento esperado para erro ou condição alternativa.

```text
Caso [condição de exceção], o sistema deve [comportamento esperado].
```

### Exemplo

Caso o link de recuperação esteja expirado, o sistema deve informar a expiração e orientar uma nova solicitação.

## 5. Padrão de critério de aceite em português BR

Use Dado / Quando / Então.

```gherkin
Dado que [contexto]
Quando [ação]
Então [resultado esperado]
```

### Exemplo

```gherkin
Dado que o usuário possui uma conta ativa
Quando solicitar a recuperação de senha com e-mail válido
Então o sistema deve enviar um link de recuperação para o e-mail cadastrado
```

## 6. Padrão de dependência

Use para deixar bloqueios ou requisitos externos explícitos.

```text
Esta história depende de [sistema/time/decisão/dado] para [motivo].
```

### Exemplo

Esta história depende do serviço de e-mail transacional para enviar o link de recuperação ao usuário.

## 7. Padrão de fora de escopo

Use para evitar interpretações indevidas.

```text
Esta história não contempla [item], que deverá ser tratado em [história futura/outro fluxo].
```

### Exemplo

Esta história não contempla recuperação por SMS, que deverá ser tratada em uma evolução futura.

## 8. Padrão de observação técnica

Use para orientar sem prescrever implementação desnecessária.

```text
Considerar [orientação técnica] para garantir [resultado técnico esperado].
```

### Exemplo

Considerar invalidação do token após uso para garantir que o link de recuperação não possa ser reutilizado.

## 9. Sinais de requisito fraco

Evite requisitos com expressões vagas como:

- rápido
- simples
- intuitivo
- robusto
- moderno
- adequado
- fácil
- melhorado

Substitua por critérios observáveis, mensuráveis ou testáveis.

## 10. Perguntas de refinamento

- Qual comportamento o sistema deve ter?
- Em qual condição esse comportamento acontece?
- Quem pode executar a ação?
- O que acontece em caso de erro?
- Quais dados são obrigatórios?
- Quais integrações são necessárias?
- Como QA validará a entrega?
