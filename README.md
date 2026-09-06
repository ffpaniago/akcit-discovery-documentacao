# Starter de arquitetura para aplicações web

Base mínima para iniciar projetos com React, Next.js, BFF e serviços Node.js.
O objetivo é produzir insumos para decisão, com fatos, hipóteses, lacunas,
contratos e responsabilidades claras.

## Comece por aqui

- [Documento inicial de arquitetura](docs/descricao-sistema.md)
- [Referência mínima de React e Next.js](docs/next-react.md)
- [Contrato para trabalho no repositório](AGENTS.md)

## Estrutura

```text
.
├── README.md
├── AGENTS.md
├── docs/
│   ├── descricao-sistema.md  ← roteiro para qualquer projeto
│   ├── next-react.md         ← referência mínima da stack web
│   └── adr/                  ← decisões arquiteturais propostas
├── .claude/skills/           ← skills do starter (Claude Code)
├── .agents/skills/           ← mesma cópia para Codex/agentes
├── .cursor/skills/           ← mesma cópia para Cursor
└── memory/                   ← histórico append-only das tarefas
```

## Princípios

- Não inventar números, custos, volumes ou SLAs; propor como medir.
- Separar fatos de hipóteses.
- Registrar lacunas e a decisão bloqueada por cada uma.
- Manter responsabilidades explícitas entre front, BFF e domínio.
- Tratar mudança de contrato Front–BFF como mudança arquitetural.
- Condicionar recomendações à prioridade escolhida pelo time.
- Considerar operação e manutenção como custo de primeira ordem para times pequenos.
- Manter documentação e, quando existirem, diagramas versionados e revisáveis por pull request.

## Fluxo mínimo

```text
React/Next.js → BFF Node.js/TypeScript → Serviços de domínio
                                      └──→ Integrações externas, quando necessário
```

O front consome exclusivamente o BFF. O BFF agrega e adapta respostas, mas não
contém regra de negócio nem acessa diretamente o banco de domínio. Serviços de
domínio são donos da regra e dos dados.
