# Dashboard de Performance Logística (Power BI)

*Este projeto segue o padrão de governança analítica e possui documentação técnica detalhada disponível em [DOCUMENTACAO_TECNICA.md](./DOCUMENTACAO_TECNICA.md).*

---

## Objetivo
Simular e analisar o **desempenho operacional de uma malha ferroviária**, aplicando conceitos de **Business Intelligence, Governança de Dados e Storytelling Analítico**.  
O painel foi criado no Power BI Desktop e integra métricas de **Saturação**, **Tempo Parado**, **Transit Time** e **Eficiência Operacional (IEC)**.

---

## Estrutura do Projeto

| Estrutura de Pastas | Descrição |
|----------------------|------------|
| `portfolio-data-analytics-gregory/` | Pasta raiz do projeto |
| ├── `data_analytics/` | Bases simuladas utilizadas no Power BI |
| │ ├── `fato_operacao_logistica.csv` | Base de fatos principal |
| │ ├── `dim_sb.csv` | Dimensão dos trechos (SB) |
| │ └── `dim_trem.csv` | Dimensão dos trens |
| ├── `pbix/` | Dashboard final |
| │ └── `Dashboard_Performance_Logistica.pbix` | Arquivo Power BI |
| ├── `scripts/` | Simulação e validação dos dados |
| │ ├── `Simulação de Dados - Performance Logística.ipynb` | Geração e tratamento de dados (Python) |
| │ └── `data_quality_check.ipynb` | Validação e consistência dos dados |
| ├── `images/` | Imagens e prévias do dashboard |
| │ └── `imagens_pbix_dax_painel.png` | Preview visual |
| └── `DOCUMENTACAO_TECNICA.md` | Detalhamento técnico, DAX e modelagem |
| └── `README.md` | Documentação completa do projeto |

---

## Ferramentas e Tecnologias
- **Power BI Desktop** – modelagem, DAX e visualização  
- **Python (pandas, numpy, faker)** – simulação e tratamento das bases  
- **GitHub + VS Code** – controle de versão local e documentação  
- **Excel / CSV** – estruturação das tabelas simuladas  

---

## Ambiente e Governança
O projeto foi desenvolvido em **ambiente gratuito (Power BI Desktop)**, com **padrão corporativo de governança de dados**.  
Mesmo sem publicação no Power BI Service, o ciclo completo foi reproduzido localmente:

[Dataflow (Simulado - Python/CSV)]
↓
[Power BI Desktop - Modelagem e DAX]
↓
[Dashboard - Visões Executiva, Analítica e Diagnóstica]
↓
[Governança - Data Quality + Documentação GitHub]

---

💡 As versões intermediárias foram controladas via **VS Code (git local)**.  
O repositório no GitHub contém a **versão consolidada e oficial** do projeto.

---

## Visões do Dashboard
1. **Operação** → visão executiva geral (indicadores de saturação, tempo parado e IEC).  
2. **Desempenho por SB** → comparação entre trechos, gargalos e boas práticas.  
3. **Paradas e Anomalias** → análise das causas de perda de fluidez operacional.

---

## Interpretação dos Indicadores

| Situação | Leitura | Ação Recomendada |
|-----------|----------|------------------|
| ⬆️ Saturação + ⬇️ IEC | Trecho sobrecarregado – gargalo operacional. | Revisar janelas de cruzamento e balanceamento de fluxo. |
| ⬆️ Tempo Parado + ⬇️ IEC | Perda de fluidez operacional. | Ações de manutenção e otimização logística. |
| ⬆️ Saturação + ⬆️ IEC | Trecho ideal – uso intenso e eficiente. | Manter boas práticas. |
| ⬇️ Saturação + ⬇️ IEC | Subutilização da capacidade. | Reavaliar demanda e programação. |

---

## Data Quality (Resumo)
As verificações aplicadas via `data_quality_check.ipynb` confirmam:

| Métrica | Resultado | Interpretação |
|----------|------------|----------------|
| **Completude Média** | 100% | Nenhum valor nulo em colunas críticas |
| **Integridade SB / Trem** | 100% | Todas as chaves válidas nas dimensões |
| **Duplicidade** | 0% | Cada operação é única |
| **Valores Inválidos** | 0% | Nenhum tempo negativo ou saturação acima de 150% |

✅ Dados consistentes, completos e adequados para uso analítico.  

---


## 👤 Autor
**Krisley Gregory**  
Análise & Governança de Dados | Inteligência Operacional  
📍 [LinkedIn](https://linkedin.com/in/krisleygregory)  
📊 [GitHub](https://github.com/krisleygregory)




