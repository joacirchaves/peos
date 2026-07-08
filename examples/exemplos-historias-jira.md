# Exemplos de Histórias Jira — PEOS

Este documento reúne exemplos de histórias refinadas seguindo o padrão PEOS.

## Exemplo 1 — Cadastro de usuário

### História: Permitir cadastro de novo usuário

#### Contexto

Novos usuários precisam criar uma conta para acessar a plataforma.

#### User Story

Como visitante, quero criar uma conta informando meus dados básicos, para acessar as funcionalidades da plataforma.

#### Regras de negócio

- O e-mail deve ser único.
- A senha deve seguir a política vigente.
- O usuário deve aceitar os termos de uso.

#### Critérios de aceite

```gherkin
Dado que sou um visitante sem conta
Quando eu preencher os dados obrigatórios e aceitar os termos
Então o sistema deve criar minha conta com sucesso
```

```gherkin
Dado que informei um e-mail já cadastrado
Quando eu tentar criar a conta
Então o sistema deve informar que não foi possível concluir o cadastro com os dados informados
```

#### Estimativa

Story Points: 5

## Exemplo 2 — Filtro de pedidos

### História: Filtrar pedidos por status

#### Contexto

Usuários precisam localizar pedidos rapidamente de acordo com o status operacional.

#### User Story

Como usuário administrativo, quero filtrar pedidos por status, para encontrar rapidamente os pedidos que exigem atenção.

#### Regras de negócio

- O filtro deve permitir seleção de um ou mais status.
- A listagem deve atualizar conforme os filtros aplicados.
- O usuário deve conseguir limpar os filtros.

#### Critérios de aceite

```gherkin
Dado que estou na listagem de pedidos
Quando eu selecionar o status "Pendente"
Então o sistema deve exibir apenas pedidos com status pendente
```

```gherkin
Dado que apliquei filtros na listagem
Quando eu clicar em limpar filtros
Então o sistema deve exibir novamente a listagem sem filtros aplicados
```

#### Estimativa

Story Points: 3

## Exemplo 3 — Exportação de relatório

### História: Exportar relatório em CSV

#### Contexto

Gestores precisam analisar dados fora do sistema em ferramentas como planilhas.

#### User Story

Como gestor, quero exportar um relatório em CSV, para analisar os dados em uma planilha.

#### Regras de negócio

- A exportação deve respeitar filtros aplicados.
- O arquivo deve ser gerado em formato CSV.
- O nome do arquivo deve conter a data da exportação.

#### Critérios de aceite

```gherkin
Dado que apliquei filtros em um relatório
Quando eu solicitar a exportação em CSV
Então o sistema deve gerar um arquivo contendo apenas os dados filtrados
```

```gherkin
Dado que a exportação foi concluída
Quando o arquivo for baixado
Então o nome do arquivo deve conter a data da exportação
```

#### Estimativa

Story Points: 5
