# 📊 Gerenciamento de Indicadores — Diretoria | Dashboard Olist E-commerce

![capa do dashboard](./images/menu.png)

## 🔎 Sobre o projeto

Dashboard interativo em Power BI desenvolvido para consolidar os principais indicadores de um marketplace de e-commerce, com base no **dataset público da Olist** (Brazilian E-Commerce Public Dataset, Kaggle). O projeto simula o trabalho de um analista de BI entregando uma central de indicadores para a diretoria, cobrindo 6 visões de negócio: Produto, Pagamento, Pedido, Avaliações, Vendedores e Vendas.

**Este projeto foi desenvolvido para fins de portfólio**, com foco em demonstrar ETL, modelagem de dados, DAX avançado e boas práticas de UX em BI.

## 🎯 Objetivo

Dar à diretoria uma visão unificada e navegável da operação do marketplace — do funil de pedidos ao comportamento de pagamento, avaliação de clientes e performance de vendedores — permitindo identificar rapidamente gargalos, oportunidades e tendências.

## 🗺️ Estrutura do dashboard

O dashboard é organizado em uma página inicial (home) com navegação por botões, dividida em 3 blocos temáticos:

| Bloco | Páginas | Técnicas aplicadas |
|---|---|---|
| **Análises Gerais** | Visão Produto, Visão Pagamento | KPIs gerais, segmentação de categorias e formas de pagamento |
| **Metas Fixas, Clusterização e Principais Influências** | Visão Pedido, Visão Avaliações | Metas fixas, clusterização (segmentação de clientes/pedidos), análise de principais influências (drivers) |
| **Metas Dinâmicas, Análise Geográfica, Pareto, Cohort e Inteligência Temporal** | Visão Vendedores, Visão Vendas | Metas dinâmicas, mapa geográfico, curva de Pareto, análise de cohort, inteligência temporal (comparativos entre períodos) |

## ❓ Perguntas de negócio respondidas

- **Visão Produto:** quais categorias de produto mais vendem e quais geram mais receita?
- **Visão Pagamento:** quais formas de pagamento (cartão, boleto, voucher) e quantidade de parcelas predominam?
- **Visão Pedido:** qual o status dos pedidos (entregues, cancelados, atrasados) e como se comportam frente às metas?
- **Visão Avaliações:** qual a nota média (review score) e quais fatores mais influenciam avaliações ruins?
- **Visão Vendedores:** quem são os vendedores com melhor/pior desempenho e como se distribuem geograficamente?
- **Visão Vendas:** como a receita evolui ao longo do tempo e quais padrões de sazonalidade/cohort aparecem?

## 🖼️ Prints do dashboard

> Como você optou por imagens estáticas, esta é a seção mais importante do README — é o que o recrutador vai ver primeiro, sem precisar abrir o Power BI.
>
> Basta colocar os prints com estes nomes dentro da pasta `images/` do repositório (são os mesmos nomes de arquivo do seu export original).

### Home — Navegação
![home](./images/menu.png)

### Visão Produto
![visão produto](./images/Visão_produto.png)
32.951 produtos cadastrados em 74 categorias, com destaque para Cama_Mesa_Banho (3.029), Esporte_Lazer (2.867) e Móveis_Decoração (2.657).

### Visão Pagamento
![visão pagamento](./images/Visão_pagamento.png)
R$ 1.601 Mi em pagamentos, com Cartão de Crédito respondendo por 73,92% do volume (77 mil pagamentos), seguido de Boleto (19,04%) e Voucher (5,56%).

### Visão Pedido
![visão pedido](./images/Visão_pedidos.png)
54.011 pedidos em 2018 (+19,76% vs. 2017), mas 25,15% abaixo da meta anual de 72,16 mil — SP, RJ e MG concentram o maior volume de pedidos.

### Visão Avaliações
![visão avaliações](./images/Visão_avaliacoes.png)
77,14% das avaliações são "Ótima", com tempo médio de 3,42 dias para retorno de avaliações sem resposta no mesmo dia; clientes do Amapá (AP) têm 1,18x mais chance de dar avaliação "Ótima".

### Visão Vendedores
![visão vendedores](./images/Visão_vendedores.png)
3.095 vendedores, dos quais 2.376 bateram a meta; apenas 3 vendedores romperam a marca de R$500 mil em vendas — SP concentra praticamente toda a receita entre os estados.

### Visão Vendas
![visão vendas](./images/Visão_vendas.png)
R$ 1.359 Mi em vendas totais; o acumulado do ano atual (R$750,66 Mi) já supera o do ano anterior no mesmo período (R$603 Mi), taxa de crescimento acumulado de 24,39%.

📄 **[Baixe o PDF completo do dashboard aqui](./Dashboard_Completo.pdf)** — todas as páginas navegáveis, sem precisar do Power BI instalado.

