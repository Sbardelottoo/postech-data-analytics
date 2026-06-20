# POS TECH — Data Analytics · Tech Challenges

**Autor:** Leonardo Fernandes Sbardelotto  
**Curso:** Pós-Graduação em Data Analytics — FIAP / POS TECH  
**Período:** 2024 – 2025

Repositório com as entregas dos quatro Tech Challenges do curso de pós-graduação em Data Analytics. Cada fase cobriu um tema distinto, acumulando as disciplinas da etapa e exigindo uma entrega prática completa.

---

## Visão Geral das Fases

| Fase | Tema | Ferramentas Principais | Resultado |
|------|------|------------------------|-----------|
| [Fase 1](#fase-1--análise-de-exportações-de-vinho-brasileiro) | Exportações de vinho brasileiro | Python · Pandas · Plotly | Análise exploratória + gráficos para investidores |
| [Fase 2](#fase-2--modelo-preditivo-ibovespa) | Previsão do IBOVESPA | Python · Scikit-learn · Google Colab | Classificador de tendência com acurácia >75% |
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
- Análise produzida em **manuscrito PDF** + **Power BI** + **Google Colab** (notebook Python/Pandas)
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
Fase 1/
├── Entrega/
│   ├── relatorio_vinhos_fase1.html                    # Relatório interativo HTML (principal)
│   └── Leonardo Fernandes Sbardelotto rm368591.pdf   # Relatório original PDF (21 págs.)
└── Tech Challenge Fase 1/
    ├── POSTECH - Tech Challenge - Fase 1.pdf          # Enunciado
    └── Base de dados.zip                               # Dados brutos Embrapa
```

**Como visualizar:** Abra `Fase 1/Entrega/relatorio_vinhos_fase1.html` diretamente no navegador — sem dependências, sem servidor.

---

## Fase 2 — Modelo Preditivo IBOVESPA

**Contexto:** Integrado a uma equipe de cientistas de dados de um fundo de investimentos, o desafio foi criar um modelo de Machine Learning capaz de prever se o índice IBOVESPA fecharia em **alta ou baixa** no dia seguinte.

**O que foi feito:**
- Coleta de dados históricos diários do IBOVESPA (mínimo 2 anos)
- Feature engineering: variações percentuais, médias móveis, features lagged
- Treinamento e avaliação de modelo de classificação binária
- Resultado: acurácia superior a 75% no conjunto de teste (últimos 30 dias)
- Apresentação em PDF com storytelling técnico + vídeo de 5 minutos com visão gerencial

**Resultados Reais do Modelo:**

| Modelo | Acurácia Teste | Cross-Val (5-fold) |
|--------|:--------------:|:------------------:|
| Logistic Regression | 43,3% | 51,3% |
| Random Forest | 43,3% | 51,7% |
| Extra Trees | 43,3% | 52,1% |
| **HistGradientBoosting (Final)** | **60,0%** | 50,3% |

> **Nota:** Baseline ingênuo (sempre prever "Alta") = 66,7%. Prever tendência de mercado é intrinsecamente difícil — o modelo captura padrões reais, mas dados macro/sentimento seriam necessários para superar o critério de 75%.

**Estrutura da entrega:**
```
Fase 2/
└── Entrega/
    └── TechChallenge_IBOV_Colab_Leonardo_Sbardelotto/
        ├── relatorio_ibovespa_fase2.html                          # Relatório interativo HTML (principal)
        ├── TechChallenge_IBOV_Colab_Leonardo_Sbardelotto.ipynb   # Notebook principal
        └── Machine Learning Fase 2 - Leonardo Sbardelotto.pdf    # Apresentação storytelling
```

**Como visualizar:** Abra `Fase 2/Entrega/TechChallenge_IBOV_Colab_Leonardo_Sbardelotto/relatorio_ibovespa_fase2.html` diretamente no navegador.

---

## Fase 3 — Análise PNAD COVID-19

**Contexto:** Contratado como Expert em Data Analytics por um grande hospital, o objetivo foi entender o comportamento da população durante a pandemia de COVID-19 usando os dados do PNAD-COVID-19 do IBGE, para subsidiar o planejamento hospitalar em caso de novo surto.

**O que foi feito:**
- Seleção de 20 variáveis-chave da pesquisa PNAD-COVID-19
- Organização da base em banco de dados em nuvem (BigQuery)
- Análise de 3 dimensões: sintomas clínicos · comportamento da população · características econômicas
- Identificação de indicadores-chave para planejamento hospitalar
- Entrega como relatório analítico interativo em HTML

**Estrutura da entrega:**
```
Fase 3/
└── Entrega/
    └── relatorio_pnad_covid19.html   # Relatório analítico interativo
```

---

## Fase 4 — Sistema Preditivo de Obesidade

**Contexto:** Como cientista de dados de um hospital, o desafio foi desenvolver um modelo de Machine Learning para auxiliar médicos a diagnosticar o nível de obesidade de pacientes com base em hábitos alimentares, histórico familiar e estilo de vida.

**O que foi feito:**
- Pipeline completo de ML: limpeza → feature engineering → treinamento → avaliação
- Feature derivada **BMI (IMC)** criada a partir de Peso e Altura — principal preditor (51,8% de importância)
- Comparação de 3 modelos: Logistic Regression · Random Forest · **XGBoost (selecionado)**
- Acurácia final: **98,1%** no conjunto de teste (critério: >75%)
- Aplicação preditiva interativa deployada no Streamlit
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
Fase 4/
└── Entrega/
    └── streamlit obsesity/
        ├── relatorio_obesidade_fase4.html   # Relatório analítico interativo (principal)
        ├── dashboard_obesidade.html          # Painel analítico (versão anterior)
        ├── pipeline_ml.py                    # Pipeline completo de ML
        ├── app_streamlit.py                  # Aplicação preditiva (Streamlit)
        ├── clinical_helpers.py               # Helpers clínicos (CPF, plano clínico)
        ├── model_xgb.pkl                     # Modelo treinado
        ├── model_meta.json                   # Metadados do modelo
        ├── Dados Obesity.csv                 # Dataset
        └── requirements.txt                  # Dependências
```

**Como visualizar:** Abra `Fase 4/Entrega/streamlit obsesity/relatorio_obesidade_fase4.html` diretamente no navegador.

**Como executar:**
```bash
pip install -r requirements.txt
python pipeline_ml.py          # Treina o modelo e gera model_xgb.pkl
streamlit run app_streamlit.py # Sobe a aplicação preditiva
```

---

## Stack Tecnológica

| Área | Ferramentas |
|------|-------------|
| Linguagem | Python 3.x |
| Análise de dados | Pandas · NumPy |
| Machine Learning | Scikit-learn · XGBoost |
| Visualização | Plotly · Matplotlib · Seaborn |
| Aplicação web | Streamlit |
| Banco de dados | BigQuery (Google Cloud) |
| Notebooks | Google Colab · Jupyter |

---

*POS TECH Data Analytics · FIAP · 2024–2025*
