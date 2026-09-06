# Starter genérico para projetos web
Data: 2026-09-06
Agente/autor: Felipe Paniago

## Objetivo
Criar base inicial genérica para projetos com React, Next.js, BFF e serviços Node.js.

## O que foi feito
- Reescrito `README.md` como ponto de entrada do starter.
- Reescrito `docs/descricao-sistema.md` com o roteiro de decisão baseado no prompt fornecido.
- Criado `docs/next-react.md` com referência mínima de React e Next.js.
- Atualizado `AGENTS.md` para refletir responsabilidades Front/BFF/domínio.
- Removidos diagramas e perfis antigos específicos de MCP e agentes.
- Mantido o ADR de documentação como código e preservado o histórico em `memory/`.

## Decisões tomadas (e por quê)
O template mantém BFF e serviços de domínio como limites explícitos porque eles
organizam responsabilidades e contratos sem depender de um produto específico.

## Suposições adotadas
React e Next.js são a referência mínima do front, enquanto Node.js/TypeScript é a
referência do BFF e dos serviços de domínio, conforme o prompt fornecido.

## Lacunas que continuam abertas
O projeto ainda não descreve um produto concreto, seus requisitos, contratos ou
ferramentas de verificação. Esses dados devem ser preenchidos no documento inicial.

## Próximo passo sugerido
Duplicar `docs/descricao-sistema.md` ou preenchê-lo com o primeiro problema real do time.
