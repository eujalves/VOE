# Git Workflow

Padrão de branches, commits e Pull Requests do projeto. A chave do item no Jira conecta o trabalho ao painel de desenvolvimento.

## 1. Chave do Jira

Todo trabalho deve ter um item no Jira. Use a chave em maiúsculas:

```text
PROJ-123
```

A mesma chave deve aparecer no início:

- do nome da branch;
- de cada mensagem de commit;
- do título do Pull Request.

Se o item não existir, crie-o antes de começar. Não invente chaves.

O Jira só mostra os dados de desenvolvimento depois do `push`, e a sincronização pode levar alguns minutos.

Referência: [Referenciar itens do Jira no desenvolvimento](https://support.atlassian.com/jira-software-cloud/docs/reference-issues-in-your-development-work/)

## 2. Fluxo de desenvolvimento

A `main` é a branch principal e deve permanecer funcional. Toda alteração parte dela e volta por um Pull Request revisado.

- Faça incrementos pequenos e fáceis de revisar.
- Mantenha as branches curtas e abra o PR cedo.
- Divida funcionalidades grandes em vários PRs, cada um com um único objetivo.
- Após o merge, remova a branch.
- Se algo quebrar a `main`, priorize a correção ou a reversão.

### Passo a passo

```bash
git checkout main
git pull
git checkout -b PROJ-123-feat/tela-login

git add .
git commit -m "PROJ-123 feat: implementar tela de login"
git push -u origin PROJ-123-feat/tela-login
```

Abra o Pull Request para `main` com o título:

```text
PROJ-123 Implementar tela de login
```

## 3. Branches

Formato:

```text
PROJ-XXX-tipo/descricao-curta
```

### Tipos

| Tipo | Uso |
|---|---|
| `feat` | Nova funcionalidade |
| `fix` | Correção de bug |
| `refactor` | Refatoração sem mudança de comportamento |
| `style` | Alterações visuais ou de estilo |
| `test` | Testes |
| `docs` | Documentação |
| `chore` | Configurações, dependências ou manutenção |

### Regras

- chave do Jira em maiúsculas;
- tipo em minúsculas;
- descrição curta, em minúsculas, com palavras separadas por `-`;
- sem espaços, acentos ou caracteres especiais.

Evite:

```text
feat/PROJ-123-tela-login
proj-123-feat/tela-login
PROJ-123/novaTela
```

Prefira:

```text
PROJ-123-feat/tela-login
```

## 4. Commits

Formato:

```text
PROJ-XXX tipo: descrição
```

Exemplos:

```text
PROJ-123 feat: implementar formulário de login
PROJ-210 fix: corrigir barra de navegação no celular
PROJ-500 docs: documentar variáveis de ambiente
```

- Um commit por alteração lógica.
- Verbo no infinitivo, sem ponto final.
- Não misture alterações não relacionadas.

Evite:

```text
PROJ-123 ajustes
PROJ-123 fix: correções
```

Prefira:

```text
PROJ-123 fix: tratar credenciais de login inválidas
```

## 5. Pull Requests

Formato do título:

```text
PROJ-XXX Descrição objetiva
```

O PR deve ter `main` como destino, focar em um único item do Jira e explicar o que mudou e como validar.

Preencha o [template do Pull Request](pull_request_template.md) com:

- link do Jira;
- links do Confluence e do Figma (ou `Não aplicável`);
- objetivo e resumo das alterações;
- instruções de teste e evidências;
- checklist.

### Evidências

PRs que alteram a interface devem incluir screenshots (computador e celular, quando relevante). Alterações internas normalmente não precisam.

## 6. CI, testes, build e deploy

Ainda **a definir**. O merge em `main` não faz deploy automático.

## 7. Antes de abrir o PR

```bash
git checkout main
git pull
git checkout PROJ-123-feat/tela-login
git merge main
```

Resolva conflitos, revise o diff e registre como a alteração foi validada.

## 8. Revisão

- Responda aos comentários.
- Corrija na mesma branch, com a mesma chave do Jira.
- Não abra outro PR para corrigir o atual.

## Resumo

```text
Jira:         PROJ-123 - Criar tela de login
Branch:       PROJ-123-feat/tela-login
Commit:       PROJ-123 feat: implementar formulário de login
Pull Request: PROJ-123 Implementar tela de login
```
