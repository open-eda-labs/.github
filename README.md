# .github

Repositório especial da organização `open-eda-labs`. Guarda o perfil público e os padrões que os demais repositórios herdam.

## Conteúdo

| Caminho | Função |
| --- | --- |
| `profile/README.md` | Perfil público da organização |
| `.github/ISSUE_TEMPLATE/` | Issue forms padrão (`tarefa`, `bug`); issues em branco desabilitadas |
| `.github/PULL_REQUEST_TEMPLATE.md` | Template padrão de PR |
| `.github/CODEOWNERS` | Dono padrão do código |
| `.github/workflows/lint.yml` | Workflow reutilizável de lint (yamllint e markdownlint) |
| `.github/workflows/ci.yml` | CI deste repositório |
| `SECURITY.md` | Como reportar vulnerabilidades |
| `.editorconfig`, `.yamllint`, `.markdownlint-cli2.yaml`, `.gitignore` | Configuração de base |

## Como os padrões são herdados

- Issue forms, template de PR e `SECURITY.md` valem como padrão da organização para todo repositório que não tenha o próprio arquivo equivalente. Um arquivo no repositório sobrescreve o padrão.
- `CODEOWNERS`, `.editorconfig`, `.yamllint`, `.markdownlint-cli2.yaml` e `.gitignore` não são herdados pelo GitHub. Cada repositório copia o seu.
- O workflow de lint é reutilizável. Um repositório o chama assim:

```yaml
jobs:
  lint:
    uses: open-eda-labs/.github/.github/workflows/lint.yml@main
```

  Se este repositório for privado, o acesso a Actions dele precisa estar liberado nas configurações da organização para ser chamado de outros repositórios; isso ainda não foi configurado, e por isso o `ci.yml` daqui não chama o reutilizável. O workflow usa o `.yamllint` e o `.markdownlint-cli2.yaml` do repositório chamador. A referência `@main` deve virar SHA de commit (D-40).

## Regras

Dados sintéticos ou públicos, nada de empresa (D-24, D-27). Tudo como código, versões pinadas, segredos fora do Git (D-40). Mudanças por PR; o agente nunca faz merge (D-02, D-31). Classes D0 a D3, e D3 nunca vai a modelo, trace ou MLflow (D-42). Plano: [PLANO_MESTRE.md](https://github.com/open-eda-labs/open-eda-labs.github.io/blob/main/docs/PLANO_MESTRE.md).
