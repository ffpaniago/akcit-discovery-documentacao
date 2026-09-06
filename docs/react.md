# React — referência mínima

## React

React organiza a interface em componentes. Cada componente deve ter uma
responsabilidade clara e receber dados por propriedades. Estado local pertence
à interface quando não precisa ser compartilhado; estado compartilhado deve
ter dono explícito.

Boas regras para este projeto:

- componentes de apresentação não acessam APIs externas;
- chamadas de dados passam pelo BFF;
- tipos de entrada e saída ficam próximos do contrato da tela;
- regra de negócio pertence ao serviço de domínio;
- efeitos assíncronos e estados de carregamento, erro e vazio são explícitos.

## Next.js (hipótese, não container)

Next.js, **se o time já o usar**, fica *dentro* da camada de front-end. Não é
container separado nem decisão de stack deste starter. Pode organizar rotas,
layouts, renderização e carregamento de dados **no front**.

Se houver Next.js no recorte:

- rotas e layouts: Next.js, ainda na camada front;
- composição e apresentação: React;
- acesso a dados da aplicação: BFF;
- regra de negócio e persistência: serviços de domínio.

O front não deve chamar diretamente serviços de domínio ou APIs de terceiros.
Quando uma decisão exigir uma mudança nessa regra, registrar a mudança como
arquitetural e revisar o contrato Front–BFF.

## Fluxo mínimo

```text
Tela React → BFF Node.js/TypeScript → Serviço de domínio
                                      └──────→ Integração externa, quando necessário
```

## Decisões que precisam ser registradas

- onde os dados são carregados: servidor, cliente ou BFF;
- qual camada é dona de cada estado;
- formato e versão do contrato Front–BFF;
- tratamento de carregamento, erro, vazio e dados parciais;
- impacto operacional para o time pequeno;
- como a hipótese será verificada sem inventar métricas.

## Checklist de uma nova tela

- [ ] A rota e o layout têm dono definido.
- [ ] A tela consome somente o BFF.
- [ ] O contrato da resposta está documentado e versionado.
- [ ] Regra de negócio está fora do componente e do BFF.
- [ ] Estados de carregamento, erro e vazio estão definidos.
- [ ] Dados pessoais e escopo de tenant estão preservados.
- [ ] Teste de contrato ou verificação equivalente está definido.
