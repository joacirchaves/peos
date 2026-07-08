# Caso Completo — Recuperação de Senha

Este exemplo demonstra o uso do PEOS do início da demanda até histórias refinadas e subtarefas.

## 1. Entrada da demanda

### Nome da demanda

Recuperação de senha por e-mail.

### Área solicitante

Atendimento ao cliente e Produto.

### Problema

Usuários que esquecem a senha precisam acionar o suporte para recuperar o acesso. Isso aumenta o volume de atendimento e gera fricção na jornada.

### Usuários impactados

- Usuários finais com conta ativa.
- Time de suporte.

### Objetivo

Permitir que o usuário recupere a senha de forma autônoma, segura e rápida.

### Resultado esperado

Reduzir chamados de suporte relacionados a recuperação de senha e melhorar a experiência de acesso.

## 2. Discovery

### Hipótese

Acreditamos que permitir recuperação de senha por e-mail reduzirá a dependência do suporte e melhorará a experiência de login.

### Jornada atual

1. Usuário tenta acessar a conta.
2. Usuário não lembra a senha.
3. Usuário entra em contato com suporte.
4. Suporte valida informações manualmente.
5. Usuário recebe orientação para redefinir acesso.

### Jornada desejada

1. Usuário acessa a tela de login.
2. Usuário clica em "Esqueci minha senha".
3. Usuário informa o e-mail cadastrado.
4. Sistema envia link seguro para redefinição.
5. Usuário cria nova senha.
6. Usuário acessa a conta com a nova senha.

### Sinais de sucesso

- Redução de chamados sobre senha.
- Aumento de recuperações concluídas sem suporte.
- Redução do tempo médio para recuperar acesso.

## 3. Solução proposta

Criar fluxo de recuperação de senha por e-mail para usuários com conta ativa.

### Escopo incluído

- Link "Esqueci minha senha" na tela de login.
- Formulário para informar e-mail.
- Envio de e-mail com link de redefinição.
- Validação de expiração do link.
- Tela para criação de nova senha.
- Confirmação de senha alterada.

### Fora de escopo

- Recuperação por SMS.
- Recuperação por WhatsApp.
- Alteração da política global de autenticação.
- Login social.

### Regras de negócio

- O link deve expirar em 30 minutos.
- O link deve ser de uso único.
- O sistema não deve informar se o e-mail existe ou não.
- Apenas contas ativas podem concluir a redefinição.
- A nova senha deve seguir a política vigente.

### Dependências

- Serviço de envio de e-mail.
- Template de e-mail transacional.
- Política de senha vigente.
- Endpoint de geração e validação de token.

## 4. Histórias refinadas

### História 1 — Solicitar recuperação de senha

#### Contexto

Usuários que esquecem a senha precisam iniciar a recuperação sem depender do suporte.

#### User Story

Como usuário com conta cadastrada, quero solicitar a recuperação de senha pelo meu e-mail, para recuperar meu acesso de forma autônoma.

#### Regras de negócio

- O sistema deve exibir a opção "Esqueci minha senha" na tela de login.
- O usuário deve informar um e-mail.
- A resposta do sistema deve ser genérica, sem revelar se o e-mail existe.

#### Critérios de aceite

```gherkin
Dado que estou na tela de login
Quando eu clicar em "Esqueci minha senha"
Então o sistema deve exibir a tela de solicitação de recuperação de senha
```

```gherkin
Dado que informei um e-mail em formato válido
Quando eu enviar a solicitação
Então o sistema deve exibir uma mensagem genérica orientando a verificar o e-mail
```

```gherkin
Dado que informei um e-mail em formato inválido
Quando eu enviar a solicitação
Então o sistema deve informar que o e-mail informado é inválido
```

#### Fora de escopo

- Validação da nova senha.
- Login automático após redefinição.

#### Dependências

- Tela de login existente.
- Serviço de envio de e-mail.

#### Subtarefas sugeridas

- [Frontend] Adicionar link "Esqueci minha senha".
- [Frontend] Criar tela de solicitação de recuperação.
- [Backend] Criar endpoint de solicitação de recuperação.
- [QA] Validar cenários de e-mail válido, inválido e resposta genérica.

#### Estimativa

Story Points: 5

### História 2 — Redefinir senha com link seguro

#### Contexto

Após solicitar a recuperação, o usuário precisa definir uma nova senha usando um link seguro e temporário.

#### User Story

Como usuário que recebeu um link de recuperação, quero cadastrar uma nova senha, para voltar a acessar minha conta com segurança.

#### Regras de negócio

- O link deve expirar em 30 minutos.
- O token deve ser de uso único.
- A nova senha deve seguir a política vigente.
- Links expirados ou inválidos devem exibir mensagem clara.

#### Critérios de aceite

```gherkin
Dado que recebi um link válido de recuperação
Quando eu acessar o link
Então o sistema deve exibir a tela para criação de nova senha
```

```gherkin
Dado que informei uma nova senha válida e sua confirmação
Quando eu confirmar a redefinição
Então o sistema deve alterar minha senha e invalidar o link utilizado
```

```gherkin
Dado que acessei um link expirado
Quando a página carregar
Então o sistema deve informar que o link expirou e orientar nova solicitação
```

#### Fora de escopo

- Autenticação multifator.
- Recuperação por canal alternativo.

#### Dependências

- Endpoint de validação de token.
- Política de senha.
- Tela de nova senha.

#### Subtarefas sugeridas

- [Backend] Implementar geração e validação de token.
- [Backend] Implementar alteração segura de senha.
- [Frontend] Criar tela de nova senha.
- [QA] Validar token válido, expirado, inválido e reutilizado.

#### Estimativa

Story Points: 8

## 5. Autoavaliação PEOS

- Clareza do problema: alta.
- Clareza da solução: alta.
- Ambiguidade restante: baixa.
- Dependências mapeadas: sim.
- Critérios de aceite testáveis: sim.
- Pronto para desenvolvimento: sim.
