# Corrigir parse do diagrama de sequência no GitHub
Data: 2026-09-06
Agente/autor: Cursor Grok 4.6

## Objetivo
Fazer o Mermaid da jornada crítica renderizar no GitHub.

## O que foi feito
- Removidos ponto e vírgula nas mensagens (o parser trata `;` como fim de
  statement).
- Removidos parênteses em aliases e acentos no bloco Mermaid.
- Espelho atualizado em `docs/diagramas/sequencia-tela-autenticada.mmd`.

## Decisões tomadas (e por quê)
O significado (opt condicional, alt de falha, idempotência em comando) ficou
igual. Só a grafia do diagrama foi adaptada ao parser.

## Suposições adotadas
O GitHub Mermaid do README usa a mesma gramática que quebra em `;` e em
`(se declarado)` sem aspas.

## Lacunas que continuam abertas
Nenhuma relativa ao parse.

## Próximo passo sugerido
Conferir o README renderizado no GitHub após o push.
