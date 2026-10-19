---
name: project-intake
description: Organiza o pedido inicial em objetivo, requisitos, restrições, hipóteses e critérios de aceite.
---

# Intake do projeto

Use esta skill ao iniciar um projeto, receber um novo objetivo ou identificar que o escopo atual mudou materialmente.

## Investigue o contexto

1. Leia `AGENTS.md` e o estado atual em `.squad/project-state.json`.
2. Confira os arquivos e a estrutura existentes no repositório.
3. Consulte requisitos e decisões que possam afetar o pedido.
4. Separe o que foi informado pelo usuário do que foi observado no repositório.

Não leia valores de arquivos de segredo. Registre apenas que um arquivo ou configuração sensível existe, se isso for relevante.

## Defina o pedido

Registre:

- problema ou necessidade;
- resultado esperado;
- usuários, sistemas ou fluxos afetados, quando conhecidos;
- restrições funcionais, técnicas, operacionais e de segurança;
- critérios de aceite observáveis;
- dependências, riscos e limitações;
- fatos confirmados;
- hipóteses reversíveis;
- perguntas bloqueantes.

Não escolha a stack antes de entender os requisitos e as capacidades de operação disponíveis. A recomendação tecnológica pertence à etapa de arquitetura.

## Ambiguidades

Pergunte ao usuário quando a resposta puder alterar materialmente o produto, o escopo, a segurança ou uma decisão difícil de reverter.

Para detalhes pequenos e reversíveis, proponha uma hipótese simples, identifique-a como hipótese e peça ao coordenador que a registre antes de depender dela.

## Saída

Entregue ao coordenador um resumo de intake com:

1. objetivo;
2. requisitos e restrições;
3. critérios de aceite;
4. hipóteses;
5. perguntas bloqueantes;
6. riscos e dependências;
7. próximo passo recomendado.

Não implemente nesta etapa.