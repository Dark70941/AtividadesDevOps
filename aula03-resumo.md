# FACULDADE DE TECNOLOGIA DE SOROCABA - FATEC
## Curso Superior de Tecnologia em Análise e Desenvolvimento de Sistemas

---

### RELATÓRIO DE GERÊNCIA DE CONFIGURAÇÃO - TAREFA 03

- **Disciplina:** Gerência de Configuração
- **Docente:** Prof. Me. Deivison S. Takatu
- **Data de Entrega:** 29 de agosto de 2026

| INTEGRANTES DO GRUPO |
| :--- |
| Karina de Moraes Garcia |
| Mike Willy Franguelli |
| Nicolly Lemos da Silva |
| Pedro Henrique Cardozo Dias |
| Rafaela Mansano Fernandes |

---

## 1. Visão Geral do Item de Configuração

Este documento apresenta o relatório prático desenvolvido para a **Tarefa 03** da disciplina de Gerência de Configuração. O objetivo consistiu na parametrização, versionamento e implantação contínua (CI/CD) de um projeto de software baseado em um template open-source.

O software utilizado foi o template *Landy*, uma aplicação web responsiva construída com **React.js**, **TypeScript** e **Node.js**. O repositório base foi clonado, estruturado localmente e vinculado ao **GitHub**, com pipeline de publicação automática integrado à plataforma de hospedagem **Vercel**.

> **📌 Registros de Repositório e Produção:**
> - **Repositório do Grupo (GitHub):** [https://github.com/nicollylemos/ProjetoGitTemplate](https://github.com/nicollylemos/ProjetoGitTemplate)
> - **Ambiente de Produção (Vercel):** [https://projeto-git-template-7s74jspc2-fatec1.vercel.app](https://projeto-git-template-7s74jspc2-fatec1.vercel.app)
> - **Repositório de Origem (Template Base):** [https://github.com/Adrinlol/landy-react-template](https://github.com/Adrinlol/landy-react-template)

### Especificações Técnicas:
- **Ambiente de Execução:** Node.js (v22 LTS) e NPM (Node Package Manager).
- **Framework Frontend:** React.js com suporte a TypeScript e Styled-Components.
- **Arquitetura de Conteúdo:** Internacionalização (i18n) descentralizada via arquivos JSON organizados em `src/content/` e `src/locales/`.

---

## 2. Execução dos Procedimentos de Gerência

### 2.1 Obtenção e Clonagem do Código-Fonte
Realizada a clonagem do código do repositório original para o ambiente local de desenvolvimento através da interface de linha de comando.

```bash
# Prompt de Comando - Windows Terminal
C:\Users\0031432512015> cd Desktop
C:\Users\0031432512015\Desktop> git clone https://github.com/Adrinlol/landy-react-template.git
Cloning into 'landy-react-template'...
remote: Enumerating objects: 1211, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (14/14), done.
Receiving objects: 100% (1211/1211), 896.10 KiB | 14.22 MiB/s, done.
Resolving deltas: 100% (506/506), done.
C:\Users\0031432512015\Desktop> code .
```

### 2.2 Instalação das Dependências (NPM)
Execução do comando de resolução de pacotes para mapear e baixar as bibliotecas declaradas no arquivo `package.json`.

```bash
# Terminal - Instalação de Dependências
C:\Users\0031432512015\Desktop\ProjetoGitTemplate> npm install

npm warn deprecated inflight@1.0.6: This module is not supported, and leaks memory.
npm warn deprecated @babel/plugin-proposal-private-methods@7.18.6: Please use @babel/plugin-transform-private-methods instead.
npm warn deprecated eslint@8.57.1: This version is no longer supported.

added 1420 packages, and audited 1421 packages in 45s
56 vulnerabilities (13 low, 15 moderate, 28 high, 3 critical)
```

### 2.3 Inicialização do Servidor Local
Validação da compilação em tempo real e testes no ambiente de homologação local (`http://localhost:3000`).

```bash
# Terminal - Servidor Local (React Scripts)
C:\Users\0031432512015\Desktop\ProjetoGitTemplate> npm start

> my-app@0.1.0 start
> react-scripts start

Starting the development server...
Compiled successfully!

You can now view my app in the browser.
  Local:            http://localhost:3000
  On Your Network:  http://192.168.185.28:3000
```

### 2.4 Versionamento e Publicação (Git & GitHub)
Configuração da origem remota, versionamento inicial do projeto e envio das alterações para a branch principal (`main`).

```bash
# Terminal - Versionamento Git
git init
git remote add origin https://github.com/nicollylemos/ProjetoGitTemplate.git
git branch -M main
git add .
git commit -m "Primeiro commit: projeto Landing Page Template"
git push -u origin main
```

### 2.5 Integração Contínua e Deploy (Vercel)
Configuração do pipeline de integração contínua (CI/CD) vinculando o repositório GitHub à plataforma Vercel, permitindo atualização automática em produção a cada novo commit.

---

## 3. Mapeamento da Estrutura de Arquivos

Organização lógica dos arquivos e itens de configuração que compõem o repositório da aplicação:

```text
PROJETO GITTEMPLATE /
|-- .github/              -> Workflows de automacao e configuracoes do GitHub
|-- node_modules/         -> Modulos e pacotes instalados via NPM
|-- public/               -> Ativos estaticos e modelo HTML principal (index.html, fontes)
|   |-- fonts/            -> Arquivos de fontes tipograficas (Motiva Sans)
|   |-- img/              -> Imagens e recursos graficos
|   |-- favicon.ico
|   |-- index.html
|   |-- manifest.json
|   `-- robots.txt
|-- src/                  -> Codigo-fonte em React e TypeScript
|   |-- common/           -> Componentes reutilizaveis (botoes, inputs, containers)
|   |-- components/       -> Componentes estruturais das secoes do site
|   |-- content/          -> Dados e textos da interface em formato JSON
|   |-- locales/          -> Arquivos de traducao e internacionalizacao (i18n)
|   |-- pages/            -> Estrutura e layout das paginas
|   |-- router/           -> Mapeamento e controle de rotas
|   |-- styles/           -> Estilizacao global e temas em Styled-Components
|   |-- index.tsx         -> Ponto de entrada da aplicacao React
|   |-- react-app-env.d.ts-> Tipagens globais do TypeScript
|   `-- translation.ts    -> Definicoes do sistema de idiomas
|-- .gitignore            -> Declaracao de arquivos e pastas ignorados no versionamento
|-- CODE_OF_CONDUCT.md    -> Diretrizes de conduta do projeto
|-- LICENSE               -> Licenca de uso do software
|-- package.json          -> Manifesto de configuracao, dependencias e scripts
|-- package-lock.json     -> Arvore exata de versoes de dependencias
|-- README.md             -> Documentacao principal do repositorio
|-- template.json         -> Definicao do modelo React
`-- tsconfig.json         -> Parametros de compilacao do TypeScript
```

---

## 4. Conclusão

O exercício prático da Tarefa 03 consolidou os conceitos essenciais da Gerência de Configuração de Software. A integração entre controle de versão (Git/GitHub), gerenciamento de dependências (NPM) e deploy contínuo (Vercel) garante rastreabilidade, padronização do ambiente e reprodutibilidade do projeto.
