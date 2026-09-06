# Skills de web, BFF, Node.js e segurança
Data: 2026-09-06
Agente/autor: Felipe Paniago

## Objetivo
Criar skills reutilizáveis para orientar trabalho em BFF, React, Node.js e boas
práticas de segurança e APIs.

## O que foi feito
- Criada `skills/bff/SKILL.md` para limites, contratos e adaptação de payloads.
- Criada `skills/react/SKILL.md` para componentes, Next.js, estados e contratos de tela.
- Criada `skills/node/SKILL.md` para serviços, falhas, configuração e operação.
- Criada `skills/security-apis/SKILL.md` para autenticação, autorização, isolamento,
  validação, segredos e integrações.
- Adicionados metadados de interface para as quatro skills.
- Executado o validador oficial; as quatro skills foram consideradas válidas.

## Decisões tomadas (e por quê)
As skills ficaram separadas por responsabilidade para permitir invocação seletiva
sem carregar orientações de segurança, UI ou backend quando não forem necessárias.

## Suposições adotadas
As skills seguem a stack documentada no projeto: React/Next.js, BFF Node.js/TypeScript
e serviços de domínio Node.js/TypeScript.

## Lacunas que continuam abertas
Não há requisitos de framework, biblioteca de validação, observabilidade ou provedor
de identidade específicos; essas escolhas continuam dependentes de cada projeto.

## Próximo passo sugerido
Usar as skills em uma tarefa real e ajustar apenas regras que se mostrarem insuficientes.
