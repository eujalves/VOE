# Contributing

Resumo dos padrões de contribuição. O fluxo completo está em [Git Workflow](git.flow.md).

Antes de contribuir, consulte:

- **Jira**: tarefas, bugs e acompanhamento;
- **Confluence**: requisitos e documentação;
- **Figma**: protótipos e interface.

## Fluxo

Todo trabalho parte da `main` e volta por um Pull Request revisado. Mantenha as branches curtas e remova-as após o merge.

Todo trabalho precisa de um item no Jira. Use a chave em maiúsculas (ex.: `PROJ-123`) na branch, em cada commit e no título do PR. Se o item não existir, crie-o antes.

```bash
git checkout main
git pull
git checkout -b PROJ-123-feat/tela-login

git add .
git commit -m "PROJ-123 feat: implementar tela de login"
git push -u origin PROJ-123-feat/tela-login
```

Abra o PR para `main` com o título:

```text
PROJ-123 Implementar tela de login
```

## Antes de abrir o PR

```bash
git checkout main
git pull
git checkout PROJ-123-feat/tela-login
git merge main
```

Revise o diff e preencha o template do PR com:

- link do Jira;
- links do Confluence e do Figma, quando aplicável;
- instruções de teste e evidências;
- atualização do `CHANGELOG.md`, quando relevante.

## Revisão

- Responda aos comentários.
- Corrija na mesma branch, com a mesma chave do Jira.
- Mantenha o PR focado em um único objetivo.

## Resumo

```text
Jira:         PROJ-123 - Criar tela de login
Branch:       PROJ-123-feat/tela-login
Commit:       PROJ-123 feat: implementar tela de login
Pull Request: PROJ-123 Implementar tela de login
```

Padrão baseado na documentação da Atlassian sobre a [integração do Jira com o Git](https://support.atlassian.com/jira-software-cloud/docs/reference-issues-in-your-development-work/).
