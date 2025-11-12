# 🦟 Dengue em Goiás — Painel de Análise de Notificações e Tendências

<img width="1782" height="997" alt="image" src="https://github.com/user-attachments/assets/9fcf8bb3-28f7-4ace-90b9-e1ae348881a9" />

## 📊 Visão Geral

Este projeto apresenta um **painel interativo em Power BI** com foco na **análise epidemiológica da Dengue no estado de Goiás**.  
O objetivo é oferecer uma **visão clara e dinâmica** sobre notificações, confirmações, óbitos e taxa de letalidade, facilitando a tomada de decisão e o acompanhamento de tendências ao longo do tempo.

---

## 🧠 Principais Indicadores

| Indicador | Descrição |
|------------|------------|
| **Notificações** | Total de casos notificados de dengue. |
| **Dengue Confirmado** | Casos confirmados laboratorialmente ou clinicamente. |
| **Óbitos** | Quantidade de óbitos confirmados por dengue. |
| **Taxa de Letalidade** | Relação entre óbitos e casos confirmados. |
| **Média Mensal de Notificações** | Média de casos notificados por mês no período analisado. |

---

## 🗺️ Recursos do Painel

- **Mapa interativo** com distribuição espacial dos casos notificados por município.  
- **Gráficos temporais** para análise de tendência mensal.  
- **Indicadores dinâmicos (KPIs)** com formatação automática em milhares (“Mil”) e milhões (“Mi”).  
- **Visualização de classificações dos casos** (Suspeito, Confirmado, Descartado, etc).  
- **Critério de confirmação** (clínico, laboratorial, em investigação).  
- **Design responsivo e limpo**, com hierarquia visual clara e acessível.

---

## ⚙️ Tecnologias Utilizadas

- **Power BI Desktop**
- **DAX (Data Analysis Expressions)**
- **Dados públicos do portal [dadosabertos.go.gov.br](https://dadosabertos.go.gov.br)**
- **Fonte de dados**: Casos notificados de dengue em Goiás
- **Mapas**: Camadas geográficas via Microsoft Bing Maps

---

## 🧮 Principais Medidas DAX

### Total de notificações
```DAX
01.01_COUNT =
COUNTROWS('dengue-casos-notificados')
