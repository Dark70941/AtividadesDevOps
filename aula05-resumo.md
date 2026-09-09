# Resumo - Aula 05: Pipeline de Integração Contínua

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** FATEC Sorocaba (Faculdade de Tecnologia)  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Base de Estudo:** Slides da Aula 05 - Pipeline de Integração Contínua (Takatu, D. S.)

---

## 1. Contextualização da Aula e Objetivos
A Aula 05 aborda os conceitos fundamentais sobre **Pipelines de Integração Contínua (CI/CD)** no ecossistema DevOps. O foco principal foi compreender a estrutura automatizada de validações que conduz o software desde a alteração no código até o deploy de forma confiável e ágil. Durante a aula, exploramos as etapas que compõem uma pipeline e realizamos uma prática utilizando o **GitHub Actions**.

---

## 2. Visão Geral do Ciclo DevOps e o Papel das Pipelines
As pipelines de CI/CD promovem a qualidade contínua e a estabilidade na entrega do software. Elas integram as etapas de desenvolvimento, testes e operações por meio de regras e automações cruciais:
- **Build uma única vez:** O artefato gerado na compilação é o mesmo promovido entre todos os ambientes (Desenvolvimento → Homologação → Produção).
- **Mesmo deploy:** Padronização nos processos de implantação em todos os níveis.
- **Regra de interrupção ("Falhou? Para tudo"):** Nenhuma etapa avança se houver qualquer erro na validação anterior.

---

## 3. Estágios e Estrutura de uma Pipeline
A estrutura de uma pipeline é composta por estágios sequenciais automatizados:

### A. Pipeline de Build
- Responsável por compilar o projeto e realizar verificações iniciais da integridade do código.
- Gera os artefatos de software executáveis ou de distribuição (arquivos `.jar`, `.war`, `.apk`, containers Docker, etc.).

### B. Pipeline de Testes
- Executa validações automáticas após o build para garantir que novas alterações não quebrem funcionalidades existentes.

### C. Pipeline de Qualidade e Segurança
- **Qualidade:** Realiza análises automatizadas para avaliar se o código atende aos padrões e padrões definidos antes de prosseguir.
- **Segurança:** Identifica vulnerabilidades no código, checa dependências utilizadas, detecta configurações inseguras e evita a exposição de informações sensíveis.

### D. Pipeline de Artefatos e Deploy
- **Artefatos (Package):** Empacota, versiona e armazena os arquivos de distribuição gerados no build em repositórios apropriados.
- **Deploy:** Publica automaticamente o artefato no ambiente de destino configurado (ex: Homologação ou Produção).

### E. Pipeline de Release e Monitoramento
- Cria e identifica versões específicas do software, controlando releases e realizando o monitoramento contínuo da aplicação em produção.

---

## 4. Automação e Execução com GitHub Actions

O **GitHub Actions** foi apresentado como a ferramenta nativa de automação integrada ao GitHub:
- **Workflows e Gatilhos:** Fluxos automatizados iniciados por eventos do repositório, tais como `push`, `pull_request`, criação de tags ou publicação de releases.
- **GitHub Marketplace:** Catálogo com ferramentas e extensões desenvolvidas pelo GitHub, parceiros ou pela comunidade para reutilização em etapas de build, testes, qualidade, segurança e deploy.

---

## 5. Atividade Proposta (Atividade Prática)
1. **Escopo:** Escolher 3 *Actions* no GitHub Marketplace e desenvolver um projeto prático.
2. **Implementação:** Configurar o workflow no GitHub Actions aplicando cada *Action* em uma etapa adequada da pipeline automatizada (ex: build, testes, qualidade, deploy).
3. **Validação e Documentação:** Executar o fluxo, verificar o correto funcionamento e documentar no projeto as *Actions* utilizadas, suas funções e como contribuíram para a automação do processo.

---

## 6. Bibliografia Indicada
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
