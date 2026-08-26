# Resumo - Aula 02: Conceitos de Integração e Entrega Contínua de Software, Versionamento, Git/GitHub e Deploy

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** FATEC Sorocaba (Faculdade de Tecnologia)  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Data Limite de Entrega:** 22 de Agosto de 2026 às 23:59  

---

## 1. O Problema da Entrega de Software (Antes vs. Depois do DevOps)

### Cenário Tradicional (Antes)
- **Desenvolvimento e Infraestrutura isolados:** Trabalhando em silos organizacionais.
- **Processos Manuais:** Testes e deploys manuais, lentos, repetitivos e altamente sujeitos a falhas humanas.
- **Conflito de Ambientes:** O clássico "funciona na minha máquina, mas dá erro no servidor".
- **Impacto:** Entregas demoradas, falhas em produção, indisponibilidade, retrabalho e medo/instabilidade a cada atualização.

### Cenário DevOps (Depois)
- **Integração DEV + OPS:** Cultura e práticas que unem desenvolvimento e operações.
- **Automação:** Testes automáticos rápidos e consistentes; pipeline de CI/CD para integração e entrega contínuas.
- **Deploy Confiável:** Entregas previsíveis, seguras, ágeis e sem interrupção de serviço.

---

## 2. DevOps: O Ciclo Infinito do Desenvolvimento Moderno
O ciclo de vida DevOps é representado por um loop contínuo dividido nas seguintes etapas:

1. **PLAN (Planejamento):** Definição de prioridades e gestão de tarefas com metodologias ágeis (ex: *Jira, Trello, Azure Boards*).
2. **CODE (Codificação):** Escrita de código limpo, legível, revisado e versionado colaborativamente.
3. **BUILD (Compilação e Build Automatizado):** Transformação do código-fonte em artefatos executáveis (JAR, imagens Docker, pacotes NPM) com verificação de qualidade via análise estática (ex: *SonarQube, Gradle, Nexus*).
4. **TEST (Testes Automatizados):** Guardiões da qualidade no pipeline de CI/CD para detecção rápida de falhas (unitários, integração, e2e).
5. **RELEASE (Liberação e Governança):** Validação dos Quality Gates e atribuição de versionamento semântico (ex: `v2.4.1`).
6. **DEPLOY (Implantação Automatizada):** Publicação rápida e segura nos ambientes de produção (ex: *Docker, AWS, Kubernetes, Azure*).
7. **OPERATE (Operação e Gestão de Infraestrutura):** Garantia de estabilidade, alta disponibilidade e escalabilidade via Infraestrutura como Código (ex: *Ansible, Chef, OpenStack*).
8. **MONITOR (Observabilidade Contínua):** Coleta contínua de métricas, logs e traces (ex: *Grafana, Graylog*) para alimentar o próximo ciclo de planejamento.

---

## 3. Conceitos Fundamentais: CI, CD e Deploy Contínuo

- **Integração Contínua (CI - Continuous Integration):** Prática de integrar alterações de código frequentemente no repositório compartilhado. A cada commit, dispara automaticamente build, testes e verificações de falhas para detectar problemas precocemente.
- **Entrega Contínua (Continuous Delivery):** Automação do preparo e disponibilização do software. O código aprovado é compilado, testado e empacotado, ficando sempre pronto para deploy manual em produção a qualquer momento.
- **Deploy Contínuo (Continuous Deployment):** Extensão da entrega contínua onde a publicação em produção ocorre de forma **100% automática** logo após a aprovação nos testes e validações do pipeline.

---

## 4. Versionamento e Versionamento Semântico (SemVer)

### Introdução ao Versionamento
- Atribuição de identificadores únicos a versões de software/documentos.
- Registra quem alterou, o que alterou e quando.
- Garante rastreabilidade, controle de mudanças, histórico, auditabilidade e facilidade de recuperação (rollback).

### Versionamento Semântico (SemVer)
Segue o padrão **MAJOR.MINOR.PATCH** (ex: `2.1.3`):
- **MAJOR (Ápice):** Mudanças incompatíveis com versões anteriores (ex: `1.0.0` -> `2.0.0`).
- **MINOR (Incremento):** Novas funcionalidades mantendo compatibilidade com versões anteriores (ex: `1.0.0` -> `1.1.0`).
- **PATCH (Correção):** Correção de bugs (*bug fixes*) sem alterar a API/funcionalidades existentes (ex: `1.1.0` -> `1.1.1`).

