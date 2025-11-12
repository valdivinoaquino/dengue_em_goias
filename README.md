# 🦟 Dengue em Goiás — Painel de Análise de Notificações e Tendências

<img width="1782" height="997" alt="image" src="https://github.com/user-attachments/assets/31f308bd-39fb-4dac-9874-02fb129cea84" />

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

### Casos de Dengue Confirmados
```DAX
03.01_QTD_DENGUE_NOTIFICADO =
CALCULATE(
    COUNTROWS('dengue-casos-notificados'),
    FILTER(
        'dengue-casos-notificados',
        'dengue-casos-notificados'[classificao] IN {"DENGUE", "DENGUE GRAVE"}
    )
)
```

### Óbitos confirmados pelo agravo
```DAX
02.01_QTD_OBITO_PELO_AGRAVO =
CALCULATE(
    COUNTROWS('dengue-casos-notificados'),
    'dengue-casos-notificados'[evolucao] = "OBITO PELO AGRAVO"
)
```

### Taxa de letalidade (%)
```DAX
04.01_TX_LETALIDADE =
DIVIDE([02.01_QTD_OBITO_PELO_AGRAVO], [03.01_QTD_DENGUE_NOTIFICADO]) * 100
```

### Formatação automática dos KPIs
```DAX
01.01_COUNT_FORMATADO =
VAR QTD = [01.01_COUNT]
RETURN
SWITCH(
    TRUE(),
    QTD >= 1000000, FORMAT(DIVIDE(QTD,1000000),"0") & " Mi",
    QTD >= 1000, FORMAT(DIVIDE(QTD,1000),"0") & " Mil",
    FORMAT(QTD,"0")
)
```

---

## 🎨 Design e Layout

- **Paleta de Cores:** Azul, amarelo, branco e vermelho (alerta).  
- **Tipografia:** Montserrat e Poppins (limpas e tecnológicas).  
- **Estilo:** Minimalista, informativo e corporativo.  
- **Layout:**  
  - Cabeçalho com KPIs principais  
  - Blocos de gráficos analíticos  
  - Mapa georreferenciado  
  - Rodapé institucional com créditos e fonte dos dados  

---

## 🧭 Insights Identificados

- **Pico de notificações entre março e abril**, indicando sazonalidade da doença.  
- **Maior concentração de casos na região metropolitana de Goiânia.**  
- **Taxa de letalidade baixa**, mas com variações significativas entre municípios.  
- **Predominância de confirmação clínica/laboratorial sobre suspeitos.**

---

## 🧩 Autor

**Desenvolvido por [Valdivino Aquino]([https://www.linkedin.com/in/valdivinoaquino/](https://www.linkedin.com/in/valdivino-aquino-ti-goiania/)**  
📧 aquino.sti@hotmail.com 
💼 DeskBI | Business Intelligence & Data Analytics  

---

## 📚 Fonte dos Dados

- Portal de Dados Abertos do Governo de Goiás  
  🔗 [https://dadosabertos.go.gov.br](https://dadosabertos.go.gov.br)  
- Conjunto de dados: *Casos de Dengue Notificados no Estado de Goiás*

---

## 🏁 Status do Projeto

✅ Concluído — Versão 1.0  
📅 Atualização: Novembro/2025  
📍 Power BI Dashboard

---

> _“Dados bem apresentados salvam vidas, guiando decisões mais inteligentes na saúde pública.”_  
> — **Valdivino Aquino**
