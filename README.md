# SM7 — Engenharia de Software e IA com Bubble.io

Este repositório documenta o desenvolvimento de uma aplicação web de gestão em uma plataforma Low-Code (**Bubble.io**). O objetivo deste laboratório foi aplicar o ciclo completo de engenharia de software, utilizando a Inteligência Artificial como aceleradora, sem abrir mão do rigor técnico em segurança, escalabilidade e governança de dados.

---

## 📌 Informações do Projeto

* **Repositório:** `SM7---Engenharia-de-Software-e-IA-com-Bubble.io`
* **Protótipo Funcional:** [Acesse a aplicação no Bubble](https://projeto-engenharia.bubbleapps.io/version-test?debug_mode=true)
* **Contexto:** Disciplina de Análise e Desenvolvimento de Sistemas (2026).

---

## 📑 Resumo da Execução (Pipeline de Engenharia)

O projeto foi conduzido seguindo um pipeline profissional dividido em etapas críticas para garantir que o produto final fosse seguro, performático e bem estruturado:

### 1. Análise Crítica e Planejamento
Antes de iniciar a implementação, foi realizada uma auditoria sobre as limitações da IA generativa. Compreendendo que a IA entrega apenas um "blueprint" ou rascunho inicial, o foco do desenvolvedor concentrou-se onde a automação costuma falhar: na modelagem de regras de negócio complexas, lógicas de permissão e refinamento de UX.

### 2. Arquitetura de Dados (Pre-Build)
A modelagem do banco de dados foi planejada antes da interface para evitar *hardcoding* e retrabalho:
* **Mapeamento de Entidades:** Definição clara de *Data Types* estruturais (Ex: Usuário, Cliente, Orçamento).
* **Otimização de Relações:** Uso estratégico de campos de referência cruzada em vez de listas extensas acopladas, garantindo a performance do banco a longo prazo.
* **Option Sets:** Padronização de estados fixos (Ex: Status de Orçamento: *Pendente*, *Aprovado*, *Cancelado*) para evitar erros sintáticos e economizar requisições ao banco.

### 3. Desenvolvimento Assistido por IA & Refatoração
O Bubble AI foi utilizado para gerar a estrutura e o layout inicial das páginas. A intervenção humana focou na **Refatoração Front-end** — ajustando o alinhamento de containers via Flexbox para garantir a responsividade em diferentes telas — e na substituição de dados estáticos por fluxos de dados dinâmicos.

### 4. Segurança (Privacy by Design)
Esta foi a etapa mais crítica do laboratório. Foram removidas todas as permissões públicas padrão geradas pela IA, aplicando-se **Regras de Privacidade Estritas (*Privacy Rules*)**:
* **Regra Aplicada:** `This Data's Creator is Current User`
* **Objetivo:** Prevenir o vazamento de dados (*IDOR*) e garantir que um usuário autenticado jamais acesse informações de terceiros, mitigando vulnerabilidades críticas descritas no *OWASP Top Ten* para plataformas Low-Code/No-Code (LCNC).

### 5. Governança e Performance
* **Otimização de WUs (*Workload Units*):** As buscas (`Do a search for`) foram concentradas e filtradas diretamente em *Repeating Groups*, evitando varreduras desnecessárias no banco de dados e controlando o consumo de unidades de processamento.
* **Documentação In-Platform:** Os fluxos de trabalho (*Workflows*) foram categorizados e organizados por cores, além de documentados internamente através de *Notes*, garantindo que a lógica da aplicação não se tornasse uma "caixa preta".

---

## 🛠️ Entregáveis do Projeto

* **Link do Aplicativo:** Sistema web funcional com isolamento completo de dados por usuário.
* **Arquitetura do Banco de Dados:** Mapeamento lógico de tabelas, relacionamentos e *Option Sets*.
* **Evidências de Segurança e Governança:** Configuração de regras de privacidade e fluxos documentados na folha de estilos da aplicação.

---

## 🚪 Estratégia de Saída (Mitigação de Vendor Lock-in)

Por se tratar de uma plataforma Low-Code proprietária onde o Bubble retém o código-fonte proprietário, foi estabelecido um plano de contingência para garantir a portabilidade da aplicação:

1. **Exportação via JSON:** Habilitação e configuração da *Data API* nativa para permitir a extração automatizada e em massa de todas as tabelas de dados caso necessário.
2. **Plano de Portabilidade:** O mapeamento de entidades, regras de validação e fluxos documentados neste laboratório servem como um guia técnico pronto para uma eventual reescrita completa do sistema utilizando uma stack tradicional (como React no Front-end e Node.js no Back-end).
