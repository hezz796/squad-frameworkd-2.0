---
description: Prepara os artefatos de uma release conforme a política do projeto.
agent: coordinator
---

Prepare a release indicada:

$ARGUMENTS

Leia `AGENTS.md`, a política de release do projeto e o estado atual da squad. Confira o escopo, as tarefas concluídas, as decisões relevantes, o estado do Git e as verificações registradas.

Peça ao agente `release-manager` que prepare os artefatos necessários, como notas de release ou atualização de changelog, seguindo os padrões existentes.

Ao receber o resultado:

- confirme que as notas correspondem às mudanças e evidências do repositório;
- registre arquivos preparados, verificações, limitações e bloqueios;
- atualize o estado da squad;
- informe qualquer ação que ainda dependa de aprovação humana.

Este command prepara a release. Não publique, crie tags remotas nem faça deploy sem autorização explícita.