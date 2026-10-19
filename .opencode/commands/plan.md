---
description: Planeja uma tarefa ou objetivo e registra dependências e critérios de aceite.
agent: coordinator
---

Planeje o seguinte objetivo ou tarefa:

$ARGUMENTS

Leia `AGENTS.md`, consulte o estado da squad e confira o repositório antes de propor o plano.

Produza:

1. resultado esperado;
2. critérios de aceite verificáveis;
3. tarefas pequenas com dependências;
4. decisões técnicas que precisam ser avaliadas;
5. verificações relevantes;
6. riscos e pontos de aprovação humana;
7. quais tarefas podem ser paralelizadas com segurança.

Use subagents para análises independentes quando forem úteis. Não delegue implementação paralela sem delimitar arquivos, interfaces e worktrees. Atualize os registros da tarefa e o próximo passo no estado da squad.