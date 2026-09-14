# Script de Contexto do Projeto (para portfólio, LinkedIn e entrevistas)

> Preencha os campos entre colchetes [ ] restantes com números e achados reais. Depois de preenchido, use este texto em 3 lugares:
> 1. Na descrição do repositório no GitHub (campo "About")
> 2. No post do LinkedIn quando divulgar o projeto
> 3. Como "script" mental para responder "me fala sobre um projeto que você fez" em entrevistas

---

## Versão curta (1 parágrafo — usar no "About" do GitHub e no início do README)

Dashboard interativo em Power BI para gerenciamento de indicadores de diretoria, construído sobre o dataset público da Olist (e-commerce brasileiro, ~100 mil pedidos entre 2016 e 2018). O projeto simula a entrega de um analista de BI para uma diretoria comercial, consolidando 6 visões de negócio — Produto, Pagamento, Pedido, Avaliações, Vendedores e Vendas — com técnicas avançadas de metas fixas e dinâmicas, clusterização, análise de Pareto, cohort e inteligência temporal.

---

## Versão longa (para o corpo do README, seção "Sobre o Projeto")

**Contexto:** Criei este projeto para simular a rotina de um analista de BI dentro de um marketplace, transformando o dataset real da Olist em um painel de gestão pronto para diretoria — com navegação intuitiva por página inicial e indicadores segmentados por área de negócio.

**Problema de negócio:** A diretoria de um marketplace precisa acompanhar, em um único lugar, a saúde da operação: volume e status dos pedidos, comportamento de pagamento, satisfação do cliente (avaliações), performance dos vendedores e evolução das vendas — sem depender de relatórios manuais e desatualizados.

**O que eu fiz:**
- Integrei e tratei as múltiplas tabelas do dataset da Olist (pedidos, itens, pagamentos, avaliações, produtos, vendedores, clientes) usando Power Query
- Modelei os dados em um esquema estrela, com tabela fato de pedidos/itens conectada a dimensões de produto, cliente, vendedor, pagamento e tempo
- Criei medidas DAX para metas fixas e dinâmicas, clusterização (segmentação), curva de Pareto, análise de cohort e comparativos temporais (inteligência temporal)
- Construí 6 páginas de dashboard (Produto, Pagamento, Pedido, Avaliações, Vendedores, Vendas) organizadas por complexidade analítica, com uma página inicial de navegação
- Apliquei boas práticas de UX em BI: hierarquia visual clara, paleta de cores consistente (roxo/laranja), botões de navegação e agrupamento lógico por bloco temático

**Principais insights encontrados:**
- A empresa cresceu 19,76% em pedidos de 2017 para 2018 (45.101 → 54.011), mas ficou 25,15% abaixo da meta anual estabelecida — sinal de que as metas não estavam calibradas com a realidade do negócio.
- Existe forte concentração de receita: apenas 3 dos 3.095 vendedores romperam R$500 mil em vendas, e o estado de SP domina isoladamente o total de vendas por estado (efeito confirmado também pela curva de Pareto 80-20).
- 77,14% das avaliações são "Ótima", mas o tempo médio de resposta a avaliações sem retorno no mesmo dia é de 3,42 dias — um ponto de atenção operacional, já que clientes de alguns estados (ex: AP) têm até 1,18x mais chance de avaliar como "Ótima", sugerindo que a experiência varia bastante por região.
- Cartão de crédito concentra 73,92% dos pagamentos, o que pode orientar negociações com adquirentes ou estratégias de diversificação de meios de pagamento.

**Resultado / aprendizado:** A recomendação de negócio seria revisar o processo de definição de metas (que parecem desconectadas da realidade, com desvios de até -99,95% em alguns meses) e investigar a concentração de vendas em poucos vendedores/estados como risco de dependência. Tecnicamente, o maior aprendizado foi implementar clusterização (gráfico de dispersão por estado/score), curva de Pareto 80-20 e análise de cohort de retenção de vendedores usando DAX, além de criar um parâmetro dinâmico (what-if) para simular variação de meta direto na tela do dashboard.

---

## Script para entrevistas (formato STAR — Situação, Tarefa, Ação, Resultado)

- **Situação:** Um marketplace de e-commerce (dados reais da Olist) não tinha um painel único para a diretoria acompanhar pedidos, pagamentos, avaliações, vendedores e vendas.
- **Tarefa:** Construir um dashboard em Power BI que consolidasse essas 6 frentes com indicadores confiáveis e navegação simples.
- **Ação:** Integrei as tabelas via Power Query, modelei em esquema estrela, e criei medidas DAX para metas, clusterização, Pareto e cohort, organizando tudo em 6 páginas navegáveis por uma home.
- **Resultado:** Identifiquei que a receita está fortemente concentrada — apenas 3 de 3.095 vendedores superam R$500 mil em vendas e SP domina isoladamente o ranking por estado — um padrão clássico de Pareto 80-20 que direcionaria ações de diversificação de base de vendedores e mitigação de risco de dependência regional.

Dica: pratique falar essa versão em voz alta em ~60 segundos. É o que recrutadores técnicos costumam pedir.

---

## Tags/palavras-chave sugeridas para o repositório e LinkedIn

`#PowerBI` `#DAX` `#PowerQuery` `#BusinessIntelligence` `#DataAnalytics` `#Olist` `#Ecommerce` `#PortfolioDeDados`
