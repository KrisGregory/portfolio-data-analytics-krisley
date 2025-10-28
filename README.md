# 🚂 Dashboard de Performance Logística (Power BI)

Este projeto foi desenvolvido para simular e analisar o **desempenho operacional de uma malha ferroviária**, aplicando conceitos de **Business Intelligence, Governança de Dados e Storytelling Analítico**.  
O painel foi criado no Power BI Desktop e integra métricas de **Saturação**, **Tempo Parado**, **Transit Time** e **Eficiência Operacional (IEC)**.

---

## 🎯 Objetivo
Demonstrar como dados operacionais podem ser transformados em **insights gerenciais e indicadores de eficiência**, apoiando a tomada de decisão em contextos logísticos reais.                

---

## 🧱 Estrutura do Projeto

| Estrutura de Pastas | Descrição |
|----------------------|------------|
| `portfolio-data-analytics-gregory/` | Pasta raiz do projeto |
| ├── `data_analytics/` | Bases simuladas utilizadas no Power BI |
| │ ├── `fato_operacao_logistica.csv` | Base de fatos principal |
| │ ├── `dim_sb.csv` | Dimensão dos trechos (SB) |
| │ └── `dim_trem.csv` | Dimensão dos trens |
| ├── `pbix/` | Dashboard final |
| │ └── `Dashboard_Performance_Logistica.pbix` | Arquivo Power BI |
| ├── `scripts/` | Simulação e verificação de qualidade dos dados |
| │ ├── `Simulação de Dados - Performance Logística.ipynb` | Script de simulação em Python |
| │ └── `data_quality_check.ipynb` | Validação e checagem de qualidade dos dados |
| ├── `images/` | Imagens e prévias do dashboard |
| │ └── `dashboard_preview.png` | Preview visual |
| └── `README.md` | Documentação completa do projeto |

---

## 🧮 Métricas Principais (DAX)
- **Transit Time (h):** tempo médio de deslocamento dos trens  
- **Tempo Parado (%):** proporção de tempo ocioso em relação ao total da operação  
- **Saturação (%):** uso da capacidade bruta por trecho  
- **Eficiência Operacional (IEC):** indicador que relaciona fluidez e desempenho operacional  

---

## 📊 Storytelling Analítico
O painel é composto por **três visões integradas**, que se complementam para fornecer uma leitura completa da operação:

1. **Operação:** panorama geral de desempenho da malha ferroviária  
2. **Desempenho por SB:** comparação entre trechos, destacando gargalos e boas práticas  
3. **Paradas e Anomalias:** análise do impacto das paradas sobre a eficiência operacional  

Cada página foi construída com foco em **clareza executiva, narrativa analítica e coerência visual**, seguindo boas práticas de **Data Storytelling** e **Design de Informação**.

---

## 🧠 Interpretação dos Indicadores

| Situação | Leitura | Ação Recomendada |
|-----------|----------|------------------|
| ⬆️ Saturação + ⬇️ IEC | Trecho sobrecarregado – gargalo operacional. | Revisar janelas de cruzamento e balanceamento de fluxo. |
| ⬆️ Tempo Parado + ⬇️ IEC | Perda de fluidez operacional. | Ações de manutenção e otimização logística. |
| ⬆️ Saturação + ⬆️ IEC | Trecho ideal – uso intenso e eficiente. | Manter boas práticas. |
| ⬇️ Saturação + ⬇️ IEC | Subutilização da capacidade. | Reavaliar demanda e programação. |

---

## 🧩 Tecnologias e Ferramentas
- **Power BI Desktop** – modelagem, DAX e visualização  
- **Python (pandas, numpy, faker)** – simulação e tratamento dos dados  
- **GitHub** – portfólio e publicação oficial  
- **VS Code** – controle de versão local e integração dos scripts  
- **Dataflows (simulados)** – ingestão e transformação de dados  
- **Excel / CSV** – apoio para bases e checagens de consistência  

---

## ☁️ Ambiente e Governança

Por se tratar de um projeto pessoal desenvolvido em **ambiente gratuito (Power BI Desktop)**,  
a publicação direta no Power BI Service não foi realizada devido à restrição de login corporativo.  

Mesmo assim, o projeto mantém **padrões de governança e ciclo de vida analítico**, simulando todas as camadas de um ambiente corporativo:

| Camada | Descrição |
|---------|------------|
| **Dataflow (Origem e Tratamento)** | Ingestão, limpeza e padronização das bases simuladas |
| **Modelagem e DAX** | Criação de relações, medidas e KPIs governados |
| **Visões Analíticas** | Camadas de leitura executiva, operacional e diagnóstica |
| **Data Quality** | Validação de consistência, completude e integridade |
| **Documentação (GitHub)** | Centralização e rastreabilidade do projeto |

💡 As versões intermediárias e arquivos de apoio estão **armazenados localmente**, com controle de versionamento via **VS Code**.  
O repositório do GitHub contém a **versão oficial e consolidada** do projeto.

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

✅ As verificações indicam **dados consistentes, completos e bem modelados**, assegurando a confiabilidade dos indicadores operacionais.

---

## 🔄 Fluxo de Governança e Entrega Analítica

O projeto foi desenvolvido dentro de um **pipeline lógico de governança**, representando o ciclo completo de um produto analítico:

[Dataflow - Origem e Transformação]
↓
[Power BI Desktop - Modelagem e DAX]
↓
[Dashboard - Visões Executiva, Analítica e Diagnóstica]
↓
[Governança - Data Quality + Documentação GitHub]

---

Esse fluxo consolida todas as etapas de **ingestão, transformação, análise e entrega**, 
mantendo rastreabilidade e padronização ponta a ponta.

---

## 👤 Autor
**Krisley Gregory**  
Análise & Governança de Dados | Inteligência Operacional  
📍 [LinkedIn](https://linkedin.com/in/krisleygregory)  
📊 [GitHub](https://github.com/krisleygregory)




