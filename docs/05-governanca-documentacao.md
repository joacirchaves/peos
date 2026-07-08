# Governança da Documentação PEOS

A governança garante que o PEOS continue claro, versionado e útil para execução do produto.

## Fontes oficiais

O PEOS usa três camadas complementares:

- **GitHub**: fonte versionada da documentação estrutural e técnica.
- **Notion**: apresentação navegável para leitura, alinhamento e consulta.
- **Jira**: execução operacional das histórias, subtarefas e acompanhamento do trabalho.

## Regra de versionamento

Toda mudança relevante na estrutura do PEOS deve ser registrada no GitHub.

Mudanças relevantes incluem:

- Alteração de fluxo
- Novo template
- Novo padrão de história
- Mudança na Definition of Ready
- Mudança na Definition of Done
- Inclusão de novo agente ou prompt operacional

## Padrão de escrita

A documentação deve ser:

- Clara
- Direta
- Sem redundância desnecessária
- Orientada à execução
- Fácil de consultar
- Independente o suficiente para ser lida fora de ordem

## Organização sugerida

```text
docs/
  01-visao-geral.md
  02-principios-operacionais.md
  03-fluxo-de-refinamento.md
  04-padrao-historias-jira.md
  05-governanca-documentacao.md

prompts/
  Prompt-Mestre-Product-Architect.md
```

## Critério de qualidade

Um documento do PEOS é considerado bom quando ajuda o leitor a tomar uma decisão, executar uma etapa ou reduzir ambiguidade.

Se um trecho apenas repete conceitos já explicados, ele deve ser removido, resumido ou referenciado.

## Evolução futura

As próximas evoluções podem incluir:

- Templates de entrada de demanda
- Templates de discovery
- Templates de refinamento
- Exemplos de histórias completas
- Estrutura de integração com Jira
- Agentes especializados por etapa do fluxo
- Automação de geração e revisão de histórias
