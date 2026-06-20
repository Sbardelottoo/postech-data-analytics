# POS TECH — Data Analytics · Tech Challenges

**Autor:** Leonardo Fernandes Sbardelotto · RM 368591  
**Curso:** Pós-Graduação em Data Analytics — FIAP / POS TECH  
**Período:** 2024 – 2025

Repositório com as entregas dos quatro Tech Challenges do curso de pós-graduação em Data Analytics. Cada fase cobriu um tema distinto, acumulando as disciplinas da etapa e exigindo uma entrega prática completa.

---

## 🔗 Relatórios Interativos

> Clique nos links abaixo para abrir os relatórios diretamente no navegador — sem baixar nenhum arquivo.

| Fase | Tema | Abrir relatório |
|------|------|----------------|
| Fase 1 | Exportações de vinho brasileiro | [📊 Ver relatório](https://sbardelottoo.github.io/postech-data-analytics/Fase-1/Entrega/relatorio_vinhos_fase1.html) |
| Fase 2 | Previsão do IBOVESPA | [📊 Ver relatório](https://sbardelottoo.github.io/postech-data-analytics/Fase-2/Entrega/relatorio_ibovespa_fase2.html) |
| Fase 3 | Análise PNAD COVID-19 | [📊 Ver relatório](https://sbardelottoo.github.io/postech-data-analytics/Fase-3/Entrega/relatorio_pnad_covid19.html) |
| Fase 4 | Sistema preditivo de obesidade | [📊 Ver dashboard](https://sbardelottoo.github.io/postech-data-analytics/Fase-4/Entrega/streamlit-obsesity/dashboard_obesidade.html) · [🚀 App Streamlit](https://app-obsesity-iq.streamlit.app/) |

---

## Visão Geral das Fases

| Fase | Tema | Ferramentas Principais | Resultado |
|------|------|------------------------|-----------|
| [Fase 1](#fase-1--análise-de-exportações-de-vinho-brasileiro) | Exportações de vinho brasileiro | Python · Pandas · Plotly | Análise exploratória + gráficos para investidores |
| [Fase 2](#fase-2--modelo-preditivo-ibovespa) | Previsão do IBOVESPA | Python · Scikit-learn · Google Colab | Classificador de tendência com Balanced Accuracy 60% |
| [Fase 3](#fase-3--análise-pnad-covid-19) | Comportamento da população na pandemia | SQL · BigQuery · Python | Relatório analítico interativo em HTML |
| [Fase 4](#fase-4--sistema-preditivo-de-obesidade) | Predição de nível de obesidade | XGBoost · Streamlit · Plotly | App preditivo deployado + dashboard analítico |

---

## Fase 1 — Análise de Vinhos e Derivados Brasileiros

**Contexto:** Atuando como Expert em Data Analytics de uma vinícola exportadora, o desafio foi construir um diagnóstico completo do setor brasileiro de vinhos para apresentação a investidores e acionistas.

**O que foi feito:**
- Diagnóstico 360° do setor cobrindo **4 dimensões**: exportações (compradores), importações (fornecedores), comercialização doméstica e produção
- Período analisado: **2009–2023** (janela escolhida por consistência dos dados e captura de ciclos-chave: pandemia, choque de fretes, guerra na Ucrânia)
- **Exportações:** 137 compradores identificados; top-10 respondem por 93,8% do volume; principais destinos: Rússia (42%) e Paraguai (39%)
- **Mapa Volume × Preço:** nichos premium (UK, Países Baixos, EUA) respondem por 17% do valor com apenas 6,9% do volume, a US$ 3,14/L — 2,5× o preço médio
- **Importações:** Chile, Argentina e Portugal consolidados como base (~78% do volume), com papel complementar de europeus premium (França US$ 5,52/L)
- **Comercialização interna:** 6,15 bi litros no período; Vinho de Mesa + Tinto dominam (62%); suco integral com aceleração estrutural pós-2018
- **Projeções:** tendências por série usando OLS e Holt-Winters para os próximos 5 anos
- Entrega reformulada como **relatório HTML interativo** com 11 gráficos Plotly (dark theme)

**Números-chave:**

| Indicador | Valor |
|-----------|-------|
| Total exportado (2009–2023) | ~78 Mi litros · US$ 98,8 Mi |
| Preço médio exportação | US$ 1,27/L |
| Concentração top-2 destinos | 81,5% do volume |
| Total importado (1970–2023) | ~1,51 Bi litros |
| Comercialização doméstica (2009–2023) | ~6,15 Bi litros |

**Estrutura da entrega:**
```
Fase-1/
├── Entrega/
│   └── relatorio_vinhos_fase1.html        # Relatório interativo HTML
└── Tech-Challenge-Fase-1/
    ├── POSTECH - Tech Challenge - Fase 1.pdf
    └── Base de dados.zip
```

**→ [Abrir relatório](https://sbardelottoo.github.io/postech-data-analytics/Fase-1/Entrega/relatorio_vinhos_fase1.html)**

---

## Fase 2 — Modelo Preditivo IBOVESPA

**Contexto:** Integrado a uma equipe de cientistas de dados de um fundo de investimentos, o desafio foi criar um modelo de Machine Learning capaz de prever se o índice IBOVESPA fecharia em **alta ou baixa** no dia seguinte.

**O que foi feito:**
- Coleta de dados históricos diários do IBOVESPA (2020–2026) — 1.449 pregões
- Feature engineering: 32 indicadores técnicos (médias móveis, MACD, RSI, volatilidade)
- Split temporal: treino nos primeiros 1.419 dias, teste nos últimos 30 pregões
- Avaliação por **Balanced Accuracy** (métrica correta para classe desbalanceada)
- Único modelo que separou as duas classes: HistGradientBoosting com BalAcc = 60%

**Resultados Reais do Modelo:**

| Modelo | Acurácia Teste | Balanced Accuracy |
|--------|:--------------:|:-----------------:|
| Logistic Regression | 66,7% | 50,0% |
| Random Forest | 66,7% | 50,0% |
| Extra Trees | 66,7% | 50,0% |
| **HistGradientBoosting (Final)** | **60,0%** | **60,0%** |
| Baseline (sempre Alta) | 66,7% | 50,0% |

> **Nota:** Accuracy sozinha engana — o baseline de sempre prever "Alta" atinge 66,7%. O HistGB é o único modelo que realmente aprende a separar as duas classes (BalAcc 60% vs 50% dos demais).

**Estrutura da entrega:**
```
Fase-2/
└── Entrega/
    └── TechChallenge_IBOV_Colab_Leonardo_Sbardelotto/
        ├── relatorio_ibovespa_fase2.html                        # Relatório interativo HTML
        └── TechChallenge_IBOV_Colab_Leonardo_Sbardelotto.ipynb  # Notebook
```

**→ [Abrir relatório](https://sbardelottoo.github.io/postech-data-analytics/Fase-2/Entrega/relatorio_ibovespa_fase2.html)**

---

## Fase 3 — Análise PNAD COVID-19

**Contexto:** Contratado como Expert em Data Analytics por um grande hospital, o objetivo foi entender o comportamento da população durante a pandemia de COVID-19 usando os dados do PNAD-COVID-19 do IBGE, para subsidiar o planejamento hospitalar em caso de novo surto.

**O que foi feito:**
- Seleção de 20 variáveis-chave da pesquisa PNAD-COVID-19 (set–nov 2020)
- Organização da base em banco de dados em nuvem (Google BigQuery)
- Análise de 3 dimensões: sintomas clínicos · comportamento da população · características econômicas
- ~1,15 milhão de respondentes ponderados · 810 grupos analíticos
- Identificação de indicadores-chave para planejamento hospitalar

**Estrutura da entrega:**
```
Fase-3/
└── Entrega/
    └── relatorio_pnad_covid19.html    # Relatório analítico interativo
```

**→ [Abrir relatório](https://sbardelottoo.github.io/postech-data-analytics/Fase-3/Entrega/relatorio_pnad_covid19.html)**

---

## Fase 4 — Sistema Preditivo de Obesidade

**Contexto:** Como cientista de dados de um hospital, o desafio foi desenvolver um modelo de Machine Learning para auxiliar médicos a diagnosticar o nível de obesidade de pacientes com base em hábitos alimentares, histórico familiar e estilo de vida.

**O que foi feito:**
- Pipeline completo de ML: limpeza → feature engineering → treinamento → avaliação
- Feature derivada **BMI (IMC)** criada a partir de Peso e Altura — principal preditor (51,8% de importância)
- Comparação de 3 modelos: Logistic Regression · Random Forest · **XGBoost (selecionado)**
- Acurácia final: **98,1%** no conjunto de teste · cross-val 5-fold: **98,6%**
- Aplicação preditiva interativa deployada no Streamlit Cloud
- Dashboard analítico HTML com insights para a equipe médica

**Resultados do Modelo:**

| Modelo | Acurácia Teste | Cross-Val (5-fold) |
|--------|:--------------:|:------------------:|
| Logistic Regression | 83,7% | 84,1% ± 1,2% |
| Random Forest | 98,3% | 98,4% ± 0,8% |
| **XGBoost (Final)** | **98,1%** | **98,6% ± 0,7%** |

**Principais insights:**
- IMC explica 51,8% da predição isoladamente
- 100% dos pacientes com Obesidade III têm histórico familiar
- Sedentarismo: frequência de atividade física cai 38% do Peso Normal para Obesidade III
- Sobrepeso aparece em média aos 23,4 anos

**Estrutura da entrega:**
```
Fase-4/
└── Entrega/
    ├── index.html                          # Página hub com todos os links da Fase 4
    └── streamlit-obsesity/
        ├── dashboard_obesidade.html        # Dashboard analítico interativo
        ├── app_streamlit.py                # Aplicação preditiva (Streamlit)
        ├── pipeline_ml.py                  # Pipeline completo de ML
        ├── clinical_helpers.py             # Helpers clínicos
        ├── model_xgb.pkl                   # Modelo treinado
        ├── Dados Obesity.csv               # Dataset (2.111 registros)
        └── requirements.txt
```

**→ [Página da Fase 4](https://sbardelottoo.github.io/postech-data-analytics/Fase-4/Entrega/index.html)**  
**→ [Dashboard analítico](https://sbardelottoo.github.io/postech-data-analytics/Fase-4/Entrega/streamlit-obsesity/dashboard_obesidade.html)**  
**→ [App Streamlit (ao vivo)](https://app-obsesity-iq.streamlit.app/)**  
**→ [Código-fonte no GitHub](https://github.com/Sbardelottoo/streamlit-obsesity)**

**Como executar localmente:**
```bash
cd Fase-4/Entrega/streamlit-obsesity
pip install -r requirements.txt
streamlit run app_streamlit.py
```

---

## Stack Tecnológica

| Área | Ferramentas |
|------|-------------|
| Linguagem | Python 3.x |
| Análise de dados | Pandas · NumPy |
| Machine Learning | Scikit-learn · XGBoost |
| Visualização | Plotly · Chart.js · Matplotlib |
| Aplicação web | Streamlit |
| Banco de dados | BigQuery (Google Cloud) |
| Notebooks | Google Colab · Jupyter |

---

*POS TECH Data Analytics · FIAP · 2024–2025*
