# Squad Framework 2.0

Framework de squad autônoma e agnóstica a stack para desenvolvimento de software usando OpenCode.

Esta squad conduz o ciclo completo de desenvolvimento: entendimento, planejamento, arquitetura, implementação, verificação, revisão e preparação de release. Ela **não presume** linguagem, framework, banco de dados ou provedor: a stack é decidida a cada projeto com base nos requisitos, nas restrições e nas capacidades de operação disponíveis.

## Objetivo

Automatizar a coordenação do trabalho de desenvolvimento por meio de um agente coordenador e especialistas delegados, mantendo:

- rastreabilidade do trabalho em arquivos de memória (`.squad/`);
- separação entre quem implementa e quem verifica;
- decisões técnicas duradouras documentadas (`docs/decisions/`);
- intervenção humana nos pontos que alteram produto, segurança ou operação.

As regras comuns da squad estão em [`AGENTS.md`](AGENTS.md). A configuração dos agentes está em [`opencode.jsonc`](opencode.jsonc).

## Estrutura do repositório

```text
.
├── AGENTS.md                       # Regras comuns da squad e do projeto
├── README.md                       # Este arquivo
├── opencode.jsonc                  # Configuração de agentes e permissões
├── .gitignore
├── .opencode/
│   ├── agents/                     # Definição de cada agente (prompt e permissões)
│   │   ├── coordinator.md
│   │   ├── product-analyst.md
│   │   ├── architect.md
│   │   ├── implementer.md
│   │   ├── qa.md
│   │   ├── reviewer.md
│   │   ├── security-reviewer.md
│   │   └── release-manager.md
│   ├── commands/                   # Commands invocáveis no OpenCode
│   │   ├── start.md  plan.md  implement.md  verify.md
│   │   ├── review.md  resume.md  release.md
│   └── skills/                     # Skills carregadas conforme a necessidade
│       ├── project-intake/  requirements/  architecture/
│       ├── implementation/  testing/  code-review/
│       ├── security-review/  release/  memory-management/
├── .squad/                         # Memória persistente da squad
│   ├── project-state.json          # Estado geral e próximo passo
│   ├── schema/                     # JSON Schema do estado
│   ├── tasks/                      # Uma tarefa por arquivo (TASK-*.json)
│   └── handoffs/                   # Transferências de contexto (HANDOFF-*.json)
└── docs/
    └── decisions/                  # ADRs (Architecture Decision Records)
```

## Agentes

O agente **`coordinator`** é o agente primário e padrão (`default_agent`). Ele lê o estado, planeja, delega aos especialistas, integra resultados e mantém a memória. Os demais são subagentes acionados por ele.

| Agente | Função | Permissões relevantes |
| --- | --- | --- |
| `coordinator` | Coordena o ciclo, mantém o estado e delega tarefas. | Pode acionar subagentes. |
| `product-analyst` | Transforma pedidos em requisitos, escopo e critérios de aceite verificáveis. | Não implementa código. |
| `architect` | Avalia opções técnicas e registra decisões sem implementar a solução. | Não implementa a solução. |
| `implementer` | Implementa tarefas delimitadas e retorna mudanças e evidências verificáveis. | Não faz commit, publicação ou deploy sem autorização explícita. |
| `qa` | Verifica critérios de aceite, testes e regressões. | Sem edição de arquivos; shell sob confirmação. |
| `reviewer` | Revisa mudanças e relata defeitos, regressões e riscos de manutenção. | Somente leitura; shell restrito a `git status`, `git diff` e `git log`. |
| `security-reviewer` | Analisa riscos de segurança em mudanças e configurações. | Somente leitura; shell restrito a `git status`, `git diff` e `git log`. |
| `release-manager` | Prepara notas e artefatos de release conforme a política do projeto. | Não publica, cria tag remota nem faz deploy sem autorização. |

Ponto central do modelo: **quem implementa não é o único revisor da própria tarefa**. QA, revisão de código e revisão de segurança são sempre delegados a agentes independentes, em modo de leitura.

## Skills

Skills ficam em `.opencode/skills/<nome>/SKILL.md` e são carregadas conforme a necessidade de cada etapa:

| Skill | Quando usar |
| --- | --- |
| `project-intake` | Ao iniciar um projeto, receber um novo objetivo ou identificar mudança material de escopo. |
| `requirements` | Ao converter pedidos em requisitos e critérios de aceite claros e verificáveis. |
| `architecture` | Quando a tarefa exigir escolher ou alterar tecnologia, interface, limite de serviço, modelo de dados ou padrão arquitetural. |
| `implementation` | Quando a tarefa delegada exigir alterações em código, configuração ou documentação do produto. |
| `testing` | Ao planejar QA, verificar uma mudança ou preparar evidências para concluir uma tarefa. |
| `code-review` | Para revisar alterações existentes de forma independente e somente leitura. |
| `security-review` | Ao revisar mudanças que afetem dados, identidade, permissões, dependências, configuração, rede ou operações privilegiadas. |
| `release` | Para preparar uma release ou revisar seus artefatos. |
| `memory-management` | Ao iniciar ou retomar trabalho, delegar tarefas, concluir etapas ou atualizar arquivos em `.squad/`. |

## Commands

Commands ficam em `.opencode/commands/` e rodam pelo agente `coordinator`:

