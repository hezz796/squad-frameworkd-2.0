---
name: architecture
description: Avalia opções de arquitetura e tecnologia segundo os requisitos e as restrições do projeto.
---

# Análise de arquitetura

Use esta skill quando uma tarefa exigir escolher ou alterar uma tecnologia, interface, limite de serviço, modelo de dados ou padrão arquitetural.

## Primeiro entenda o contexto

1. Leia requisitos, critérios de aceite e restrições.
2. Inspecione a arquitetura e a stack atuais.
3. Identifique o problema concreto que a decisão precisa resolver.
4. Evite uma reescrita ou abstração que não seja necessária para esse problema.

## Compare opções

Escolha critérios relevantes ao caso, por exemplo:

- adequação aos requisitos;
- compatibilidade com o sistema existente;
- segurança e privacidade;
- complexidade de desenvolvimento e operação;
- custo e disponibilidade de competências;
- desempenho e escalabilidade necessários;
- manutenção e facilidade de teste;
- portabilidade ou dependência de fornecedor.

Compare apenas opções viáveis. Explique as consequências mais importantes e as incertezas. Se a evidência for insuficiente, proponha uma investigação pequena ou um protótipo.

## Recomendação

A recomendação deve:

- responder aos requisitos e restrições conhecidos;
- explicar por que foi escolhida;
- registrar trade-offs e riscos;
- indicar os impactos sobre implementação, operação e migração;
- separar decisão técnica de aprovação de produto ou negócio.

## ADR

Proponha um registro em `docs/decisions/` para decisões duradouras. Inclua contexto, alternativas, decisão, consequências e estado. Não crie ADR para toda escolha local de implementação.

## Limites

Não implemente a arquitetura durante a análise. Se um requisito essencial estiver indefinido, retorne a pergunta ao coordenador antes de tratar uma hipótese como decisão.