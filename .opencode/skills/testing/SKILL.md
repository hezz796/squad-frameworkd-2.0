---
name: testing
description: Planeja e executa verificações relacionadas aos critérios de aceite sem confundir testes planejados com evidências.
---

# Verificação e testes

Use esta skill ao planejar QA, verificar uma mudança ou preparar evidências para concluir uma tarefa.

## Planejamento

1. Leia os critérios de aceite.
2. Identifique os testes e verificações existentes.
3. Relacione cada critério a uma evidência possível.
4. Escolha verificações proporcionais ao risco e ao escopo.
5. Verifique se o ambiente e as dependências necessários estão disponíveis.

Prefira os comandos documentados pelo projeto e os testes já existentes. Não crie uma nova infraestrutura de testes sem necessidade para a tarefa.

## Execução

- Execute as verificações relevantes para a mudança.
- Registre o comando exato e o resultado observado.
- Não declare sucesso com base apenas em leitura de código ou em testes que não foram executados.
- Se uma verificação não puder ser executada, registre o motivo.
- Se houver falha, determine se ela está relacionada à mudança ou parece preexistente; não esconda a falha.

## Revisão dos critérios

Para cada critério de aceite, registre:

- passou, falhou, não executado ou não aplicável;
- evidência correspondente;
- limitações ou dependências externas.

## Fechamento

Envie ao coordenador um resumo dos resultados, falhas, riscos residuais e verificações pendentes. O agente que implementou a tarefa não deve ser a única fonte de revisão independente quando o plano exigir QA ou revisão.