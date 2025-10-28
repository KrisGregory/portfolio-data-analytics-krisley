# Documentação Técnica – Dashboard de Performance Logística

## Visão Geral
Este documento descreve a estrutura técnica, modelagem e regras de governança aplicadas ao **Dashboard de Performance Logística**, desenvolvido em **Power BI Desktop**.  
O projeto foi construído com dados simulados e integra etapas de **ingestão, modelagem, análise e validação de qualidade**.

---

## Pipeline de Dados

[Python / CSV Simulado]
↓
[Power BI Desktop - Modelagem e DAX]
↓
[Dashboard - Visões Executiva, Analítica e Diagnóstica]
↓
[Governança - Data Quality + Documentação GitHub]



| Etapa | Tecnologia | Descrição |
|--------|-------------|-----------|
| **Origem (Dataflow Simulado)** | Python / pandas | Geração e padronização de dados em CSV |
| **Modelagem (Power BI)** | Power Query + DAX | Criação das relações e cálculos |
| **Governança** | Python / VS Code | Validação e versionamento local |
| **Visualização** | Power BI Desktop | Dashboard final consolidado |


---

## Modelagem de Dados

### Estrutura
| Tipo | Nome | Descrição |
|------|------|------------|
| **Fato** | `fato_operacao_logistica` | Operações ferroviárias (dados de desempenho) |
| **Dimensão** | `dim_sb` | Trechos (SB) da malha logística |
| **Dimensão** | `dim_trem` | Informações sobre os trens |

### 🔗 Relacionamentos
- `fato_operacao_logistica.id_sb` → `dim_sb.id_sb` (1:N)  
- `fato_operacao_logistica.id_trem` → `dim_trem.id_trem` (1:N)

---

## Dicionário de Dados

### fato_operacao_logistica
| Coluna | Tipo | Descrição | Nulo | Sensibilidade |
|---------|------|------------|------|----------------|
| `id_operacao` | Inteiro | Identificador da operação | Não | Baixa |
| `data_operacao` | Data | Data do evento operacional | Não | Baixa |
| `id_trem` | Inteiro | Código do trem | Não | Baixa |
| `id_sb` | Inteiro | Trecho operacional | Não | Baixa |
| `tempo_transit` | Decimal | Tempo em deslocamento (h) | Não | Baixa |
| `tempo_parado` | Decimal | Tempo total parado (h) | Não | Baixa |
| `capacidade_bruta` | Decimal | Capacidade total disponível | Não | Baixa |
| `carga_transportada` | Decimal | Carga efetivamente transportada | Não | Baixa |
| `km_percorrido` | Decimal | Quilometragem percorrida | Não | Baixa |
| `anomalias` | Inteiro | Número de anomalias | Sim | Média |

---

### dim_trem
| Coluna | Tipo | Descrição | Nulo |
|---------|------|------------|------|
| `id_trem` | Inteiro | Identificador do trem | Não |
| `prefixo` | Texto | Código identificador | Não |
| `modelo` | Texto | Tipo/modelo do trem | Sim |
| `empresa` | Texto | Operadora responsável | Sim |

---

### dim_sb
| Coluna | Tipo | Descrição | Nulo |
|---------|------|------------|------|
| `id_sb` | Inteiro | Identificador único | Não |
| `nome_sb` | Texto | Nome do trecho operacional | Não |
| `uf` | Texto | Unidade federativa | Sim |
| `tipo_trecho` | Texto | Tipo (principal/secundário) | Sim |

---

## Métricas e Fórmulas DAX

| Métrica | Fórmula | Descrição |
|----------|----------|-----------|
| **Transit Time (h)** | `AVERAGE(stg_dados_operacao_raw[tempo_transit])` | Tempo médio de deslocamento |
| **Tempo Parado (%)** | `DIVIDE(
    SUM(stg_dados_operacao_raw[tempo_parado]),
    SUM(stg_dados_operacao_raw[tempo_transit]) + SUM(stg_dados_operacao_raw[tempo_parado]))` | Percentual de tempo ocioso |
| **Saturação (%)** | `DIVIDE(SUM(fato_operacao_logistica[carga_transportada]), SUM(fato_operacao_logistica[capacidade_bruta]))` | Uso da capacidade |
| **IEC (Eficiência Operacional)** | `DIVIDE(
    SUM(stg_dados_operacao_raw[km_percorrido]),
    SUM(stg_dados_operacao_raw[tempo_transit]) + SUM(stg_dados_operacao_raw[tempo_parado])) *10` | Índice composto de eficiência |
| **Eficiência Operacional (IEC%)** | `DIVIDE(
    SUM(stg_dados_operacao_raw[km_percorrido]),
    SUM(stg_dados_operacao_raw[tempo_transit]) + SUM(stg_dados_operacao_raw[tempo_parado])
) /10` | Índice composto de eficiência |
| **Media IEC** | `COALESCE( AVERAGE(stg_dados_operacao_raw[eficiencia_operacional]),0 )` |
| **Media Saturacao** | `COALESCE( AVERAGE(stg_dados_operacao_raw[saturacao]) , 0 )`  |
| **Media Tempo Parado** | `COALESCE( AVERAGE(stg_dados_operacao_raw[tempo_parado]),0 )` |
| **Insight Operacional (Texto)** | `VAR mediaIEC = [_Media IEC]
VAR mediaSat = [_Media Saturacao]
VAR mediaParado = [_Media Tempo Parado]
RETURN
SWITCH(
    TRUE(),
    mediaIEC < 60 && mediaSat > 90,
        "⚠️ Alta saturação e baixa eficiência: indício de gargalo operacional.",
    mediaParado > 40 && mediaIEC < 60,
        "⚠️ Tempo parado elevado impactando a eficiência da via.",
    mediaIEC > 80 && mediaSat >= 70 && mediaSat <= 90,
        "✅ Operação equilibrada: boa utilização da capacidade e fluidez.",
    mediaSat < 60 && mediaIEC < 60,
        "ℹ️ Capacidade subutilizada: há espaço para otimização.",
    "Operação dentro da normalidade."
)` |


---

## Validação de Qualidade

| Verificação | Descrição | Resultado |
|--------------|------------|------------|
| **Completude** | Colunas críticas sem nulos | 100% preenchidas |
| **Integridade** | Todas as chaves válidas nas dimensões | OK |
| **Faixas válidas** | Saturação ≤150% e tempos ≥0 | OK |
| **Duplicidade** | Unicidade por Trem + SB + Data | OK |
| **Consistência** | Correlação coerente entre transit e parado | OK |

---

## Versionamento e Ambientes

| Item | Descrição |
|------|------------|
| **Ambiente Local** | Desenvolvimento no Power BI Desktop |
| **Versionamento** | Git local via VS Code |
| **Publicação Oficial** | Repositório público no GitHub |
| **Dataflow** | Simulado em Python / CSV |
| **Governança** | Manual e documentada (README + este arquivo) |

---

## Conclusão

Mesmo em ambiente gratuito, o projeto mantém as práticas de **Data Governance, Data Quality e Modelagem Dimensional**.  
A estrutura é escalável para ambientes corporativos com **Deployment Pipeline real** e integração com **Power BI Service**.
