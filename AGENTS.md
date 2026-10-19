# Instruções do projeto e da squad

## Objetivo

Este repositório usa uma squad de agentes do OpenCode para conduzir o ciclo de desenvolvimento de software: entendimento, planejamento, arquitetura, implementação, verificação, revisão e preparação de release.

A squad é agnóstica a tecnologia. A stack deve ser escolhida para cada projeto com base nos requisitos, nas restrições e nas capacidades de operação disponíveis.

## Fontes de verdade

Antes de iniciar uma tarefa:

1. Leia este arquivo e as instruções `AGENTS.md` aplicáveis ao diretório.
2. Consulte `.squad/project-state.json`, se existir.
3. Leia os requisitos e decisões relevantes em `docs/`.
4. Confira o estado atual do repositório e do Git.
5. Trate o código, os testes e o histórico do repositório como evidência do trabalho realizado. Não confie apenas no histórico da conversa ou em registros de memória.

A memória persistente resume o trabalho e aponta para evidências; ela não substitui o código, os testes ou o Git.

## Regras comuns

- O agente coordenador mantém o fluxo, a memória geral e a integração das tarefas.
- Especialistas trabalham apenas no escopo delegado e retornam resultados verificáveis.
- Cada tarefa deve ter objetivo, contexto, arquivos ou área de trabalho, dependências, critérios de conclusão e formato de retorno.
- Não delegue tarefas dependentes como se fossem independentes.
- Prefira mudanças pequenas, revisáveis e reversíveis.
- Não escolha uma tecnologia antes de entender as necessidades do projeto.
- Registre decisões técnicas duradouras em `docs/decisions/`.
- Registre progresso, bloqueios, evidências e próximo passo em `.squad/`.
- Não declare uma etapa concluída sem indicar o que mudou e como foi verificada.
- Se não for possível executar uma verificação, registre o motivo e o que ainda precisa ser confirmado.
- Não permita que agentes paralelos editem os mesmos arquivos ou atualizem simultaneamente o mesmo arquivo de estado geral.

## Paralelismo e sessões

- Use subagents em background para pesquisa, análise ou revisão independente que não bloqueie o próximo trabalho.
- Use subagents em foreground quando o coordenador precisar da resposta para tomar a próxima decisão.
- Use worktrees separadas para tarefas de implementação paralelas.
- O coordenador integra as alterações e executa ou delega as verificações integradas.
- Ao delegar, forneça um brief autossuficiente. Não presuma que o subagent conhece a conversa anterior.
- Registre o identificador da sessão ou da worktree, quando disponível, no registro da tarefa.
- Ao retomar uma sessão, confirme se a sessão, a worktree e os arquivos ainda existem antes de continuar.

## Aprovações humanas

A squad pode avançar sem confirmação a cada passo quando o escopo estiver claro, as mudanças forem reversíveis e as verificações forem possíveis.

Peça aprovação humana antes de:

- alterar significativamente o escopo ou os requisitos;
- executar uma migração destrutiva ou difícil de reverter;
- acessar, expor ou alterar dados sensíveis;
- publicar uma release ou fazer deploy em produção;
- assumir custos, compromissos ou impactos externos relevantes.

Se faltarem informações essenciais ou houver conflito entre requisitos, pare a etapa dependente e apresente uma pergunta específica com as opções necessárias.

## Critérios para concluir uma tarefa

Uma tarefa só pode ser marcada como concluída quando:

- os critérios de aceite foram verificados ou suas limitações foram registradas;
- as revisões exigidas pelo plano foram concluídas;
- os arquivos alterados e as verificações estão anotados;
- o estado da tarefa e o próximo passo foram atualizados.

## Commands da squad

- `/start <pedido>`: inicia o intake do pedido.
- `/plan <objetivo>`: cria plano, dependências e critérios de aceite.
- `/implement <id>`: inicia a implementação de uma tarefa planejada.
- `/verify <id>`: verifica os critérios e registra evidências.
- `/review [escopo]`: solicita revisão independente.
- `/resume`: retoma o trabalho a partir da memória persistente.
- `/release <versão>`: prepara os artefatos de release.

## Skills da squad

As skills ficam em `.opencode/skills/` e são carregadas conforme a necessidade:

- `project-intake`
- `requirements`
- `architecture`
- `implementation`
- `testing`
- `code-review`
- `security-review`
- `release`
- `memory-management`