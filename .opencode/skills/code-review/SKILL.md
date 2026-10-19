---
name: code-review
description: Revisa um diff em modo somente leitura e relata achados acionáveis com evidência.
---

# Revisão de código

Use esta skill para revisar alterações existentes de forma independente.

## Preparação

- Leia os critérios de aceite e as decisões relevantes.
- Examine o diff e o contexto mínimo necessário.
- Confirme quais arquivos fazem parte do escopo.
- Trabalhe em modo somente leitura.

## Procurar

Priorize:

1. comportamento incorreto;
2. perda ou corrupção de dados;
3. problemas de autenticação, autorização ou exposição de informação;
4. regressões e casos de erro ausentes;
5. incompatibilidade com requisitos, contratos ou decisões;
6. problemas de manutenção com consequência concreta provável.

## Achados

Um achado deve incluir:

- severidade;
- arquivo, linha ou área;
- condição para reproduzir;
- comportamento observado;
- impacto;
- relação com requisito ou risco.

Não reporte preferências pessoais como defeitos. Se depender de uma hipótese, identifique-a. Se não encontrar problemas, diga o que foi revisado e quais limitações permaneceram.

## Retorno

Ordene os achados por impacto. Não altere arquivos. Envie as conclusões ao coordenador para que ele decida sobre correções e estado da tarefa.