| Command | Função |
| --- | --- |
| `/start <pedido>` | Inicia um pedido, registra objetivo, restrições, hipóteses e critérios de aceite iniciais. |
| `/plan <objetivo>` | Planeja uma tarefa ou objetivo, com dependências e critérios de aceite. |
| `/implement <id>` | Implementa uma tarefa planejada e registra mudanças e verificações. |
| `/verify <id>` | Verifica os critérios de aceite de uma tarefa e registra o resultado com evidência. |
| `/review [escopo]` | Solicita revisão independente das mudanças atuais ou de um escopo indicado. |
| `/resume` | Retoma o trabalho a partir dos registros e do estado atual do repositório. |
| `/release <versão>` | Prepara os artefatos de uma release (não publica). |

## Como iniciar e retomar um trabalho

**Iniciar** — envie `/start <pedido>`. O coordenador lê `AGENTS.md`, consulta `.squad/project-state.json` e confere o repositório antes de agir; em seguida separa objetivo, fatos confirmados, hipóteses, restrições, perguntas bloqueantes e critérios de aceite iniciais, criando um plano curto com tarefas e dependências explícitas.

**Ciclo típico**: `/start` → `/plan` → `/implement` → `/verify` (e `/review` quando houver risco) → encerramento da tarefa na memória → `/release` quando aplicável.

**Retomar** — envie `/resume`. O coordenador relê `AGENTS.md`, `.squad/project-state.json`, a tarefa atual, handoffs e decisões referenciadas; confere Git, worktrees e arquivos relevantes; e confere se os registros ainda correspondem ao estado real. Duas regras explícitas valem aqui: não se presume que uma sessão ou processo ainda está ativo só porque aparece na memória, e não se repete trabalho já concluído sem verificar o repositório. Divergências são corrigidas na memória antes de prosseguir.

## A memória em `.squad/`

A memória persistente resume o trabalho e aponta para evidências; ela **não substitui** o código, os testes ou o Git. Fontes de verdade:

| Arquivo | Conteúdo |
| --- | --- |
| `AGENTS.md` | Regras comuns do projeto. |
| `.squad/project-state.json` | Resumo do estado atual, tarefas, decisões, trabalho ativo, verificações e próximo passo. |
| `.squad/tasks/TASK-*.json` | Escopo e progresso detalhado de cada tarefa. |
| `.squad/handoffs/HANDOFF-*.json` | Contexto para transferir uma tarefa a outro agente. |
| `docs/decisions/` | Decisões duradouras (ADRs) e suas justificativas. |
| Código, testes e Git | Evidência do que foi realmente alterado e verificado. |

O `project-state.json` segue o JSON Schema em `.squad/schema/project-state.schema.json` (`schema_version` `1.0`). O estado registra, entre outros campos:

- `project` — nome, objetivo e `stack_status` (`undecided`, `proposed` ou `selected`);
- `workflow` — `phase` (`intake`, `requirements`, `architecture`, `implementation`, `verification`, `release`, `maintenance`), `status` (`ready`, `in_progress`, `blocked`, `complete`), tarefa atual e próximo passo;
- `tasks`, `decisions`, `active_work`, `last_verified` (commits e verificações com evidência) e `blockers`.

Modelos de referência: `.squad/tasks/TASK-XXX.json` e `.squad/handoffs/HANDOFF-XXX.json`. Cada tarefa tem ID estável, resultado esperado, status, responsável, dependências, escopo incluído/excluído, critérios observáveis, evidências, bloqueios, worktree/sessão associada e data de atualização em ISO 8601.

Regra de concorrência: **agentes paralelos não escrevem simultaneamente no `project-state.json`**. Cada agente entrega seu resultado ao coordenador, que consolida o estado geral; o trabalho paralelo usa arquivos de tarefa separados.

## Ações que exigem aprovação humana

A squad avança sem confirmação a cada passo quando o escopo está claro, as mudanças são reversíveis e as verificações são possíveis. É necessária aprovação humana antes de:

- alterar significativamente o escopo ou os requisitos;
- executar uma migração destrutiva ou difícil de reverter;
- acessar, expor ou alterar dados sensíveis;
- publicar uma release ou fazer deploy em produção;
- assumir custos, compromissos ou impactos externos relevantes.

O coordenador ainda escala para uma pessoa quando falta uma informação que altere materialmente a solução, há conflito entre requisitos, as verificações falham repetidamente sem causa clara, ou existem mais de uma opção razoável com impacto relevante para o produto.

Sobre release, vale explícito: o command `/release` e o `release-manager` apenas **preparam** artefatos. Publicar, criar tags remotas ou fazer deploy sem autorização explícita está fora do escopo, e a preparação local de notas não equivale à aprovação para publicação.

Para hipóteses pequenas e reversíveis, a squad escolhe a opção mais simples, registra a hipótese e prossegue — sem esperar decisão humana.

## Critérios para concluir uma tarefa

Uma tarefa só é marcada como concluída quando os critérios de aceite foram verificados (ou suas limitações registradas e aceitas), as revisões exigidas pelo plano foram concluídas, os arquivos alterados e as verificações estão anotados, e o estado da tarefa e o próximo passo foram atualizados. Implementação terminada não é o mesmo que tarefa concluída.
