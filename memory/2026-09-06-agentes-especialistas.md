# Agentes especialistas por camada
Data: 2026-09-06
Agente/autor: Felipe Paniago

## Objetivo
Criar especialistas de PostgreSQL, BFF, APIs, Node e front/React em
`.claude/agents` e `.agents/agents`.

## O que foi feito
- Criados `postgres.md`, `bff.md`, `apis.md`, `node.md` e `react.md` nas duas
  pastas de agentes.
- Criada a skill `postgres` (ainda não existia), espelhada em `.claude/skills`
  e `.agents/skills`.
- Atualizados `AGENTS.md` (tabela de delegação) e a estrutura do `README.md`.

## Decisões tomadas (e por quê)
Os agentes reutilizam as skills já existentes (`bff`, `node`, `react`,
`security-apis`) via frontmatter. Postgres ganhou skill própria porque o
banco só pode viver no domínio e o BFF não pode conectar nele. Persistência
continua condicionada ao PROBLEMA.

## Suposições adotadas
Claude Code lê `.claude/agents/*.md`. Codex neste repo segue o espelho em
`.agents/agents/`, no mesmo padrão das skills.

## Lacunas que continuam abertas
Não há `.codex/agents/*.toml` nem cópia em `.cursor`. O PROBLEMA ainda não
declara persistência nem IdP; o agente `postgres` deve registrar isso como
lacuna até o time declarar o store.

## Próximo passo sugerido
Invocar um especialista numa decisão real (por exemplo contrato Front–BFF ou
schema de domínio, se persistência for declarada).
