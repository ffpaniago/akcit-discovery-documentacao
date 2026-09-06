# Starter de arquitetura para aplicações web

Base para um time pequeno que mantém um produto web com React, BFF e serviços
Node.js. O material daqui é insumo para decisão. A decisão pertence ao time.

Quem escreve neste repositório atua como arquiteto de software sênior e
consultor interno: esclarece fatos, hipóteses, lacunas, contratos e
responsabilidades. Não escolhe sozinho a alternativa vencedora.

## Comece por aqui

1. Preencha o [PROBLEMA](docs/descricao-sistema.md) (produto, dor, resultado,
   atributos de qualidade, restrições e o que já está fora de discussão).
2. Siga o contrato de trabalho em [AGENTS.md](AGENTS.md).
3. Use a [referência mínima de React](docs/next-react.md) quando a dúvida for
   de tela, estado ou fronteira com o BFF.
4. Proponha ADR em `docs/adr/` com status **Proposto**. A aceitação é do time,
   por pull request.

## Stack

```text
React (TypeScript) → BFF Node.js/TypeScript → Serviços de domínio
                                           └──→ Integrações externas, quando o problema declarar
```

| Camada | Faz | Não faz |
|---|---|---|
| Front | Apresentação e estado de tela. Consome só o BFF. | Chamar domínio ou terceiro. Guardar regra ou segredo. |
| BFF | Agregar, adaptar e reduzir payload. Propagar escopo autenticado. | Regra de negócio. Banco de domínio. Vazamento de fornecedor ao front. |
| Domínio | Dono da regra e do dado. | Delegar decisão de negócio ao front ou ao BFF. |

Persistência, fila e cache só entram se já estiverem no PROBLEMA. Tecnologia
fora da stack exige justificativa e custo de operação explícitos.

## Dependências

Permitido: Front → BFF; BFF → serviços de domínio e integrações externas.

Proibido: Front → domínio ou terceiro; BFF → banco de domínio; detalhe de
fornecedor vazando do BFF para o front.

Quebrar o contrato Front–BFF é mudança arquitetural, não refactor. Contrato de
API versionado fica junto do código e é revisado em pull request.

## Restrições recorrentes

- Time pequeno: bus factor baixo é risco real; manutenção é custo de primeira ordem.
- Legado e ambientes de terceiros que o time não controla.
- Dados pessoais e segregação por cliente/tenant.
- APIs externas com quota e mudança unilateral de contrato.
- Observabilidade limitada ao que o PROBLEMA declarar. Ferramenta nova é pré-requisito.

## O que uma decisão deve entregar

Documento em Markdown, na ordem, pronto para revisão de time. Um stakeholder
precisa conseguir responder sem ter lido a conversa que o gerou.

1. Fatos × hipóteses
2. 6 a 10 perguntas de esclarecimento (sem respondê-las)
3. 3 alternativas (responsabilidade, contrato Front–BFF, trade-off, uso / não uso, esforço, operação)
4. Recomendação condicionada a dois cenários de priorização
5. 6 a 8 riscos em tabela, incluindo vazamento de responsabilidade entre camadas
6. Plano de verificação com as ferramentas já existentes
7. ADR proposto, mudanças de contrato e itens de execução com critério de aceitação
8. Lacunas e a decisão que cada uma bloqueia

O roteiro preenchível está em [`docs/descricao-sistema.md`](docs/descricao-sistema.md).

## Estrutura

```text
.
├── README.md
├── AGENTS.md                 ← contrato para agentes e autores
├── docs/
│   ├── descricao-sistema.md  ← PROBLEMA + entrega da decisão
│   ├── next-react.md         ← referência mínima de React/Next.js
│   └── adr/                  ← ADRs com status Proposto
├── .claude/skills/
├── .agents/skills/
├── .cursor/skills/
└── memory/                   ← um arquivo por tarefa executada
```

Diagramas, quando existirem, são código: um nível por desenho, integrações
externas marcadas, revisão por pull request.
