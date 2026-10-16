# trabalho-devops

[![CI](https://github.com/Frivcoom111/trabalho-devops/actions/workflows/blank.yml/badge.svg)](https://github.com/Frivcoom111/trabalho-devops/actions/workflows/blank.yml)
[![Changelog](https://github.com/Frivcoom111/trabalho-devops/actions/workflows/changelog.yml/badge.svg)](https://github.com/Frivcoom111/trabalho-devops/actions/workflows/changelog.yml)

Trabalho da disciplina **Ferramentas de DevOps Avançado** (UniALFA, 2º ano, 2º bimestre) com o professor Fernando.

O objetivo é automatizar tarefas do repositório com **GitHub Actions**.

## Workflows

| Workflow | Quando roda | O que faz |
|----------|-------------|-----------|
| **CI** | Push e Pull Request na `main` | Executa os passos de build/teste do projeto |
| **Changelog** | Push na `main` ou manualmente | Gera o `CHANGELOG.md` a partir do histórico de commits e commita de volta no repositório |

## Como funciona o Changelog

1. Faz o checkout do repositório com o histórico completo (`fetch-depth: 0`)
2. Roda `git log` e escreve cada commit no formato:
   ```
   - AAAA-MM-DD: mensagem do commit (hash) — autor
   ```
3. Commita o `CHANGELOG.md` como `github-actions[bot]`. O commit leva `[skip ci]` na mensagem para não disparar os outros workflows.

O resultado fica em [CHANGELOG.md](CHANGELOG.md).

## Como testar

1. Faça um commit na `main`, ou o merge de um PR.
2. Abra a aba **Actions** e acompanhe o workflow **Changelog**.
3. Quando terminar, rode `git pull`. O `CHANGELOG.md` atualizado vai aparecer.

Para rodar manualmente: **Actions → Changelog → Run workflow**.

> Se o push da action falhar com erro 403, ative **Settings → Actions → General → Workflow permissions → Read and write permissions**.

## Estrutura

```
.github/
└── workflows/
    ├── blank.yml       # CI
    └── changelog.yml   # Geração do changelog
README.md
CHANGELOG.md            # Gerado automaticamente
```
