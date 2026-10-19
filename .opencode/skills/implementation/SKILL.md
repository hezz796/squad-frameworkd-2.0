---
name: implementation
description: Procedimento para implementar tarefas pequenas e verificáveis, respeitando escopo, decisões e execução paralela.
---

# Implementação da squad

Use esta skill quando uma tarefa delegada exigir alterações no código, configuração ou documentação do produto.

## Preparação

1. Leia o brief e os critérios de aceite.
2. Consulte `AGENTS.md`, instruções locais, requisitos e decisões relevantes.
3. Examine os arquivos e padrões existentes.
4. Confira o Git e a worktree antes de editar.
5. Identifique verificações existentes para a área afetada.

Se houver ambiguidade que altere materialmente a solução, informe o coordenador antes de fazer mudanças dependentes.

## Escolha da abordagem

- Prefira a menor mudança que atenda aos critérios de aceite.
- Siga os padrões existentes quando forem adequados.
- Não suponha uma stack; descubra-a no repositório e nos requisitos.
- Evite dependências novas, refatorações amplas e alterações fora do escopo.
- Se surgir uma decisão duradoura não coberta pela documentação, proponha-a ao coordenador para registro.

## Execução

- Faça alterações localizadas e fáceis de revisar.
- Preserve comportamento não relacionado.
- Mantenha compatibilidade com interfaces e contratos existentes, salvo se a tarefa permitir uma mudança incompatível.
- Não edite arquivos que estejam sendo alterados por outra tarefa paralela.
- Se uma alteração exigir expandir o escopo, peça ao coordenador que atualize o brief.

## Verificação

Execute as verificações relevantes que já existem no projeto. Relacione cada resultado aos critérios de aceite.

Se a verificação falhar:

- confirme se a falha foi introduzida pela mudança;
- corrija quando estiver dentro do escopo;
- caso contrário, reporte a falha e evidências ao coordenador.

Não declare que uma verificação passou sem executá-la.

## Entrega

Retorne ao coordenador:

- resumo do que foi implementado;
- arquivos alterados;
- critérios atendidos;
- verificações executadas e resultados;
- decisões ou hipóteses;
- riscos, limitações e trabalho restante.