# Sincronização GitHub ↔ Notion

Este documento registra como a documentação do **PEOS — Product Engineering Operating System** deve ser mantida sincronizada entre GitHub e Notion.

## Papel de cada ferramenta

- **GitHub**: fonte canônica, versionada e rastreável da documentação.
- **Notion**: portal executivo e operacional de leitura, navegação e alinhamento.

## Regra principal

Toda alteração estrutural, conceitual ou operacional deve nascer ou ser consolidada no GitHub antes de ser refletida no Notion.

O Notion não substitui o versionamento. Ele apresenta a documentação de forma mais acessível para consulta, alinhamento e uso diário.

## Fluxo de sincronização

1. Atualizar ou criar arquivos Markdown no repositório.
2. Registrar mudanças relevantes no `CHANGELOG.md`.
3. Atualizar o `README.md` quando houver novo documento, template, exemplo ou agente.
4. Refletir no Notion apenas o resumo, links internos e navegação executiva.
5. Conferir se o portal do Notion aponta para os mesmos blocos presentes no GitHub.

## Páginas esperadas no Notion

### Documentação principal

- Visão Geral
- Princípios Operacionais
- Fluxo de Refinamento
- Padrão de Histórias Jira
- Governança
- Roadmap
- Checklist de Revisão de Refinamento
- Biblioteca de Padrões de Requisitos

### Templates

- Template — Entrada de Demanda
- Template — Discovery
- Template — História Jira

### Exemplos

- Caso Completo — Recuperação de Senha
- Exemplos de Histórias Jira

### Prompts e agentes

- Prompt-Mestre — Product Architect
- Catálogo de Agentes PEOS

### Histórico

- Changelog PEOS

## Status da sincronização

Última sincronização registrada: **2026-07-08**.

Escopo sincronizado:

- Sprint 1 — Fundação
- Sprint 2 — Publicação
- Sprint 3 — Portal e Operação
- Sprint 4 — Exemplos e Casos de Uso

## Critério de pronto

A sincronização é considerada concluída quando:

- O GitHub contém a versão canônica atualizada.
- O Notion apresenta a navegação executiva equivalente.
- O Changelog registra o escopo entregue.
- O README aponta para os documentos, templates, exemplos, prompts e agentes existentes.
