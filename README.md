# portfolio-data-analytics-gregory
# Dashboard de Performance Logística (Power BI)

Este projeto foi desenvolvido para simular e analisar o **desempenho operacional de uma malha ferroviária**, aplicando conceitos de **Business Intelligence, Governança de Dados e Storytelling Analítico**.  
O painel foi criado no Power BI e integra métricas de **saturação, tempo parado, transit time e eficiência operacional (IEC)**.

---

## Objetivo
Demonstrar como dados operacionais podem ser transformados em **insights gerenciais e indicadores de eficiência**, apoiando a tomada de decisão em contextos logísticos reais.                

---

| Estrutura de Pastas | Descrição |
|----------------------|------------|
| `portfolio-data-analytics-gregory` | Pasta raiz do projeto |
| ├── `data_analytics/` | Contém os arquivos de base simulada |
| │ ├── `fato_operacao_logistica.csv` | Base de fatos principal |
| │ ├── `dim_sb.csv` | Dimensão dos trechos (SB) |
| │ └── `dim_trem.csv` | Dimensão dos trens |
| ├── `pbix/` | Dashboard final |
| │ └── `Dashboard_Performance_Logistica.pbix` | Arquivo Power BI |
| ├── `scripts/` | Simulação e tratamento de dados |
| │ └── `Simulação de Dados - Performance Logística — Eficiência de Trens - Carga - Entregas.ipynb` | Notebook Python |
| │ └── data_quality_check.ipynb
| ├── `images -1.2.3/` | Imagens e prévias do dashboard |
| │ └── `dashboard_preview.png` | Preview visual |
| ├── `README.md` | Documentação do projeto

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

## 🧠 Interpretação dos Indicadores

| Situação | Leitura | Ação Recomendada |
|-----------|----------|------------------|
| ⬆️ Saturação + ⬇️ IEC | Trecho sobrecarregado – gargalo operacional. | Revisar janelas de cruzamento e balanceamento de fluxo. |
| ⬆️ Tempo Parado + ⬇️ IEC | Perda de fluidez operacional. | Ações de manutenção e otimização logística. |
| ⬆️ Saturação + ⬆️ IEC | Trecho ideal – uso intenso e eficiente. | Manter boas práticas. |
| ⬇️ Saturação + ⬇️ IEC | Subutilização da capacidade. | Reavaliar demanda e programação. |

---

## 🧩 Tecnologias e Ferramentas
- **Power BI Desktop**
- **Python (pandas, numpy, faker)** – para simulação dos dados
- **GitHub** – versionamento e portfólio público

---
## 🧹 Data Quality Check

| Métrica | Resultado | Interpretação |
|----------|------------|----------------|
| **Completude Média** | 100% | Nenhum valor nulo encontrado nas colunas-chave |
| **Saturações Inválidas** | 0% | Todas dentro da faixa esperada (≤150%) |
| **Tempos Inválidos** | 0% | Nenhum tempo negativo ou inconsistente |
| **Duplicados** | 0% | Cada operação é única por Trem + SB + Data |
| **Integridade SB** | 100% | Todos os trechos da fato possuem correspondência na dimensão |
| **Integridade Trem** | 100% | Todos os trens da fato possuem correspondência na dimensão |

✅ As verificações indicam **dados consistentes, completos e bem modelados** para uso em análises operacionais e métricas de eficiência logística.


---
## 📈 Próximos Passos 
- Publicar o dashboard online (Power BI Service ou Power BI Public).  
- Integrar uma camada de governança com validação de metadados.

---

## 👤 Autor
**Krisley Gregory**  
Análise & Governança de Dados | Inteligência Operacional  
📍 [LinkedIn](https://linkedin.com/in/krisleygregory)  
📊 [GitHub](https://github.com/krisleygregory)




