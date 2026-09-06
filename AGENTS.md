# Contrato de trabalho do repositório

Este repositório é uma base de documentação arquitetural para aplicações web
com React, Next.js, BFF e serviços Node.js. A fonte de verdade é textual:
Markdown, contratos e diagramas versionados.

## Regras invioláveis

1. Não invente números, SLAs, custos ou volumes. Proponha como medi-los.
2. Separe fatos de hipóteses.
3. Registre toda lacuna essencial e a decisão que ela bloqueia.
4. Toda recomendação deve ser condicionada à prioridade do time.
5. Cada pró e contra deve referenciar um atributo de qualidade ou restrição.
6. Toda proposta deve indicar a responsabilidade no front, BFF ou domínio.
7. Mudança no contrato Front–BFF é mudança arquitetural, não refactor.
8. Tecnologia fora da stack exige justificativa e custo de operação.
9. Um diagrama tem um nível por desenho e integrações externas marcadas.
10. Toda tarefa executada gera um arquivo em `memory/`.

## Stack padrão

- Front-end: React com TypeScript, normalmente estruturado com Next.js.
- BFF: Node.js/TypeScript; agrega, adapta e reduz payload para as telas.
- Serviços de domínio: Node.js/TypeScript; donos da regra e do dado.
- Persistência, fila e cache: somente quando declarados no problema.

## Dependências proibidas

- Front → domínio ou terceiro.
- BFF → banco de domínio.
- Vazamento de detalhe de fornecedor do BFF para o front.

São permitidos Front → BFF e BFF → serviços de domínio ou integrações externas.

## Fluxo ao alterar documentação

1. Ler `docs/descricao-sistema.md`.
2. Separar fatos, hipóteses e lacunas.
3. Registrar ADR quando houver mudança de limite, dependência ou contrato.
4. Atualizar documento e diagramas correspondentes.
5. Revisar com o checklist do documento.
6. Registrar a tarefa em `memory/`.

## Fora de escopo

- Marcar ADR como Aceita.
- Escolher alternativa sem declarar a priorização.
- Responder às próprias perguntas de esclarecimento.
- Gerar código quando a tarefa pedir apenas documentação.

## Formato de `memory/`

Um arquivo por tarefa: `memory/AAAA-MM-DD-slug-da-tarefa.md`.

```markdown
# <título curto da tarefa>
Data: AAAA-MM-DD
Agente/autor: <quem executou>

## Objetivo
## O que foi feito
## Decisões tomadas (e por quê)
## Suposições adotadas
## Lacunas que continuam abertas
## Próximo passo sugerido
```
