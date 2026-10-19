---
name: memory-management
description: Orienta agentes a ler e atualizar o estado, tarefas, decisões e handoffs da squad sem perder a fonte de verdade.
---

# Gestão da memória da squad

Use esta skill ao iniciar ou retomar trabalho, delegar tarefas, concluir etapas ou atualizar arquivos em `.squad/`.

## Fontes de verdade

- `AGENTS.md`: regras comuns do projeto.
- `.squad/project-state.json`: resumo do estado atual e próximo passo.
- `.squad/tasks/`: escopo e progresso detalhado de cada tarefa.
- `.squad/handoffs/`: contexto necessário para transferir uma tarefa.
- `docs/decisions/`: decisões duradouras e suas justificativas.
- Código, testes e Git: evidência do que foi realmente alterado e verificado.

A memória ajuda a localizar e entender o trabalho. Ela não substitui a inspeção do repositório.

## Ao começar ou retomar

1. Leia `AGENTS.md`.
2. Leia `.squad/project-state.json`, se existir.
3. Localize o arquivo da tarefa atual.
4. Leia as decisões e os handoffs referenciados.
5. Confira o Git, a worktree e os arquivos relevantes.
6. Compare os registros com o estado atual. Corrija informações desatualizadas em vez de repeti-las como fatos.

Se o estado não puder ser confirmado, registre-o como desconhecido e investigue antes de avançar em uma ação dependente.

## Ao registrar uma tarefa

Cada tarefa deve incluir:

- ID estável e título objetivo;
- resultado esperado;
- status;
- responsável;
- dependências;
- área incluída e excluída do escopo;
- critérios de aceite;
- evidências;
- bloqueios;
- worktree ou sessão associada, se houver;
- data de atualização em ISO 8601.

Critérios de aceite devem ser observáveis. Evite itens vagos como “funciona bem”.

## Ao registrar um handoff

O handoff deve permitir que outro agente continue sem ler a conversa anterior. Inclua:

- ID da tarefa e objetivo;
- contexto confirmado;
- decisões relevantes e links;
- arquivos examinados ou alterados;
- verificações executadas e seus resultados;
- hipóteses ainda não confirmadas;
- bloqueios;
- próxima ação recomendada;
- sessão ou worktree associada, se aplicável.

## Ao registrar uma decisão

Crie um arquivo em `docs/decisions/` quando uma decisão técnica ou de produto for duradoura e puder afetar trabalho futuro. Inclua:

- contexto e problema;
- opções consideradas;
- decisão;
- consequências e riscos;
- data e status.

Não registre toda escolha de implementação como uma decisão arquitetural.

## Ao concluir uma etapa

1. Confirme os resultados no repositório.
2. Registre verificações reais, não planejadas.
3. Atualize o arquivo da tarefa.
4. Atualize `.squad/project-state.json` com o estado e o próximo passo.
5. Atualize ou crie decisões e handoffs necessários.
6. Mantenha o estado geral curto e sem duplicar documentos.

## Concorrência

Não permita que agentes paralelos escrevam simultaneamente em `project-state.json`. Cada agente entrega seu resultado ao coordenador; o coordenador consolida o estado geral. Para trabalho paralelo, mantenha arquivos de tarefa separados.