---
description: Verifica os critérios de aceite de uma tarefa e registra o resultado.
agent: coordinator
---

Verifique a tarefa indicada:

$ARGUMENTS

Leia o brief, os critérios de aceite e o diff atual. Confira as verificações existentes e escolha QA, revisão de código ou revisão de segurança conforme o risco.

Delegue a verificação a um agente independente quando apropriado. Não peça ao agente que implementou a tarefa para ser o único revisor dela.

Para cada critério, registre:

- resultado;
- evidência;
- comando executado, quando houver;
- limitação ou motivo para não executar.

Se houver achados, converta-os em tarefas de correção com escopo e critérios explícitos. Atualize o status da tarefa e o estado geral. Só marque como concluída quando os critérios forem atendidos ou as limitações estiverem claramente registradas e aceitas conforme a política do projeto.