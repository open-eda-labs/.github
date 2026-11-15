# open-eda-labs

Laboratório pessoal de workflows agênticos disparados por eventos: alertas por webhook e varredura de vulnerabilidades. Roda com Argo Workflows e padrões abertos. Um repositório por peça trocável; todas dependem só do contrato versionado em `triage-contract`.

## Repositórios

| Repositório | O que contém |
| --- | --- |
| [`.github`](https://github.com/open-eda-labs/.github) | Perfil, templates e CI padrão da organização |
| [`triage-contract`](https://github.com/open-eda-labs/triage-contract) | Schemas CloudEvents e de recomendação, AGENTS.md, skills |
| [`triage-eval`](https://github.com/open-eda-labs/triage-eval) | Replay, gabarito JSONL, suítes de avaliação |
| [`intake-adapter`](https://github.com/open-eda-labs/intake-adapter) | Autenticação, normalização, dedup, limites |
| [`agent-workflows`](https://github.com/open-eda-labs/agent-workflows) | WorkflowTemplates de triagem e do vuln fixer Maven |
| [`lab-infra`](https://github.com/open-eda-labs/lab-infra) | k3s, Argo, InfluxDB, Grafana, MLflow como código |
| [`demo-service`](https://github.com/open-eda-labs/demo-service) | App Maven com CVEs reais conhecidas; alvo do vuln fixer e da injeção de falhas |
| [`agent-step-images`](https://github.com/open-eda-labs/agent-step-images) | Imagens OCI do passo de agente |
| [`open-eda-labs.github.io`](https://github.com/open-eda-labs/open-eda-labs.github.io) | Base das sessões e site |

## Regras

- Só dados sintéticos ou públicos. Nenhum dado, código ou nome de empresa (D-24, D-27).
- Tudo como código, versões pinadas, segredos fora do Git (D-40).
- Mudanças entram por PR. O agente nunca faz merge; escreve só como branch + PR draft (D-02, D-31).
- Classes de dado: D0 operacional, D1 interno, D2 pessoal, D3 proibido. D3 nunca vai a modelo, trace ou MLflow (D-42).
- Convenção antes de configuração: YAML para configuração, schemas e fixtures; gRPC entre serviços próprios, HTTP+JSON só nas bordas externas (webhooks de alerta e API do modelo).

## Plano

Fonte da verdade: [PLANO_MESTRE.md](https://github.com/open-eda-labs/open-eda-labs.github.io/blob/main/docs/PLANO_MESTRE.md).
