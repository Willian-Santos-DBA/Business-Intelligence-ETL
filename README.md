# 📊 Business Intelligence: Do ETL à Análise Multidimensional

Este repositório contém os projetos práticos desenvolvidos para a área de Business Intelligence. O conteúdo está dividido em dois grandes pilares: a automação de Data Ingestion utilizando técnicas de Web Scraping e a implementação de um Data Warehouse com análise via Cubos de Fato.

## 🚀 Tecnologias Utilizadas
- **Banco de Dados:** PostgreSQL.
- **Linguagem:** Python 3.x.
- **Bibliotecas Python:** Pandas, Requests, BeautifulSoup (bs4) e Time.
- **Análise de Dados:** SQL Avançado (GROUP BY CUBE).

---

## 🏛️ Parte 01: Modelagem Multidimensional e Cubo de Fatos
O objetivo deste projeto foi desenvolver um sistema de análise de vendas para o varejo, transformando dados operacionais em informações estratégicas.

### Estrutura do Data Warehouse (Star Schema)
O banco de dados foi estruturado seguindo o modelo estrela para otimizar consultas analíticas:
- **Dimensões:** 
  - `dim_tempo`: Granularidade de data, mês e ano.
  - `dim_produto`: Detalhes descritivos (nome, categoria, preço).
- **Fato:** 
  - `fato_vendas`: Centraliza as métricas (quantidade e valor total) e as chaves estrangeiras.

### Diferencial Técnico: Análise via CUBE
Foi utilizada a cláusula `GROUP BY CUBE` do PostgreSQL para gerar uma visão 360° das vendas. Esta funcionalidade permite a extração automática de:
- **Vendas Específicas:** Cruzamento de categoria por mês.
- **Subtotais:** Faturamento total por mês e desempenho isolado por categoria.
- **Grand Total:** Receita total acumulada no período analisado.

---

## 🐍 Parte 02: Web Scraping e Ingestão de Dados (ETL)
Desenvolvimento de aplicações em Python para extração automatizada de dados de e-commerce, demonstrando a evolução de scripts estáticos para coleta dinâmica via API.

### 1. Versão Básica (HTML Parsing)
- **Alvo:** Website Books to Scrape.
- **Foco:** Mapeamento de tags HTML (`<article>`, `<h3>`, `<p>`) e extração de títulos e preços.

### 2. Versão Intermediária (Otimização para Negócios)
- **Melhoria:** Implementação de boas práticas de exportação para o mercado brasileiro.
- **Destaque:** Uso do separador `;` (`sep=';'`) e codificação `utf-8-sig` para garantir que o arquivo CSV seja aberto corretamente no Excel em português, evitando problemas de formatação para o usuário final.

### 3. Versão Avançada (Extração via API JSON)
- **Alvo:** API de catálogo da Max Titanium.
- **Técnicas de Engenharia de Dados Aplicadas:**
  - **Paginação Dinâmica:** Controle automático de loops para baixar o catálogo completo (50 em 50 produtos).
  - **Rate-Limiting:** Uso de `time.sleep()` para respeitar a carga do servidor.
  - **Data Cleaning:** Tratamento de duplicatas com Pandas e conversão de strings de preço para o padrão decimal brasileiro (troca de `.` por `,`).
  - **Resiliência:** Tratamento de exceções (`try/except`) para garantir que falhas em atributos individuais não interrompam o pipeline de coleta.

---
*Desenvolvido por: Willian Nunes dos Santos.*
