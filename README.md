# niteroi-acidentes

> Análise geoespacial de acidentes de trânsito na região de Niterói/RJ usando dados públicos da PRF, com visualização interativa em mapas e modelo preditivo de gravidade.

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Folium](https://img.shields.io/badge/Folium-77B829?style=flat-square&logo=leaflet&logoColor=white)](https://python-visualization.github.io/folium/)
[![GeoPandas](https://img.shields.io/badge/GeoPandas-139C5A?style=flat-square)](https://geopandas.org/)

---

## Sobre o projeto

Este projeto analisa dados abertos de acidentes registrados pela Polícia Rodoviária Federal (PRF) nos municípios de Niterói, São Gonçalo, Itaboraí e Rio Bonito entre 2020 e 2026. O objetivo é identificar padrões temporais, mapear pontos críticos com inteligência geográfica e construir um classificador de gravidade de acidentes — replicando o tipo de trabalho realizado pelo Escritório de Dados e SIGeo da Prefeitura de Niterói.

---

## Resultados

| Métrica | Resultado |
|---|---|
| Registros analisados | 4.320 (2020–2026) |
| Horário de maior risco | 7h (pico matinal) |
| Dia mais crítico | Terça-feira |
| Causa mais comum | Ausência de reação do condutor |
| Acidentes fatais | 4,3% do total (187 ocorrências) |
| Município mais crítico | São Gonçalo — 1.592 acidentes, 72 fatais |
| Hotspot principal | Lat -22.880 / Lon -43.110 (79 acidentes) |
| Acurácia — Random Forest | 73,6% (cross-val: 75,7% ± 2,2%) |
| Feature mais preditiva | Tipo de acidente |

---

## Estrutura

```
niteroi-acidentes/
├── data/
│   ├── raw/               # Dados brutos da PRF (não versionados)
│   └── processed/         # Dataset limpo e filtrado
├── notebooks/
│   ├── 01_coleta_e_limpeza.ipynb       # Ingestão e pré-processamento
│   ├── 02_analise_exploratoria.ipynb   # EDA — padrões temporais e causas
│   ├── 03_analise_geoespacial.ipynb    # Mapas Folium + spatial join OSMnx
│   └── 04_modelo_ml.ipynb              # Classificador de gravidade
├── outputs/
│   ├── mapa_calor_niteroi.html         # Heatmap interativo
│   ├── mapa_pontos_acidentes.html      # Pontos por gravidade
│   ├── mapa_pontos_negros.html         # Somente acidentes fatais
│   └── mapa_hotspots.html              # Top 15 pontos críticos
├── requirements.txt
└── README.md
```

---

## Tecnologias utilizadas

| Ferramenta | Uso |
|---|---|
| `pandas` / `numpy` | Limpeza e manipulação dos dados |
| `matplotlib` / `seaborn` | Visualização estatística |
| `folium` | Mapas interativos georreferenciados |
| `geopandas` / `osmnx` | Dados espaciais e spatial join por município |
| `scikit-learn` | Random Forest e Regressão Logística |
| `jupyter` | Ambiente de análise |

---

## Como executar

### 1. Clone o repositório
```bash
git clone https://github.com/Gurkan22/niteroi-acidentes.git
cd niteroi-acidentes
```

### 2. Crie o ambiente e instale as dependências
```bash
conda create -n niteroi python=3.11 -y
conda activate niteroi
pip install -r requirements.txt
pip install osmnx
```

### 3. Baixe os dados
Acesse [dados abertos da PRF](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf) e baixe os CSVs de acidentes por ocorrência. Salve em `data/raw/` com o padrão `acidentes_YYYY.csv`.

### 4. Execute os notebooks em ordem
```bash
jupyter notebook
```

> Selecione o kernel **Python (niteroi)** antes de rodar cada notebook.

---

## Fonte dos dados

- **PRF — Polícia Rodoviária Federal**: [gov.br/prf](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf)
- Dados públicos sob licença aberta. Recorte: Niterói e região metropolitana, 2020–2026.

---

## Autor

Desenvolvido como projeto de portfólio — Pedro Lucas Almeida dos Santos — Ciência da Computação, UFF.
