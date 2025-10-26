# portfolio-data-analytics-gregory
# Dashboard de Performance Logística (Power BI)

Este projeto foi desenvolvido para simular e analisar o **desempenho operacional de uma malha ferroviária**, aplicando conceitos de **Business Intelligence, Governança de Dados e Storytelling Analítico**.  
O painel foi criado no Power BI e integra métricas de **saturação, tempo parado, transit time e eficiência operacional (IEC)**.

---

## Objetivo
Demonstrar como dados operacionais podem ser transformados em **insights gerenciais e indicadores de eficiência**, apoiando a tomada de decisão em contextos logísticos reais.

---

## Estrutura do Projeto
performance-logistica-pbi/
│
├── data/
│   ├── fato_operacao_logistica.csv
│   ├── dim_sb.csv
│   └── dim_trem.csv
│
├── pbix/
│   └── Dashboard_Performance_Logistica.pbix
│
├── scripts/
│   └── simulacao_base_dados.ipynb   
│
├── images/
│   └── dashboard_preview.png
│
├── README.md                     


---

## 🧮 Métricas Principais (DAX)
- **Transit Time (h):** tempo médio de deslocamento dos trens  
- **Tempo Parado (%):** proporção de tempo ocioso  
- **Saturação (%):** uso da capacidade bruta por trecho  
- **Eficiência Operacional (IEC):** indicador de fluidez operacional  

---

## 📊 Storytelling Analítico
O painel é dividido em três visões:

1. **Operação:** panorama geral de desempenho da malha.  
2. **Desempenho por SB:** comparação entre trechos, destacando gargalos e boas práticas.  
3. **Paradas e Anomalias:** análise do impacto das paradas sobre a eficiência operacional.

Cada página foi construída com foco em **clareza executiva, leitura analítica e coerência visual**, seguindo boas práticas de Data Storytelling.

---

## 🧩 Tecnologias e Ferramentas
- **Power BI Desktop**
- **Python (pandas, numpy, faker)** – para simulação dos dados
- **GitHub** – versionamento e portfólio público

---

## 📈 Próximos Passos
- Adicionar módulo de **Data Quality**, avaliando consistência e completude das bases simuladas.  
- Publicar o dashboard online (Power BI Service ou Power BI Public).  
- Integrar uma camada de governança com validação de metadados.

---

## 👤 Autor
**Krisley Gregory**  
Análise & Governança de Dados | Inteligência Operacional  
📍 [LinkedIn](https://linkedin.com/in/krisleygregory)  
📊 [GitHub](https://github.com/krisleygregory)