### Tipos Comuns de Alterações no Código
- **Bug Fix:** Correção de erros.
- **New Feature:** Adição de nova funcionalidade.
- **Feature Enhancement:** Melhoria em funcionalidade existente.
- **Refactoring:** Reorganização do código para maior clareza e eficiência sem alterar comportamento externo.
- **Performance:** Otimização de velocidade e recursos.
- **Security Patch:** Correção de vulnerabilidades.
- **Dependency Update:** Atualização de bibliotecas/frameworks.
- **Adding Tests:** Inclusão de testes automatizados.

---

## 5. Git, Tags e Deploy

### O que é o Git?
- Sistema distribuído de controle de versão de arquivos criado por Linus Torvalds.
- Instalado localmente e manipulado via terminal/IDE (VS Code).
- Permite criar histórico de commits, trabalhar em branches e sincronizar com plataformas remotas (GitHub, GitLab, Bitbucket).

### Tags no Git
- Marcadores que identificam pontos específicos e relevantes no histórico de commits (ex: releases de versões `v1.0.0`).
- **Tipos:**
  - *Leve (lightweight):* Um simples ponteiro/nome para um commit específico.
  - *Anotada (annotated):* Armazena dados do autor, data, e-mail e mensagem explicativa.

### O que é Deploy e Plataformas (Vercel)
- **Deploy:** Processo de colocar uma aplicação pronta em ambiente de produção para acesso dos usuários finais.
- **Vercel:** Plataforma moderna focada no deploy simplificado de sites estáticos e aplicações front-end (React, Next.js, HTML/CSS/JS), integrada nativamente ao GitHub para deploys automáticos a cada push.

---

## 6. Atividade Prática (Tarefa 02)

### Descrição da Tarefa
1. Instalar e configurar o **Visual Studio Code (VS Code)** e o **Git**.
2. Criar a estrutura básica do projeto com os arquivos `index.html`, `style.css` e `script.js` na mesma pasta.
3. Configurar a identidade no Git (`user.name` e `user.email`) e inicializar o repositório local.
4. Conectar e publicar o repositório no **GitHub**.
5. Realizar alterações no projeto, registrar as modificações via novos **commits** e criar **tags** de versão (ex: `v1.0.0`, `v1.1.0`).
6. Documentar o processo e enviar o repositório no Microsoft Teams.

---

## 7. Entregáveis e Links da Atividade

- **Link do Repositório no GitHub:** `[COLE_AQUI_O_LINK_DO_SEU_REPOSITORIO_GITHUB]`
- **PDF da Documentação:** `[COLE_AQUI_O_LINK_OU_NOME_DO_ARQUIVO_PDF_ANEXADO]`

---

## 8. Integrantes do Grupo
- Nome Completo 1 - RA/E-mail
- Nome Completo 2 - RA/E-mail
- Nome Completo 3 - RA/E-mail
- Nome Completo 4 - RA/E-mail

---

## 9. Referências Bibliográficas
- ARUNDEL, J.; DOMINGUS, J. *DevOps nativo de nuvem com Kubernetes*. São Paulo: Novatec, 2019.
- HUMBLE, J.; PRIKLANDNICKI, R. *Entrega Contínua: Como Entregar Software de Forma Rápida e Confiável*. São Paulo: Bookman, 2013.
- KIM, G.; HUMBLE, J.; DEBOIS, P.; WILLIS, J. *Manual de DEVOPS: Como obter agilidade, confiabilidade e segurança em organizações tecnológicas*. São Paulo: Starlin Alta Editora, 2018.
- MORAES, G. *Caixa de Ferramentas DevOps: Um guia para construção, administração e arquitetura de sistemas modernos*. São Paulo: Casa do Código, 2015.
- MUNIZ, A. et al. *Jornada DevOps: Unindo Cultura Ágil, Lean e Tecnologia Para Entrega De Software Com Qualidade*. São Paulo: Brasport, 2019.
- PIRES, A.; MILITÃO, J. *Integração Contínua com Jenkins*. São Paulo: Casa do Código, 2019.
- SATO, D. *DevOps na prática: entrega de software confiável e automatizada*. São Paulo: Casa do Código, 2014.
- SILVA, R. *Entrega contínua em Android: Como automatizar a distribuição de apps*. São Paulo: Casa do Código, 2016.
- SILVERMAN, R. E. *Git: guia prático*. São Paulo: Novatec, 2019.
- VITALINO, J. F. N.; CASTRO, M. A. N. *Descomplicando o Docker*. 2 ed. São Paulo: Brasport, 2018.
