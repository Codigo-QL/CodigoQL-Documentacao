# Políticas de Contribuição do Código-QL

Agradecemos seu interesse em contribuir com o Código-QL! Este projeto cresce com a ajuda da comunidade. Para manter tudo organizado, criamos este guia.

---

## Como Você Quer Contribuir?

Existem duas formas principais de ajudar o projeto. Escolha o caminho que mais se encaixa com seu objetivo:

### 1. Contribuindo com Conteúdo (Capítulos e Níveis)
Se você é um professor ou especialista em SQL e deseja adicionar novos exercícios, narrativas e desafios para os alunos, este é o seu caminho. O foco aqui é puramente no material didático.

Para começar, consulte nosso tutorial detalhado:

- **[➡️ Tutorial: Como Criar Novos Capítulos](tutorial.md)**

> **Importante:** Mesmo contribuindo apenas com conteúdo, pedimos que você siga nosso **Fluxo de Trabalho Padrão** (descrito abaixo) para criar branches e Pull Requests. Para o tipo de branch e commit, você pode usar `feat`, pois um novo capítulo é uma nova "feature" para os alunos.

### 2. Contribuindo com Código (Funcionalidades e Correções)
Se você é um desenvolvedor e quer ajudar a melhorar a plataforma, corrigir bugs, refatorar o código ou adicionar novas funcionalidades (como um novo tipo de feedback para o aluno, por exemplo), este é o seu caminho.

Para começar, procure uma **[Issue aberta no nosso repositório](https://github.com/Codigo-QL/CodigoQL-Documentacao/issues)** e siga o **Fluxo de Trabalho Padrão** descrito a seguir.

---

## Fluxo de Trabalho Padrão (Para Todos os Colaboradores)

Independente do tipo de contribuição, pedimos que siga o fluxo abaixo para manter o projeto organizado e rastreável.

### Issues

Toda contribuição deve começar com uma Issue.

- **Título:**
  `CÓDIGO - breve título`

  | Tipo         | Prefixo | Exemplo no título da issue              |
  |--------------|---------|-------------------------------------------|
  | User Story   | USX     | US4 - Exibir progresso do usuário         |
  | Bug          | BUGX    | BUG2 - Corrigir erro de login             |
  | Documentação | DOCX    | DOC1 - Atualizar guia do usuário          |
  | Tarefa       | TASKX   | TASK2 - Atualizar dependências do projeto |
  | Teste        | TESTX   | TEST3 - Cobertura de testes no cadastro   |
  | Melhoria     | IMPX    | IMP1 - Melhorar responsividade            |

- **Descrição:**
  A descrição deve ser clara e detalhada. Inclua contexto, critérios de aceite, passos para reprodução (em bugs) etc.

### Branches

- **Padrão de nome:**
  `tipo/CÓDIGO`

  | Tipo    | Descrição                                               | Exemplo       |
  |---------|---------------------------------------------------------|---------------|
  | `feat`  | Nova funcionalidade, capítulo ou nível                  | `feat/US3`    |
  | `bug`   | Correção de bug                                         | `bug/BUG2`    |
  | `doc`   | Mudanças na documentação                                | `doc/DOC1`    |
  | `build` | Mudanças em build, CI/CD, dependências                  | `build/TASK2` |
  | `chore` | Tarefas rotineiras, refatorações                        | `chore/TASK2` |
  | `test`  | Inclusão ou ajuste de testes                            | `test/TEST3`  |
  | `style` | Ajustes de formatação/estilo                            | `style/IMP1`  |

- **Fluxo de Trabalho:**

    1.  Sempre crie sua branch a partir da `main`.
    2.  Garanta que sua `main` local está atualizada: `git pull origin main`.
    3.  Crie a nova branch: `git checkout -b tipo/CODIGO`.

### Pull Requests (PRs)

- **Título:**
  Deve ser igual ao título da issue relacionada.

- **Descrição:**
    - **Relacione a Issue:** Use `Closes #42` para que o GitHub feche a issue automaticamente.
    - **Checklist antes de submeter:**
        - [ ] Minha branch está atualizada com a `main`.
        - [ ] A alteração resolve completamente a issue mencionada.
        - [ ] O título e os commits seguem os padrões definidos.

### Commits

- **Padrão de mensagem:**

    `tipo: mensagem do commit`
    
    **Exemplos:**

    - `feat: adiciona capítulo sobre funções de janela`
    - `bug: corrige validação da resposta do nível 3`
    - `doc: melhora o tutorial de criação de capítulos`