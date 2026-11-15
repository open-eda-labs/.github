# .github

Repositório especial da organização `open-eda-labs`. Guarda o perfil público e as convenções que os demais repositórios seguem sem configurar nada.

## Conteúdo

| Caminho | Função |
| --- | --- |
| `profile/README.md` | Perfil público da organização e regras do laboratório |
| `.github/ISSUE_TEMPLATE/` | Issue form padrão (`tarefa`); issues em branco desabilitadas |
| `.github/PULL_REQUEST_TEMPLATE.md` | Template padrão de PR |
| `.github/workflows/lint.yml` | Workflow reutilizável de lint (yamllint, com a configuração embutida) |

## Como as convenções chegam aos outros repositórios

- O issue form e o template de PR valem para todo repositório da organização que não tenha o próprio.
- O lint é um workflow reutilizável; o `ci.yml` de cada repositório só o chama:

  ```yaml
  jobs:
    lint:
      uses: open-eda-labs/.github/.github/workflows/lint.yml@main
  ```

  A configuração do yamllint fica dentro do workflow: mudar uma regra é um PR aqui, não um por repositório. Se este repositório for privado, o acesso a Actions dele precisa estar liberado nas configurações da organização. A referência `@main` deve virar SHA de commit (D-40).
- `CODEOWNERS` e `.editorconfig` não são herdados pelo GitHub; cada repositório tem o seu.
