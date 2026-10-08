# 📊 Gerenciamento de Indicadores : Diretoria | Dashboard E-commerce

![capa do dashboard](./images/menu.png)

Dashboard em Power BI com 6 visões de negócio de um marketplace, construído sobre o dataset público da Olist (99.441 pedidos, 2016 a 2018).

> **Sobre este projeto:** a base veio de um curso guiado. Depois, fiz uma revisão independente e encontrei erros que distorciam os números, como valores em reais 100 vezes maiores e gráficos repetindo o mesmo total em todas as categorias. O que encontrei e como corrigi está na seção 5.

---

## 1. 🎯 Problema

Uma empresa de e-commerce tomava decisões "no achismo". A diretoria precisava de um painel único para acompanhar produto, pagamentos, pedidos, avaliações, vendedores e vendas, com metas e comparação entre períodos.

---

## 2. 🏗️ Arquitetura

### Fluxo do dado

```mermaid
flowchart TB
    A["📦 Fonte<br/>CSVs públicos da Olist (Kaggle)"]
    B["🔧 Power Query<br/>tipos com localidade en-US, limpeza,<br/>mesclagens e tabela Calendário"]
    C["🔗 Modelo de dados<br/>8 tabelas e 6 relacionamentos"]
    D["🧮 DAX<br/>metas, meta dinâmica, Pareto,<br/>cohort e inteligência temporal"]
    E["📊 Relatório<br/>menu, 6 visões e cohort"]
    F["🚀 Entrega<br/>.pbix, PDF e prints no GitHub"]
    A --> B --> C --> D --> E --> F
```

### Modelo de dados

![modelo de dados](./images/modelo_dados.png)

A tabela Calendário é compartilhada por pedidos, itens e avaliações, cada um pela sua data. Os relacionamentos `payments` → `orders` e `orders` ↔ `costumers` foram criados na revisão (seção 5).

---

## 3. 🛠️ Stack

| Etapa | Ferramenta |
|---|---|
| ETL | Power Query (M) |
| Modelagem e cálculos | Relacionamentos 1:N e 1:1, DAX |
| Visualização | Power BI Desktop, tema próprio e menu com botões |
| Versionamento | Git e GitHub |

---

## 4. 💻 Implementação

<table>
<tr>
<td width="50%"><img src="./images/Vis%C3%A3o_produto.png" width="100%"><br><b>Produto</b></td>
<td width="50%"><img src="./images/Vis%C3%A3o_pagamento.png" width="100%"><br><b>Pagamento</b></td>
</tr>
<tr>
<td><img src="./images/Vis%C3%A3o_pedidos.png" width="100%"><br><b>Pedido</b></td>
<td><img src="./images/Vis%C3%A3o_avaliacoes.png" width="100%"><br><b>Avaliações</b></td>
</tr>
<tr>
<td><img src="./images/Vis%C3%A3o_vendedores.png" width="100%"><br><b>Vendedores</b></td>
<td><img src="./images/Vis%C3%A3o_vendas.png" width="100%"><br><b>Vendas</b></td>
</tr>
</table>

📄 **[PDF com as 8 páginas](./Dashboard_Completo.pdf)**, para ver sem o Power BI. Para abrir o `.pbix`, use o Power BI Desktop. Os CSVs não estão no repositório: baixe no [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) e ajuste o caminho das fontes no Power Query.

---

## 5. 🔍 Revisão, resultados e próximos passos

### O que encontrei e corrigi

| Sintoma | Causa | Correção |
|---|---|---|
| Vendas de R$ 1,36 bilhão (o real é R$ 13,6 milhões) | CSVs usam ponto decimal; o Power BI em português leu `58.90` como `5890` | Tipagem com localidade en-US no Power Query e limites das medidas ajustados à escala real |
| Gráficos de pagamento com o mesmo total em todos os status | `payments` sem relacionamento com `orders` | Relacionamento `payments` → `orders`, que corrigiu 3 visuais |
| "Clientes" igual ao número de pedidos (99.441) | `customer_id` muda a cada pedido | Contagem por `customer_unique_id`: 96.096 clientes |
| Dois cartões com erro na Visão Avaliações | Fórmula comparava `review_id` (texto) com número | Troca para `review_score` |
| Meta mensal com -99,95% | Fim do dataset: só 4 pedidos em outubro de 2018 | Acompanhamento mensal até agosto, último mês completo |
| 2016 marcado como "meta atingida" | Meta vazia tratada como zero | Medida de status com `ISBLANK` e `HASONEVALUE` |

Também removi medidas duplicadas de exercícios e renomeei medidas com nomes enganosos.

<details>
<summary><b>Ver o antes e depois no código</b></summary>

**Separador decimal (Power Query, tabela `order_items`)**
```
Antes:  ... {"price", type number}, {"freight_value", type number}})
Depois: ... {"price", type number}, {"freight_value", type number}}, "en-US")
```

**Contagem de clientes (DAX)**
```DAX
Antes:  Qtd. de Clientes = DISTINCTCOUNT(orders[customer_id])
Depois: Qtd. de Clientes = DISTINCTCOUNT(costumers[customer_unique_id])
```

**Avaliações nota 4 e 5 (DAX)**
```DAX
Antes:  order_reviews[review_score] = 4 || order_reviews[review_id] = 5
Depois: order_reviews[review_score] = 4 || order_reviews[review_score] = 5
```

</details>

### Principais achados

- **Metas descoladas da realidade:** os pedidos cresceram 19,76% em 2018, mas a meta pedia 60%. Resultado: 25,15% abaixo da meta anual.
- **Recompra baixa:** 99.441 pedidos para 96.096 clientes. Quase todo cliente comprou uma única vez.
- **Vendas concentradas:** São Paulo responde por cerca de 38% da receita.
- **Pagamento:** cartão de crédito domina, com 73,92% dos pagamentos.
- **Satisfação:** 77,14% das avaliações são "Ótima".

### Próximos passos

- **Vendas por categoria:** ligar `order_items` a `products` pelo `product_id`, como fiz com `payments` e `orders`.
- **Atualização por qualquer pessoa:** criar um parâmetro no Power Query com a pasta dos CSVs, para quem baixar o projeto trocar um único valor.
- **Navegação online:** publicar no Power BI Service, que exige conta Microsoft corporativa ou de estudante.

---

📬 [LinkedIn](https://www.linkedin.com/in/iannfava) · iannfava@gmail.com
