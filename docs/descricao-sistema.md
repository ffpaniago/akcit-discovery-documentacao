# Documento inicial de arquitetura

Este documento é um ponto de partida para projetos web com front-end React,
camada BFF e serviços Node.js. Ele deve ser preenchido antes de uma decisão
arquitetural e revisado por pull request.

## 1. Fatos

- Produto e escopo afetado: `<telas, rotas do BFF e serviços>`
- Situação atual e onde dói: `<descrever o problema observado>`
- Resultado esperado: `<descrever o resultado>`
- Atributos de qualidade, em ordem de prioridade: `<listar>`
- Restrições: `<prazo, contrato, legado e equipe>`
- Já decidido e fora de discussão: `<listar>`

## 2. Hipóteses

- `<inferência que ainda precisa ser confirmada>`
- `<risco ou comportamento esperado não medido>`

Hipóteses não viram fatos sem verificação. Números, SLAs, custos e volumes
devem ser medidos; quando não existirem, registrar como lacuna.

## 3. Stack e responsabilidades

| Camada | Responsabilidade | Dependências permitidas | Limites |
|---|---|---|---|
| Front-end | React com TypeScript, estado da tela e apresentação | BFF | Não acessa domínio nem terceiros diretamente |
| BFF | Agregar, adaptar e reduzir payload para as telas | Serviços de domínio e integrações externas | Não contém regra de negócio nem acessa banco de domínio |
| Serviço de domínio | Regra de negócio e posse dos dados | Persistência, fila e cache já declarados no problema | Não delega sua regra ao front ou ao BFF |

Toda proposta deve dizer onde a responsabilidade fica e o que acontece com
o contrato entre as camadas. Quebrar o contrato Front–BFF é mudança
arquitetural, não refactor.

## 4. Regras de camada

- Front → BFF: permitido.
- Front → domínio ou terceiro: proibido.
- BFF → serviço de domínio e integrações externas: permitido.
- BFF → banco de domínio: proibido.
- Detalhe de fornecedor externo não vaza do BFF para o front.
- Tecnologia fora da stack exige justificativa e custo de operação explícitos.

## 5. Fatos x hipóteses da decisão

### Fatos confirmados

- `<fato com fonte ou evidência>`

### Hipóteses de trabalho

- `<hipótese e como será verificada>`

## 6. Perguntas de esclarecimento

Ordenar de maior para menor impacto na decisão. Não responder às próprias
perguntas nesta seção.

1. `<pergunta que pode mudar o limite entre camadas>`
2. `<pergunta sobre contrato ou requisito de qualidade>`
3. `<pergunta sobre legado, terceiros ou restrição de equipe>`
4. `<pergunta sobre dados e responsabilidade>`
5. `<pergunta sobre observabilidade e verificação>`
6. `<pergunta adicional, se necessária>`

## 7. Alternativas

Registrar três alternativas, sempre com responsabilidade, contrato e operação.

| Alternativa | Onde fica cada responsabilidade | Impacto no contrato Front–BFF | Trade-off ligado a atributo ou restrição | Usar quando | Não usar quando | Esforço para time pequeno | Operação adicionada |
|---|---|---|---|---|---|---|---|
| A | Front: `<...>`<br>BFF: `<...>`<br>Domínio: `<...>` | `<...>` | `<atributo ou restrição>` | `<condição>` | `<condição>` | Alto/médio/baixo: `<uma frase>` | `<manutenção, deploy, observabilidade>` |
| B | Front: `<...>`<br>BFF: `<...>`<br>Domínio: `<...>` | `<...>` | `<atributo ou restrição>` | `<condição>` | `<condição>` | Alto/médio/baixo: `<uma frase>` | `<...>` |
| C | Front: `<...>`<br>BFF: `<...>`<br>Domínio: `<...>` | `<...>` | `<atributo ou restrição>` | `<condição>` | `<condição>` | Alto/médio/baixo: `<uma frase>` | `<...>` |

Evitar argumentos genéricos como “moderno”, “flexível” ou “escalável”.

## 8. Recomendação condicionada

- Se priorizarmos `<atributo A>`, então `<alternativa e motivo>`.
- Se priorizarmos `<atributo B>`, então `<alternativa e motivo>`.

A decisão pertence ao time. Nenhuma alternativa deve ser marcada como vencedora
sem declarar a priorização que a favorece.

## 9. Riscos

| Risco | Causa provável | Impacto | Detecção | Mitigação arquitetural |
|---|---|---|---|---|
| Regra de negócio no front | Pressão para reduzir uma chamada | alto/médio/baixo | Revisão do contrato e testes | Manter decisão no serviço de domínio |
| Regra de negócio no BFF | BFF acumula transformação e decisão | alto/médio/baixo | Revisão de código | BFF apenas agrega e adapta |
| Vazamento de fornecedor no front | Resposta externa repassada sem adaptação | alto/médio/baixo | Teste de contrato | Modelo próprio no BFF |
| Contrato Front–BFF quebrado | Mudança tratada como refactor | alto/médio/baixo | Teste de contrato versionado | Versionar e revisar a mudança |
| Bus factor baixo | Conhecimento concentrado | alto/médio/baixo | Revisão e documentação | Dono, runbook e decisão registrada |
| Terceiro muda o contrato | API externa muda unilateralmente | alto/médio/baixo | Teste de integração e alertas | Adaptador isolado no BFF |

## 10. Plano de verificação

| Hipótese | Como testar com ferramentas existentes | Critério de aceitação | Sinal de alerta |
|---|---|---|---|
| `<hipótese>` | Teste de contrato, revisão de PR ou inspeção de logs já disponíveis | `<critério observável>` | `<sinal>` |
| `<hipótese>` | `<ferramenta existente>` | `<critério>` | `<sinal>` |

Ferramenta nova é pré-requisito: documentar antes de incorporá-la.

## 11. Registro e execução

### ADR-NNN — `<decisão>`

- Status: Proposto
- Contexto: `<fatos e restrições>`
- Decisão proposta: `<alternativa condicionada>`
- Consequências: `<contrato, operação e manutenção>`
- Lacunas: `<o que impede aceitar a decisão>`

### Mudanças de contrato

- `<contrato afetado, versão e compatibilidade>`

### Itens de execução

- `<item>` — Critério de aceitação: `<resultado verificável>`

## 12. Lacunas

| Lacuna | Decisão bloqueada |
|---|---|
| `<informação essencial ausente>` | `<decisão que depende dela>` |

## Fora de escopo

- Não marcar ADR como Aceita.
- Não eleger alternativa sem condicionar a recomendação.
- Não gerar código neste documento.
- Não responder às perguntas da seção 6.
