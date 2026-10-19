---
description: Solicita revisão independente das mudanças atuais ou de um escopo indicado.
agent: coordinator
---

Revise este escopo:

$ARGUMENTS

Leia `AGENTS.md`, os critérios relevantes e o diff atual. Se o escopo não tiver sido especificado, revise as mudanças da tarefa ativa.

Delegue a revisão ao agente `reviewer`, que deve trabalhar em modo de leitura. Para riscos de segurança, solicite também a revisão de `security-reviewer`.

Peça que os achados sejam ordenados por severidade e incluam arquivo ou área, cenário, impacto e evidência. Não peça ao revisor que altere o código.

Ao receber o resultado:

- transforme achados acionáveis em tarefas de correção;
- preserve os achados e limitações na tarefa correspondente;
- registre a revisão no estado da squad;
- informe se a entrega está aprovada, reprovada ou aprovada com limitações.