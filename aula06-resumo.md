# Resumo e Análise Prática - Aula 06: Revisão de Ferramentas e Pipelines

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** FATEC Sorocaba (Faculdade de Tecnologia)  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Base de Estudo:** Slides da Aula 06 - Revisão Ferramentas e Pipelines (Takatu, D. S.)

---

## 1. Resumo Teórico da Aula 06

A Aula 06 revisou a cultura DevOps como um **ciclo infinito** que integra as equipes de Desenvolvimento (DEV) e Operações (OPS), eliminando silos organizacionais para acelerar a entrega de software com alta qualidade e confiabilidade.

### O Ciclo Infinito DevOps (8 Fases)
1. **PLAN:** Planejamento e gestão ágil utilizando ferramentas como Jira, Trello e Azure Boards.
2. **CODE:** Escrever, revisar e versionar código com boas práticas e IDEs integradas (ex: Git, GitHub, GitLab).
3. **BUILD:** Compilação automatizada do código em artefatos executáveis (JAR, WAR, pacotes NPM, imagens Docker) utilizando ferramentas como Gradle e Maven.
4. **TEST:** Execução automatizada contínua de testes para rápida detecção de falhas e garantia de regressão zero.
5. **RELEASE:** Liberação, versionamento semântico (`Major.Minor.Patch`) e aplicação de *Quality Gates* antes do ambiente final.
6. **DEPLOY:** Implantação automatizada em ambientes de produção/homologação sem downtime (ex: Kubernetes no AWS EKS, rolling updates).
7. **OPERATE:** Gestão de infraestrutura automatizada e Infraestrutura como Código (IaC) utilizando Kubernetes e Ansible.
8. **MONITOR:** Observabilidade contínua alimentando o próximo ciclo através de **Métricas** (CPU, latência, erros), **Logs** (registros de eventos) e **Traces** (rastreamento de requisições) com Grafana e Graylog.

---

### Regras Fundamentais e Estrutura de Pipelines
* **Build uma única vez:** O mesmo artefato gerado na compilação é promovido entre todos os ambientes (Desenvolvimento → Homologação → Produção).
* **Mesmo deploy:** Padronização dos processos de implantação em todos os níveis.
* **Regra de Interrupção ("Falhou? Para tudo"):** Se qualquer etapa apresentar erro, a pipeline é interrompida imediatamente para evitar a propagação de falhas.

#### Estágios da Pipeline:
* **Build:** Compilação, resolução de dependências e verificação de integridade.
* **Testes:** Validações automáticas e contínuas do sistema.
* **Qualidade:** Verificação de padrões e padronização do código.
* **Segurança:** Análise estática de vulnerabilidades e verificação de dependências inseguras.
* **Artefatos (Package):** Empacotamento, versionamento e armazenamento seguro em repositórios (ex: Nexus).
* **Deploy:** Publicação automatizada no ambiente de execução de destino.
* **Release e Monitoramento:** Controle de versões disponibilizadas e acompanhamento em tempo real.

---

## 2. Atividade Prática: Análise de Pipelines em Repositórios GitHub

Atendendo à proposta da atividade da Aula 06, foram analisados três projetos *open-source* reais no GitHub que integram pipelines automatizadas utilizando **GitHub Actions**, configuradas para execução no branch principal (`main`/`master`).

### Projeto 1: Vue.js Core (`vuejs/core`)
* **Ecossistema:** TypeScript / JavaScript
* **Características:** Framework JavaScript progressivo focado na construção de interfaces de usuário.
* **Funcionalidades da Pipeline:**
  * Checagem de tipagem estática via TypeScript.
  * Testes unitários e de componentes executados via Vitest.
  * Validação de qualidade de código e padronização com ESLint.
  * Verificação automatizada do tamanho final dos pacotes gerados (*bundle size check*).
* **Gatilhos (Triggers):**
  * Disparo automatizado em eventos de `push` na branch `main`.
  * Validação de `pull_request` direcionados à branch `main`.
  * Execução agendada via `schedule` (cron).
* **Histórico:** Pipeline madura e extremamente ativa, garantindo alta estabilidade a cada nova versão lançada no ecossistema Vue.

---

### Projeto 2: Spring Boot (`spring-projects/spring-boot`)
* **Ecossistema:** Java / Gradle
* **Características:** Framework Java amplamente utilizado para a criação de microsserviços e aplicações corporativas.
* **Funcionalidades da Pipeline:**
  * Compilação do projeto e gerenciamento de dependências via Gradle/Maven.
  * Execução de matrizes de testes de integração em múltiplas versões do Java (JDK 17 e JDK 21).
  * Análise estática de estilo de código com Checkstyle.
  * Publicação automática de artefatos de desenvolvimento (`SNAPSHOT`) no repositório Nexus.
* **Gatilhos (Triggers):**
  * Execução automatizada em eventos de `push` na branch `main` e branches de suporte (ex: `3.2.x`).
  * Validação de `pull_request`.
  * Disparo manual via `workflow_dispatch`.
* **Histórico:** Histórico consistente de automação corporativa, aplicando rigorosamente bloqueios no fluxo em caso de quebra de testes ou inconformidade de código.

---

### Projeto 3: NestJS (`nestjs/nest`)
* **Ecossistema:** Node.js / TypeScript
* **Características:** Framework Node.js progressivo para a construção de aplicações *server-side* escaláveis.
* **Funcionalidades da Pipeline:**
  * Compilação e empacotamento em arquitetura de monorepo.
  * Execução de testes unitários e testes de integração de ponta a ponta (*E2E*) utilizando Jest.
  * Verificação e aplicação de formatação de código via Prettier.
  * Envio de métricas de cobertura de código para integração com Codecov.
* **Gatilhos (Triggers):**
  * Disparo automatizado a cada `push` na branch `master`.
  * Execução automatizada em todos os `pull_request`.
* **Histórico:** Pipeline enxuta e ágil, projetada para fornecer *feedback* rápido de integridade aos desenvolvedores e contribuidores da comunidade.

---

## 3. Tabela Comparativa dos Projetos Analisados

| Projeto / Repositório | Ecossistema | Principais Etapas da Pipeline | Gatilhos Principais |
| :--- | :--- | :--- | :--- |
| **Vue.js Core**<br>`vuejs/core` | TypeScript / JS | TypeScript Check, Vitest, ESLint, Bundle Size Check | `push` (main), `pull_request`, `schedule` |
| **Spring Boot**<br>`spring-projects/spring-boot` | Java / Gradle | Gradle Build, Matriz JDK (17/21), Checkstyle, Nexus Publish | `push` (main/branches), `pull_request`, `workflow_dispatch` |
| **NestJS**<br>`nestjs/nest` | Node.js / TS | Monorepo Build, Jest (Unit & E2E), Prettier, Codecov | `push` (master), `pull_request` |

---

## 4. Conclusão

A revisão da Aula 06 reforça que a eficiência do modelo DevOps se apoia na automação contínua de ponta a ponta. A análise dos repositórios **Vue.js**, **Spring Boot** e **NestJS** demonstra a aplicação direta dos conceitos apresentados: pipelines disparadas automaticamente por eventos de `push` no branch principal, execução encadeada de testes e qualidade, e o cancelamento imediato da entrega caso ocorra qualquer falha durante o processo.
