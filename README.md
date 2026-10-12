# 🎮 Xbox Game Pass - Sales & Subscriptions Dashboard

![Xbox Badges](https://shields.io)
![UI Design](https://shields.io)
![Status](https://shields.io)

## 📌 Sobre o Projeto
Este projeto consiste no desenvolvimento de um **Dashboard de Vendas e Assinaturas** para o ecossistema Xbox (Xbox Game Pass Ultimate, Standard e Core). O objetivo principal foi transformar uma base de dados bruta contendo o histórico de assinantes e vendas de serviços complementares (*Add-ons* como EA Play e Minecraft Season Pass) em uma ferramenta visual e analítica de tomada de decisão, simulando as demandas reais de uma equipe de Business Intelligence (BI).

O design e a interface foram projetados seguindo as diretrizes de **UI/UX corporativo**, utilizando a identidade visual oficial da marca Xbox, segmentação de dados (filtros dinâmicos) e um menu lateral de navegação integrado.

---

## 🛠️ Arquitetura do Arquivo Excel
Para garantir a escalabilidade e a manutenção do projeto (padrão de mercado), o arquivo `.xlsx` foi estruturado em três camadas distintas:

1. **`📺 Dashboard`**: A camada de apresentação (Front-end). Contém os indicadores-chave de performance (KPIs), tabelas analíticas secundárias, gráficos dinâmicos e o menu lateral estilizado. 100% limpa, sem linhas de grade visíveis.
2. **`📊 Tabelas_Dinamicas`**: A camada de processamento (Middle). Onde os dados brutos são agrupados, filtrados e sumarizados para alimentar a camada visual sem sobrecarregar o painel principal.
3. **`🗃️ Dados_Vendas`**: A camada de armazenamento (Back-end). Contém a base de dados bruta com as informações de ID, Plano, Tipo de Assinatura, Cupons e Valores Totais.

---

## 🎨 Identidade Visual e Design System
A interface foi construída utilizando conceitos de *Negative Zone* (fundos claros e limpos para maior legibilidade) contrastando com componentes escuros (*Dark Mode*) no menu de navegação e Kpis para simular o ecossistema de um software de gerenciamento da Microsoft.

*   **Verde Xbox Principal**: `#22C55E` (Destaques, botões ativos e KPIs positivos)
*   **Verde Xbox Secundário**: `#9BC848`
*   **Menus / Painel Lateral**: `#1F2937` e `#374151` (Grafite escuro para profundidade visual)
*   **Fundo de Tela**: `#E8E6E9` (Cinza ultra-claro para reduzir a fadiga visual)

---

## 🧠 Resolução das Perguntas de Negócio
O desafio exigia a extração de métricas específicas para responder a dores reais da operação de vendas. Abaixo estão as metodologias aplicadas:

### 📈 Métricas Gerais Calculadas
*   **Faturamento Bruto Total**: Centralizado no card principal utilizando `=SUM(Dados_Vendas[Total Value])`.
*   **Volume de Assinantes**: Contagem total de IDs ativos via `=COUNTA(Dados_Vendas[Subscriber ID])`.
*   **Ticket Médio**: Valor médio gasto por transação utilizando `=AVERAGE(Dados_Vendas[Total Value])`.

### 🔍 Perguntas Específicas Respondidas no Painel

| Pergunta de Negócio | Abordagem Técnica Aplicada | Resolução / Insights |
| :--- | :--- | :--- |
| **1. Qual o faturamento total de vendas de planos mensais/anuais?** | Criação de matriz de sumarização cruzando `Subscription Type` com `Total Value`. | Permite identificar qual ciclo de faturamento traz mais estabilidade financeira para o fluxo de caixa. |
| **2. Qual o faturamento por tipo de plano separado por Auto Renovação?** | Aplicação da fórmula `=SUMIF` segmentando as vendas totais com base na flag `Yes/No` da coluna `Auto Renewal`. | Identifica o comportamento de retenção do cliente e a previsibilidade de receita recorrente. |
| **3. Qual o total de vendas do EA Play Season Pass?** | Sumarização filtrada das assinaturas agregadas que possuem a flag `EA Play Season Pass = Yes` vinculada ao plano *Ultimate*. | Mede a adesão do público à principal parceria de conteúdo de terceiros do ecossistema. |
| **4. Qual o total de vendas do Minecraft Season Pass?** | Mapeamento financeiro da receita direta gerada pelo ecossistema Minecraft dividida por categoria de plano (*Standard* vs. *Ultimate*). | Identifica o poder de cross-selling do produto em diferentes faixas de preço de planos base. |

---

## 🚀 Diferenciais Técnicos Implementados (Para Recrutadores)
*   **Menu Lateral Estilizado**: Simula a navegação de um aplicativo web através do uso de blocos de células e segmentadores de dados posicionados estrategicamente.
*   **Fórmulas Totalmente Dinâmicas**: Nenhuma métrica ou totalizador foi digitado manualmente (*hardcoded*). Se uma nova linha de venda for adicionada à base, todo o dashboard se atualiza automaticamente.
*   **Formatação Condicional Avançada**: Cores de status adaptativas para destacar variações positivas e negativas de desempenho.
*   **Design Clean e Executivo**: Alinhamento milimétrico de cards, tipografia padronizada (Segoe UI / Calibri) e ausência de elementos visuais desnecessários (*chartjunk*).

---

## 📂 Como Reproduzir ou Testar o Projeto
1. Faça o clone deste repositório ou baixe diretamente o arquivo localmente.
2. Abra o arquivo `dashboard_xbox_finalizado.xlsx` no Microsoft Excel (recomendado Excel 2019 ou superior para total compatibilidade de recursos visuais).
3. Navegue pelas tabelas ou utilize os **Segmentadores de Dados (Filtros)** para interagir e ver os gráficos e KPIs mudando em tempo real.

---
⭐ *Este projeto foi desenvolvido como um desafio técnico de negócios e análise de dados para processos seletivos.*
