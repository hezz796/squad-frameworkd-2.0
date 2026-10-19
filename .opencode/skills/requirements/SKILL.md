---
name: requirements
description: Converte pedidos em requisitos, restrições e critérios de aceite claros e verificáveis.
---

# Análise de requisitos

Use esta skill ao iniciar um pedido, revisar escopo ou esclarecer o comportamento esperado antes de planejar a implementação.

## Levantamento

Identifique:

- problema ou necessidade;
- resultado esperado;
- usuários, sistemas ou fluxos afetados;
- comportamento funcional necessário;
- restrições de negócio, operação, segurança ou compatibilidade;
- critérios de aceite;
- dependências e riscos.

Consulte o comportamento existente e a documentação do projeto antes de propor alterações.

## Critérios de aceite

Cada critério deve descrever um resultado observável. Prefira critérios que possam ser verificados por um teste, inspeção ou demonstração.

Evite:

- critérios vagos como “fácil de usar” ou “performático” sem medida;
- misturar vários resultados independentes em um único critério;
- exigir uma tecnologia específica sem justificativa do projeto;
- confundir uma tarefa técnica com o resultado de produto.

Quando fizer sentido, cubra:

- caminho normal;
- entradas inválidas;
- ausência ou falha de dependências;
- permissões e autenticação;
- limites e estados extremos;
- compatibilidade com comportamentos existentes.

## Ambiguidades e hipóteses

Separe informações confirmadas, hipóteses e perguntas.

Pergunte à pessoa quando a resposta puder alterar materialmente o produto, o escopo, a segurança ou uma decisão difícil de reverter. Para detalhes de baixo impacto e reversíveis, proponha uma hipótese simples ao coordenador e registre-a.

## Retorno

Entregue um resumo curto, critérios de aceite, restrições, hipóteses, perguntas bloqueantes e dependências. Não implemente código nesta etapa.