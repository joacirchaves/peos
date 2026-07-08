# Exemplos de Histórias Jira — PEOS

Este documento reúne exemplos de histórias refinadas seguindo o template completo do PEOS.

## Exemplo 1 — Cadastro de usuário

### História: Permitir cadastro de novo usuário

#### Contexto

Novos usuários precisam criar uma conta para acessar a plataforma.

##### Repositórios Git considerados

- `joacirchaves/peos`: referência documental do padrão PEOS.
- `app-frontend`: interface de cadastro e validação visual.
- `app-backend`: APIs de criação de conta e validações de usuário.

##### Dados externos considerados

- Página de Confluence com política de senha.
- Documento de termos de uso vigente.
- Especificação da API de autenticação.

##### As Is da solução determinada

Atualmente o cadastro é iniciado pela tela pública, mas a validação de unicidade de e-mail e aceite dos termos precisa estar explícita no fluxo de criação da conta.

#### Objetivo

Como visitante, quero criar uma conta informando meus dados básicos, para acessar as funcionalidades da plataforma.

#### Regras de negócio

- O e-mail deve ser único.
- A senha deve seguir a política vigente.
- O usuário deve aceitar os termos de uso.
- O cadastro não deve ser concluído sem os campos obrigatórios.

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

```gherkin
Dado que não aceitei os termos de uso
Quando eu tentar criar a conta
Então o sistema deve impedir o cadastro e indicar que o aceite é obrigatório
```

#### Fora de escopo

- Login social.
- Confirmação de e-mail em duas etapas.
- Autenticação multifator.

#### Dependências

- Política de senha publicada.
- Texto vigente dos termos de uso.
- Endpoint de criação de usuário disponível.

#### Análise Técnica

##### Repositórios impactados

- `app-frontend`: criação ou ajuste do formulário de cadastro.
- `app-backend`: validação de e-mail único, senha e aceite dos termos.

##### Entregáveis técnicos esperados

- Scripts de banco: avaliar necessidade de campo para aceite dos termos e data de aceite.
- Atualizações de pacotes/dependências: não previstas inicialmente.
- Alterações em APIs/endpoints: endpoint de criação de usuário deve validar campos obrigatórios, e-mail único e aceite dos termos.
- Alterações em eventos, filas ou integrações: não previstas inicialmente.
- Alterações em configurações/variáveis de ambiente: não previstas inicialmente.
- Atualizações de documentação técnica: documentar contrato da API de cadastro.
- Outros entregáveis: mensagens de erro padronizadas.

##### Definição da solução técnica

A solução deve validar os dados no frontend para resposta imediata ao usuário e repetir as validações no backend para garantir consistência e segurança. O backend deve persistir a conta apenas quando todos os critérios forem atendidos.

#### Subtarefas sugeridas

- [Frontend] Criar formulário de cadastro com campos obrigatórios.
- [Frontend] Exibir mensagens de validação.
- [Backend] Validar unicidade de e-mail.
- [Backend] Validar política de senha e aceite dos termos.
- [Database] Avaliar persistência do aceite dos termos.
- [QA] Validar cadastro válido, e-mail duplicado, senha inválida e ausência de aceite.
- [Docs] Atualizar documentação do endpoint de cadastro.

#### Estimativa

Story Points: 5

#### Autoavaliação

- Problema claro: sim
- Solução clara: sim
- Critérios testáveis: sim
- Dependências mapeadas: sim
- Pronto para desenvolvimento: parcialmente

## Exemplo 2 — Filtro de pedidos

### História: Filtrar pedidos por status

#### Contexto

Usuários administrativos precisam localizar pedidos rapidamente de acordo com o status operacional.

##### Repositórios Git considerados

- `app-frontend`: tela de listagem e componentes de filtro.
- `app-backend`: endpoint de consulta paginada de pedidos.

##### Dados externos considerados

- Confluence com definição dos status possíveis do pedido.
- Documentação da API de pedidos.

##### As Is da solução determinada

Atualmente a listagem de pedidos exibe registros em ordem cronológica, mas não permite restringir os resultados por status.

#### Objetivo

Como usuário administrativo, quero filtrar pedidos por status, para encontrar rapidamente os pedidos que exigem atenção.

#### Regras de negócio

- O filtro deve permitir seleção de um ou mais status.
- A listagem deve atualizar conforme os filtros aplicados.
- O usuário deve conseguir limpar os filtros.
- A paginação deve considerar os filtros ativos.

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

```gherkin
Dado que selecionei mais de um status
Quando a listagem for carregada
Então o sistema deve exibir pedidos que correspondam a qualquer um dos status selecionados
```

#### Fora de escopo

- Filtro por período.
- Exportação da listagem.
- Criação de novos status.

#### Dependências

