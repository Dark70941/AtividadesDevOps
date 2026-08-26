# Resumo - Aula 04: Análise Comparativa de Ferramentas CI/CD (Azure DevOps vs. GitHub)

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** FATEC Sorocaba (Faculdade de Tecnologia)  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`) 
**Data Limite de Entrega:** 5 de setembro de 2026 às 23:59
**Base de Estudo:** MANOLOV, Vladislav; GOTSEVA, Daniela; HINOV, Nikolay. *Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub*. Future Internet, v. 17, n. 4, 2025, p. 153. (DOI: 10.3390/fi17040153)

---

## 1. Contextualização da Aula e Objetivos
A Aula 04 aborda o ecossistema de ferramentas de Integração Contínua (CI) e Entrega/Implantação Contínua (CD), focando na automação de processos de desenvolvimento de software de acordo com os princípios DevOps. A atividade principal consiste em analisar e comparar empiricamente as plataformas **Azure DevOps** e **GitHub** com base no estudo recente de Manolov, Gotseva e Hinov (2025).

---

## 2. Visão Geral do Ciclo DevOps e o Papel do CI/CD
O ciclo de vida DevOps é representado por um fluxo contínuo dividido em etapas interligadas:
- **PLAN:** Planejamento ágil, backlog e gestão de tarefas.
- **CODE:** Desenvolvimento colaborativo, versionamento e revisão de código.
- **BUILD:** Compilação automatizada, análise estática e empacotamento.
- **TEST:** Testes automatizados (unitários, integração, regressão, segurança).
- **RELEASE:** Versionamento semântico, governança e Quality Gates.
- **DEPLOY:** Implantação automatizada em ambientes (Staging, Production).
- **OPERATE:** Gestão de infraestrutura como código (IaC) e orquestração.
- **MONITOR:** Observabilidade, logs, métricas e rastreabilidade (telemetria).

As pipelines de CI/CD automatizam a transição entre essas fases, reduzindo falhas humanas, encurtando o tempo de ciclo (*lead time*) e aumentando a previsibilidade do software.

---

## 3. Ferramentas Identificadas no Artigo e no Ecossistema
No artigo de Manolov et al. (2025) e nos materiais complementares da disciplina, foram mapeadas e categorizadas as seguintes ferramentas do ciclo CI/CD:

### A. Plataformas Principais de CI/CD e ALM
- **Azure DevOps (Azure Pipelines):** Plataforma corporativa *end-to-end* da Microsoft para gestão do ciclo de vida do software (ALM).
- **GitHub (GitHub Actions):** Plataforma nativa orientada a desenvolvedores para automação de workflows baseados em eventos no Git.
- **GitLab CI/CD:** Solução integrada para DevSecOps com forte foco em pipelines declarativas e *single pane of glass*.
- **Bitbucket Pipelines:** Ferramenta de CI/CD integrada ao ecossistema Atlassian (Jira/Bitbucket).
- **Jenkins:** Servidor de automação *open-source* altamente extensível via plugins.
- **Outras plataformas citadas:** CircleCI, Travis CI, TeamCity, Bamboo, Buddy, Concourse, Axify.

### B. Gestão, Colaboração e Planejamento (PLAN / CODE)
- **Azure Boards & Azure Repos:** Módulos do Azure DevOps para gestão de projetos ágeis (Scrum/Kanban) e controle de versão Git.
- **GitHub Projects & GitHub Repositories:** Gerenciamento visual de tarefas e hospedagem de código-fonte.
- **Jira & Trello:** Ferramentas da Atlassian amplamente utilizadas no mercado para acompanhamento de sprints e tarefas.

### C. Segurança, Qualidade e Gestão de Artefatos (BUILD / TEST)
- **SonarQube:** Análise estática de código (SAST), identificando *code smells*, vulnerabilidades e dívida técnica.
- **GitHub Advanced Security:** Ferramentas nativas do GitHub incluindo **CodeQL** (análise estática), **Dependabot** (gestão de dependências e vulnerabilidades) e **Secret Scanning**.
- **Azure Artifacts & GitHub Packages:** Gerenciamento centralizado de pacotes e dependências (NuGet, npm, Maven, Docker).
- **Azure Test Plans:** Suporte e gestão integrada de testes manuais e de regressão no Azure DevOps.

### D. Implantação, Orquestração e Infraestrutura (DEPLOY / OPERATE / MONITOR)
- **Docker & Kubernetes:** Conteinerização de aplicações e orquestração de contêineres em ambientes distribuídos.
- **Helm:** Gerenciador de pacotes para Kubernetes.
- **Argo CD & Spinnaker:** Ferramentas especializadas em automação de entrega contínua baseadas em GitOps e estratégias avançadas de deploy.
- **Ansible & Chef:** Automação de infraestrutura como código (IaC) e gestão de configuração.
- **Grafana & Graylog:** Ferramentas para monitoramento visual, telemetria, logs centralizados e observabilidade.

---

## 4. Análise Comparativa: Azure DevOps vs. GitHub (Manolov et al., 2025)

Baseado nos testes empíricos e análises qualitativas descritas no artigo científico, a tabela abaixo sintetiza os principais critérios de comparação entre as duas plataformas centrais:

| Critério de Comparação | Azure DevOps (Azure Pipelines) | GitHub (GitHub Actions) |
| :--- | :--- | :--- |
| **Arquitetura & Abordagem** | Suíte corporativa completa (ALM). Separação formal de *Build* (CI) e *Release* (CD). | Plataforma focada no desenvolvedor. Unificação de CI/CD via workflows baseados em eventos. |
| **Configuração de Pipelines** | Editor Visual (Classic UI) ou arquivos YAML com múltiplos estágios (*stages*), empregos (*jobs*) e tarefas (*tasks*). | Arquivos YAML declarativos localizados na pasta `.github/workflows`, acionados por eventos Git (*push*, *PR*, *release*). |
| **Reutilização & Modularidade** | Templates YAML reutilizáveis centralizados e bibliotecas de variáveis (Variable Groups). | *Reusable Workflows* e *Composite Actions* publicadas no GitHub Marketplace. |
| **Governança & Controle** | Rigoroso controle de acesso baseado em funções (RBAC), *Quality Gates*, *Environment Approvals* e auditoria enterprise. | Regras de proteção de *branch*, aprovação em ambientes (*Environment Protection Rules*) e segredos por escopo. |
| **Segurança NFM (DevSecOps)** | Integração com Azure Key Vault, conexões de serviço seguras (*Service Connections*) e SonarQube. | Suporte nativo ao ecossistema DevSecOps (CodeQL, Dependabot, Secret Scanning integrado ao fluxo). |
| **Gestão de Testes** | Excelente suporte e integração profunda com *Azure Test Plans* e relatórios detalhados de execução. | Execução de testes via matrizes (*job matrix*) e relatórios integrados via Actions de terceiros. |
| **Experiência do Desenvolvedor (DX)** | Curva de aprendizado inicial mais íngremes devido ao volume de configurações e módulos do ecossistema. | Altíssima adoção e facilidade de uso (*Developer-friendly*), com integração direta com a interface de código-fonte. |
| **Modelo de Custos (TCO)** | Cobrança por usuários (licenciamento corporativo), minutos de execução de pipeline e agentes paralelos. | Cobrança baseada em consumo de minutos de *runners* e armazenamento de artefatos (gratuito para código aberto). |

---

## 5. Vantagens, Limitações e Adequação por Cenário

### Azure DevOps (Azure Pipelines)
- **Vantagens:**
  - Governança corporativa robusta e rastreabilidade completa desde o requisito (Azure Boards) até o deploy em produção.
  - Suporte superior para ambientes híbridos, estruturas legadas e aprovações complexas de segurança de múltiplos estágios.
  - Interface madura para gestão visual de testes e monitoramento de execução de releases.
- **Limitações:**
  - Configuração inicial e interface mais complexas e fragmentadas.
  - Menor dinamismo da comunidade em comparação com plataformas puramente abertas.
- **Situações de Maior Adequação:** Grandes corporações, empresas com forte presença no ecossistema Microsoft Enterprise, projetos que exigem governança rigorosa, auditoria severa e integração com ALM.

### GitHub (GitHub Actions)
- **Vantagens:**
  - Experiência de desenvolvimento integrada (o código, os Pull Requests e os pipelines vivem no mesmo lugar).
  - Vasto ecossistema de automação através do GitHub Marketplace (milhares de Actions comunitárias e oficiais).
  - Segurança integrada por padrão (DevSecOps) com varredura automática de código e dependências.
- **Limitações:**
  - Gerenciamento de múltiplos pipelines interdependentes em larga escala pode requerer estruturas complexas de automação.
  - Menos recursos nativos para gestão formal corporativa de testes manuais e rastreabilidade avançada de ALM sem plugins externos.
- **Situações de Maior Adequação:** Startups, projetos Open Source, equipes modernas focadas em agilidade e *Developer Experience*, arquiteturas nativas em nuvem (*Cloud Native*) e fluxos de trabalho *Git-centric*.

---

## 6. Critérios de Avaliação da Disciplina
Fórmula da média final: **(P1 × 0,25) + (P2 × 0,25) + ((PJ + AT) × 0,25)**
- **P1:** Prova 1
- **P2:** Prova 2
- **PJ:** Projeto Prático
- **AT:** Atividades de Sala/Semanais

---

## 7. Atividade Proposta (Tarefa 04)
1. **Prazo de entrega:** 5 de setembro de 2026, até as 23:59.
2. **Formato:** Submissão em grupo (3 a 5 integrantes).
3. **Escopo:**
   - Ler o artigo *Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub* (MANOLOV, GOTSEVA e HINOV, 2025).
   - Identificar todas as ferramentas citadas pelos autores no artigo.
   - Escrever um documento Markdown (`.md`) com a análise comparativa detalhada cobrindo características, vantagens, limitações e cenários de utilização.
   - Publicar o arquivo `.md` no repositório GitHub do grupo no repositório da disciplina.

---

## 8. Bibliografia Indicada
- ARUNDEL, J.; DOMINGUS, J. *DevOps nativo de nuvem com Kubernetes*. São Paulo: Novatec, 2019.
- HUMBLE, J.; PRIKLANDNICKI, R. *Entrega Contínua: Como Entregar Software de Forma Rápida e Confiável*. São Paulo: Bookman, 2013.
- KIM, G.; HUMBLE, J.; DEBOIS, P.; WILLIS, J. *Manual de DEVOPS: Como obter agilidade, confiabilidade e segurança em organizações tecnológicas*. São Paulo: Starlin Alta Editora, 2018.
- MANOLOV, V.; GOTSEVA, D.; HINOV, N. *Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub*. Future Internet, v. 17, n. 4, 2025, p. 153. DOI: 10.3390/fi17040153.
- MORAES, G. *Caixa de Ferramentas DevOps: Um guia para construção, administração e arquitetura de sistemas modernos*. São Paulo: Casa do Código, 2015.
- MUNIZ, A. et al. *Jornada DevOps: Unindo Cultura Ágil, Lean e Tecnologia Para Entrega De Software Com Qualidade*. São Paulo: Brasport, 2019.
- PIRES, A.; MILITÃO, J. *Integração Contínua com Jenkins*. São Paulo: Casa do Código, 2019.
- SATO, D. *DevOps na prática: entrega de software confiável e automatizada*. São Paulo: Casa do Código, 2014.
- SILVA, R. *Entrega contínua em Android: Como automatizar a distribuição de apps*. São Paulo: Casa do Código, 2016.
- SILVERMAN, R. E. *Git: guia prático*. São Paulo: Novatec, 2019.
- VITALINO, J. F. N.; CASTRO, M. A. N. *Descomplicando o Docker*. 2 ed. São Paulo: Brasport, 2018.
