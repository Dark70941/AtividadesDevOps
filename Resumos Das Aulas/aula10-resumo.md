# Resumo - Aula 10: Arquitetura e Requisitos de um Projeto DevOps

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** FATEC Sorocaba (Faculdade de Tecnologia)  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Base de Estudo:** Slides da Aula 10 - Projeto DevOps (Takatu, D. S.)

---

## 1. Resumo Teórico da Aula 10

A Aula 10 consolida todos os conceitos, ferramentas e práticas estudados ao longo da disciplina em uma **arquitetura de aplicação web completa de ponta a ponta**. O objetivo central é integrar desenvolvimento colaborativo, testes automatizados, padronização de ambientes, pipelines de CI/CD, segurança e observabilidade em um fluxo contínuo e reproduzível.

### Pilares Arquiteturais de uma Aplicação Web Moderna
Uma aplicação web estruturada sob práticas DevOps divide-se em camadas desacopladas e integradas:
- **Front-end:** Camada de interface responsável pela experiência e interação com o usuário.
- **Back-end:** Camada responsável pelas regras de negócio, processamento e exposição de *endpoints* (APIs).
- **Banco de Dados:** Camada dedicada à persistência estruturada ou não estruturada das informações.
- **Middleware:** Camadas intermediárias responsáveis por integração, autenticação, autorização, validação de requisições e *logs*.

---

### Fluxo de Versionamento e Colaboração (Git e GitHub)
O controle de versão atua como a espinha dorsal da colaboração e da rastreabilidade de mudanças:
- **Repositório Estruturado:** Centralização do código-fonte, arquivos de configuração, pipelines e documentação (`README.md`).
- **Estratégia de Branches:** Criação de *branches* dedicadas para novas funcionalidades (*features*) e correções (*fixes*), preservando a estabilidade da branch principal (`main`).
- **Commits Semânticos e Organizados:** Histórico claro, atômico e descritivo de cada alteração realizada.
- **Pull Requests (PRs) e Code Review:** Integração controlada de alterações mediante revisão de código por pares e vinculação direta entre tarefas e mudanças.

---

### Estratégia Completa de Testes Automatizados
Para garantir confiabilidade antes de qualquer entrega, a arquitetura prevê quatro níveis complementares de validação:
1. **Testes Unitários:** Validam funções, componentes e regras de negócio de forma isolada.
2. **Testes de Integração:** Verificam a comunicação e o contrato entre módulos, serviços e banco de dados.
3. **Testes Ponta a Ponta (*E2E*):** Simulam e validam os fluxos críticos reais do usuário na aplicação.
4. **Testes de Performance:** Avaliam tempo de resposta (latência), comportamento sob volume de requisições e taxa de erros.

---

## 2. Esteira CI/CD, Conteinerização, Segurança e Observabilidade

A automação operacional garante que o software seja construído, validado, empacotado e monitorado de maneira padronizada entre todos os ambientes.

### Integração Contínua (CI) e Entrega Contínua (CD)
- **Integração Contínua (CI - ex: GitHub Actions):**
  * Instalação automatizada de dependências.
  * Validação de estrutura e análise estática de qualidade de código.
  * Execução automatizada da suíte de testes.
  * Compilação/*build* dos artefatos da aplicação.
- **Entrega Contínua e Deploy (CD):**
  * Construção automatizada de imagens Docker versionadas.
  * Implantação automatizada em ambiente de destino com identificação clara da versão publicada.
  * Verificações pós-deploy (*smoke tests* / *health checks*) e documentação do processo de implantação.

### Padronização de Ambiente com Docker
- Criação de `Dockerfile` dedicado para o **back-end** e para o **front-end** (quando aplicável).
- Definição explícita de portas de rede, variáveis de ambiente e dependências de sistema.
- Orquestração dos serviços (ex: aplicação + banco de dados) garantindo paridade entre desenvolvimento e produção.

### Configuração e Segurança (*DevSecOps*)
- **Separação entre Código e Configuração:** Nenhuma configuração sensível deve ser fixada (*hardcoded*) no código-fonte.
- **Variáveis de Ambiente e `.env.example`:** Uso de variáveis de ambiente em tempo de execução, mantendo no repositório apenas um arquivo `.env.example` com chaves fictícias.
- **Gestão de Segredos e Permissões:** Proteção rigorosa de senhas, *tokens* e chaves privadas (via *GitHub Secrets*), aplicando o princípio do menor privilégio nas permissões das pipelines e realizando análise de vulnerabilidades quando viável.

### Logs, Monitoramento e Observabilidade
- **Registro de Eventos e Erros:** Geração estruturada de *logs* de operações críticas e exceções relevantes.
- **Disponibilidade e Métricas:** Monitoramento contínuo da saúde do serviço (*uptime*), consumo de recursos e métricas operacionais no ambiente implantado.

---

## 3. Matriz de Requisitos Técnicos da Arquitetura DevOps

| Camada / Pilar | Ferramentas e Artefatos | Objetivo Técnico Principal |
| :--- | :--- | :--- |
| **Aplicação Web** | Front-end, Back-end, Banco de Dados, Middleware | Separar responsabilidades e garantir escalabilidade e manutenção |
| **Controle de Versão** | Git, GitHub, Branches, Pull Requests, Code Review | Rastrear alterações e validar código antes da integração na `main` |
| **Qualidade e Testes** | Testes Unitários, Integração, E2E e Performance | Detectar regressões e gargalos automaticamente antes do deploy |
| **Padronização** | Docker, `Dockerfile`, Orquestração de Serviços | Eliminar divergências de ambiente e empacotar dependências |
| **Automação CI/CD** | GitHub Actions (`.yml`), Build e Deploy Automatizado | Acelerar entregas com validação contínua e versionamento |
| **Segurança** | Variáveis de Ambiente, `.env.example`, Secrets | Proteger credenciais sensíveis e controlar permissões de pipeline |
| **Observabilidade** | Logs estruturados, Métricas, Health Checks | Garantir visibilidade operacional e diagnóstico rápido de falhas |

---

## 4. Conclusão

A Aula 10 sintetiza a jornada da disciplina ao demonstrar como cada prática DevOps se conecta em uma arquitetura real: o versionamento colaborativo alimenta a pipeline de Integração Contínua (CI), que executa testes automatizados e constrói imagens Docker padronizadas; na sequência, a Entrega Contínua (CD) implanta a versão validada de forma segura — protegida por variáveis de ambiente e segredos — enquanto logs e métricas garantem a observabilidade contínua da aplicação em produção.