- Lista oficial de status do pedido.
- Endpoint de consulta de pedidos com suporte a filtros.

#### Análise Técnica

##### Repositórios impactados

- `app-frontend`: componente de filtro e integração com query params.
- `app-backend`: suporte a parâmetro de status na consulta de pedidos.

##### Entregáveis técnicos esperados

- Scripts de banco: não previstos inicialmente.
- Atualizações de pacotes/dependências: não previstas inicialmente.
- Alterações em APIs/endpoints: endpoint de listagem deve aceitar filtro por múltiplos status.
- Alterações em eventos, filas ou integrações: não previstas.
- Alterações em configurações/variáveis de ambiente: não previstas.
- Atualizações de documentação técnica: atualizar contrato da API de pedidos.
- Outros entregáveis: testes automatizados para filtro simples e múltiplo.

##### Definição da solução técnica

O frontend deve enviar os status selecionados como parâmetros de consulta. O backend deve aplicar os filtros na camada de consulta, mantendo paginação e ordenação consistentes.

#### Subtarefas sugeridas

- [Frontend] Criar componente de filtro por status.
- [Frontend] Integrar filtro com listagem e limpeza de filtros.
- [Backend] Ajustar endpoint de consulta para múltiplos status.
- [QA] Validar filtro único, múltiplo, limpeza e paginação.
- [Docs] Atualizar documentação da API de pedidos.

#### Estimativa

Story Points: 3

#### Autoavaliação

- Problema claro: sim
- Solução clara: sim
- Critérios testáveis: sim
- Dependências mapeadas: sim
- Pronto para desenvolvimento: sim

## Exemplo 3 — Exportação de relatório

### História: Exportar relatório em CSV

#### Contexto

Gestores precisam analisar dados fora do sistema em ferramentas como planilhas.

##### Repositórios Git considerados

- `app-frontend`: tela do relatório e ação de exportação.
- `app-backend`: geração do arquivo CSV.
- `data-service`: origem dos dados consolidados, quando aplicável.

##### Dados externos considerados

- Confluence com definição das colunas do relatório.
- Dicionário de dados.
- Regras de autorização para acesso a relatórios.

##### As Is da solução determinada

Atualmente o relatório é visualizado apenas em tela. O usuário precisa copiar dados manualmente para análise externa.

#### Objetivo

Como gestor, quero exportar um relatório em CSV, para analisar os dados em uma planilha.

#### Regras de negócio

- A exportação deve respeitar filtros aplicados.
- O arquivo deve ser gerado em formato CSV.
- O nome do arquivo deve conter a data da exportação.
- Apenas usuários autorizados podem exportar relatórios.

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

```gherkin
Dado que meu usuário não possui permissão para exportar relatórios
Quando eu acessar a tela do relatório
Então o sistema não deve exibir a ação de exportação
```

#### Fora de escopo

- Exportação em PDF.
- Agendamento recorrente de relatórios.
- Envio automático por e-mail.

#### Dependências

- Definição oficial das colunas do CSV.
- Permissão de exportação configurada.
- Fonte de dados do relatório disponível.

#### Análise Técnica

##### Repositórios impactados

- `app-frontend`: botão de exportação e tratamento do download.
- `app-backend`: endpoint de geração do CSV.
- `data-service`: consulta aos dados consolidados, se necessário.

##### Entregáveis técnicos esperados

- Scripts de banco: não previstos inicialmente.
- Atualizações de pacotes/dependências: avaliar biblioteca de geração CSV no backend.
- Alterações em APIs/endpoints: criar ou ajustar endpoint de exportação.
- Alterações em eventos, filas ou integrações: não previstas inicialmente.
- Alterações em configurações/variáveis de ambiente: avaliar limite de tamanho de arquivo/exportação.
- Atualizações de documentação técnica: documentar endpoint, permissões e colunas exportadas.
- Outros entregáveis: testes de autorização e compatibilidade do CSV.

##### Definição da solução técnica

A solução deve gerar o CSV no backend com base nos filtros recebidos e permissões do usuário autenticado. O frontend deve apenas solicitar a exportação e tratar o download do arquivo.

#### Subtarefas sugeridas

- [Frontend] Adicionar ação de exportação na tela do relatório.
- [Frontend] Ocultar ação para usuários sem permissão.
- [Backend] Criar endpoint de exportação CSV.
- [Backend] Aplicar filtros e permissões na exportação.
- [QA] Validar exportação com filtros, sem permissão e nome do arquivo.
- [Docs] Documentar colunas exportadas e contrato do endpoint.

#### Estimativa

Story Points: 5

#### Autoavaliação

- Problema claro: sim
- Solução clara: sim
- Critérios testáveis: sim
- Dependências mapeadas: sim
- Pronto para desenvolvimento: parcialmente
