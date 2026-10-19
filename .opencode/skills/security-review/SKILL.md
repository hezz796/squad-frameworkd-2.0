---
name: security-review
description: Revisa mudanças e configurações considerando riscos de segurança relevantes ao escopo.
---

# Revisão de segurança

Use esta skill ao revisar uma mudança que afete dados, identidade, permissões, dependências, configuração, rede ou operações privilegiadas.

## Escopo

Comece pelo diff e pelos fluxos que ele altera. Considere riscos relevantes ao projeto, sem transformar a revisão em uma lista genérica desconectada do código.

Verifique, quando aplicável:

- autenticação, autorização e limites entre usuários;
- validação, normalização e uso de entradas;
- exposição de dados pessoais, credenciais ou segredos;
- permissões de arquivos, ferramentas e serviços;
- tratamento de erros, logs e mensagens;
- dependências, configuração e valores padrão;
- efeitos de operações destrutivas ou privilegiadas;
- compatibilidade com requisitos de segurança documentados.

## Evidências

Para cada possível achado:

1. identifique o arquivo ou fluxo afetado;
2. descreva a condição necessária;
3. explique o impacto;
4. cite a evidência observada;
5. diferencie defeito confirmado de risco que exige validação.

Não afirme que algo é seguro sem verificar o comportamento relevante. Não exponha segredos em relatórios.

## Limites

A revisão é somente de leitura. Não faça testes contra serviços externos, produção ou dados reais. Para verificações que dependam de autorização, solicite ao coordenador um ambiente seguro e autorizado.

## Retorno

Organize achados por severidade e indique correções ou mitigações possíveis. Informe também o escopo coberto, o que não foi verificado e as incertezas restantes.