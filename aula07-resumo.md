# Resumo e Atividade Prática - Aula 07: Testes Automatizados

**Disciplina:** Integração e Entrega Contínua (DevOps)  
**Instituição:** FATEC Sorocaba (Faculdade de Tecnologia)  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@fatec.sp.gov.br`)  
**Base de Estudo:** Slides da Aula 07 - Testes Automatizados (Takatu, D. S.)

---

## 1. Resumo Teórico da Aula 07

A Aula 07 aprofundou o papel dos **Testes Automatizados** e da validação de qualidade dentro das pipelines de Integração Contínua (CI), demonstrando como garantir a confiabilidade e a estabilidade do software antes que qualquer alteração avance para ambientes de homologação ou produção.

### Conceito e Importância dos Testes Automatizados
- **Definição:** Verificações executadas automaticamente por ferramentas para validar o comportamento esperado de uma aplicação sem depender de execução manual.
- **Benefícios Principais:**
  * **Redução de erros humanos:** Eliminação de validações manuais repetitivas e sujeitas a falhas.
  * **Aumento de velocidade:** Execução de dezenas ou centenas de cenários em segundos.
  * **Detecção rápida de falhas (*Fail Fast*):** Identificação imediata de regressões logo após um `push`.
  * **Consistência e Confiabilidade:** Garantia contínua de que novas alterações não quebram funcionalidades já existentes.

---

### Pipelines de Testes, Qualidade e Ecossistema
- **Pipeline de Testes:** Executada logo após a etapa de *build*, valida funcionalmente o sistema para garantir regressão zero.
- **Pipeline de Qualidade:** Realiza análise estática para verificar se o código atende aos padrões definidos antes de prosseguir (ex: **ESLint** para identificar variáveis não utilizadas como `no-unused-vars`, problemas de sintaxe ou fora de padrão).
- **GitHub Actions Marketplace:** Catálogo oficial de extensões e *Actions* prontas (criadas pelo GitHub, parceiros ou comunidade) para acelerar etapas de build, testes, qualidade, cache e deploy.
- **Regra de Interrupção ("Falhou? Para tudo"):** Caso qualquer teste ou verificação de qualidade falhe, a pipeline bloqueia o avanço da versão, fornece *feedback* imediato à equipe e impede a propagação de bugs.

---

### Estudo de Caso: Sistema Comercial de Descontos
Para ilustrar a aplicação prática, a aula apresentou um sistema web desenvolvido em React/JavaScript (`projeto-pipeline-testes`) para automatizar o cálculo de descontos de uma loja de roupas, substituindo o cálculo manual suscetível a erros:
- **Regra de Negócio:**
  * Compras abaixo de $\text{R\$ } 100,00$ recebem $10\%$ de desconto.
  * Compras iguais ou superiores a $\text{R\$ } 100,00$ recebem $5\%$ de desconto.
- **Arquitetura do Projeto (`src/`):**
  * `components/DiscountDashboard.jsx`: Interface de usuário.
  * `services/discountService.js`: Lógica e regras de cálculo de desconto.
  * `tests/unit/`, `tests/integration/`, `tests/performance/`: Separação modular dos níveis de teste.

---

### Os Três Pilares de Testes Abordados
1. **Testes Unitários (`unit/`):**
   - Validam funções, métodos e componentes de forma isolada e rápida.
   - *Exemplo de falha:* Alterar a regra para $15\%$ quando o teste unitário espera $10\%$ ou $5\%$.
2. **Testes de Integração (`integration/`):**
   - Verificam a comunicação e o funcionamento conjunto entre módulos, interface, serviços, APIs e bancos de dados.
   - *Exemplo de falha:* Alterar o texto de um botão na interface de `"Calcular Desconto"` para `"Calcular"`, quebrando o fluxo de interação esperado.
3. **Testes de Performance (`performance/`):**
   - Avaliam tempo de resposta, consumo de recursos e comportamento sob carga para prevenir gargalos.
   - *Exemplo de falha:* Definir um tempo máximo de resposta (SLA) rigoroso de $1\text{ms}$ que a aplicação não consegue cumprir.

## 3. Tabela Comparativa dos Tipos de Testes

| Tipo de Teste | Escopo de Validação | Objetivo Principal | Exemplo de Falha na Pipeline |
| :--- | :--- | :--- | :--- |
| **Testes Unitários** | Funções, métodos e regras isoladas (`discountService.js`) | Garantir que a lógica individual funciona conforme especificado | Regra de desconto alterada incorretamente de $10\%$ para $15\%$ |
| **Testes de Integração** | Comunicação entre UI, serviços, APIs e banco de dados | Validar fluxos completos e integração entre módulos | Alteração no rótulo do botão impedindo o disparo da ação |
| **Testes de Performance** | Tempo de resposta, carga e consumo de recursos | Identificar gargalos e assegurar escalabilidade/SLA | Tempo de resposta excedendo o limite máximo configurado ($1\text{ms}$) |
| **Análise Estática (Qualidade)** | Código-fonte completo (ESLint) | Padronização de código e prevenção de erros sintáticos | Declaração de variável não utilizada (`no-unused-vars`) |

---

## 4. Conclusão

A Aula 07 consolida o conceito de que qualidade em DevOps não é uma etapa isolada ao final do desenvolvimento, mas sim um processo contínuo e automatizado. Ao combinar análise estática (ESLint) com testes unitários, de integração e de performance executados automaticamente via GitHub Actions a cada `push` na branch `main`, garante-se que apenas código validado, performático e livre de regressões avance no ciclo de entrega.