### Bônus — Análise de Cohort (retenção de vendedores)
![análise de cohort](./images/Analise_cohort.png)

## 💡 Principais insights

- Em 2018 a empresa cresceu 19,76% em pedidos frente a 2017, mas ficou 25,15% abaixo da meta anual — evidenciando que metas estavam desalinhadas com a capacidade real de crescimento.
- Cartão de crédito domina os pagamentos (73,92%), concentração que pode ser explorada em negociações com operadoras ou em campanhas de meios alternativos.
- Apesar de 77,14% das avaliações serem "Ótima", o tempo médio de resposta a avaliações sem retorno no mesmo dia (3,42 dias) é um ponto de atenção para retenção de clientes.
- A receita de vendedores é extremamente concentrada: apenas 3 dos 3.095 vendedores romperam R$500 mil em vendas, e SP domina o total de vendas por estado — um sinal claro de dependência de poucos players/regiões (padrão também confirmado pela curva de Pareto 80-20 na Visão Vendas).
- O catálogo de produtos é liderado por categorias de casa e lazer (Cama_Mesa_Banho, Esporte_Lazer, Móveis_Decoração), o que pode orientar decisões de sortimento e marketing.

## 🗂️ Fonte dos dados

- **Origem:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle)
- **Descrição:** dados reais e anonimizados de ~100 mil pedidos feitos na Olist entre 2016 e 2018, em múltiplos marketplaces brasileiros
- **Tabelas utilizadas:**
  - `olist_orders_dataset` — pedidos e seus status/datas
  - `olist_order_items_dataset` — itens de cada pedido (preço, frete)
  - `olist_order_payments_dataset` — forma e valor de pagamento
  - `olist_order_reviews_dataset` — avaliações dos clientes
  - `olist_products_dataset` — atributos dos produtos
  - `olist_sellers_dataset` — vendedores e sua localização
  - `olist_customers_dataset` — clientes e sua localização
  - `product_category_name_translation` — tradução das categorias (PT → EN)
  - `olist_geolocation_dataset` — coordenadas geográficas (usada no mapa da Visão Vendedores)
- **Período analisado:** 2016–2018

## 🛠️ Tecnologias e técnicas utilizadas

| Etapa | Ferramenta/Técnica |
|---|---|
| ETL | Power Query (integração das múltiplas tabelas da Olist) |
| Modelagem | Modelo estrela (star schema) com fato Pedidos/Itens e dimensões Produto, Cliente, Vendedor, Pagamento, Tempo |
| Cálculos | DAX — metas fixas e dinâmicas, clusterização, Pareto, cohort, comparativos temporais |
| Visualização | Power BI Desktop, navegação por página inicial com botões |
| Versionamento | Git/GitHub |

### Exemplos de medidas DAX criadas

```DAX
Total de Vendas = SUM(Order_Items[price])

Taxa de Crescimento (17-18) = 
DIVIDE([Qtd. de Pedidos 2018] - [Qtd. de Pedidos 2017], [Qtd. de Pedidos 2017])

% Atingimento da Meta Anual = 
DIVIDE([Qtd. de Pedidos], [Meta Anual de Pedidos]) - 1
```

*(substitua pelos exemplos reais mais relevantes do seu modelo — especialmente as medidas de clusterização (dispersão por estado/score na Visão Avaliações), Pareto 80-20 (ranking acumulado por estado na Visão Vendas) e cohort (retenção de vendedores mês a mês), que são os maiores diferenciais técnicos do projeto)*

## 📁 Estrutura do repositório

```
├── images/                  # prints de todas as páginas do dashboard
├── Dashboard_Completo.pdf   # export em PDF para visualização sem Power BI
├── gerenciamento-indicadores-olist.pbix   # arquivo original do Power BI
├── dataset/                 # LEIA-ME.md com o link do Kaggle (dados não versionados por serem grandes/públicos)
├── CONTEXTO_PROJETO.md      # contexto detalhado do projeto
└── README.md
```

## 👀 Como visualizar

- **Sem Power BI instalado:** veja os [prints acima](#-prints-do-dashboard) ou baixe o [PDF completo](./Dashboard_Completo.pdf)
- **Com Power BI Desktop:** baixe o arquivo `.pbix` deste repositório e abra localmente

## 🧠 Aprendizados

[O que foi mais desafiador tecnicamente? Ex: "Implementar a análise de cohort em DAX puro" ou "Modelar a clusterização de clientes sem usar Python, apenas DAX/Power Query".]

## 📬 Contato

- LinkedIn: [linkedin.com/in/iannfava](https://www.linkedin.com/in/iannfava)
- E-mail: iannfava@gmail.com

---
⭐ Se este projeto foi útil ou interessante, deixe uma estrela no repositório!
