---
Created: 2025-06-18
---
### Definição de CI
É a automatização de etapas de integração, testes, entrega de uma aplicação

#### CI - Integração continua 
Basicamente uma prática que incentiva os devs a integrarem seu código em um repo compartilhado varias vezes ao dia. Cada integração dispara um processo de:
- Build (compilação)
- Execução de testes unitários e de integração
- Análise de qualidade de código (lint, cobertura, segurança)


Ferramentas para CI:
- GitHub Actions
- GitLab CI
- Jenkins
- CircleCI
- Travis CI
- Azure Pipelines

### Entrega Contínua (Continuous Delivery) ou Deploy Contínuo (Continuous Deployment)

Basicamente a etapa de envio para um ambiente

#### Com objetivo de:

- Reduzir o tempo entre desenvolvimento e entrega
- Aumentar a frequência de deploys
- Minimizar erros manuais
- Tornar o deploy seguro e reversível (rollback)

#### Etapas comuns:

- **Checkout do código**
- **Build da aplicação**
- **Testes (unitários, integração, e2e)**
- **Análise de código (lint, segurança)**
- **Geração de artefatos (docker, pacotes, etc.)**
- **Deploy em staging**
- **Deploy em produção (manual ou automático)**