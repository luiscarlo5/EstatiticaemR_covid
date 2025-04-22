# 📊 Análise Estatística da COVID-19 no Afeganistão (2020–2023)

Este projeto realiza uma análise estatística detalhada da evolução da COVID-19 no Afeganistão, utilizando dados oficiais sobre casos, mortes e vacinação entre 2020 e 2023. O objetivo é comparar ondas da pandemia em diferentes momentos, observando padrões e variações ao longo do tempo.

---

## 📁 Dados Utilizados

O conjunto de dados é um arquivo `.csv` contendo estatísticas globais da COVID-19. Para esta análise, foram selecionados exclusivamente os registros do Afeganistão.

**Fonte**: `[covid_dataset](https://www.kaggle.com/datasets/imdevskp/corona-virus-report?select=covid_19_clean_complete.csv)`

## 🔎 Preprocessamento
Embora o foco da análise tenha sido exclusivamente o país Afeganistão, existem outros países nos dados trabalhados, por isso é bom se atentar ao código fonte que realiza a separação e análise temporal dos dados com base nas colunas de interesse aqui trabalhadas.

### 📌 Variáveis de interesse:
- `date`: Data do registro
- `new_cases`: Novos casos diários
- `new_cases_smoothed`: Novos casos suavizados
- `new_vaccinations`: Novas vacinações diárias
- `new_vaccinations_smoothed`: Novas vacinações suavizadas
- `total_cases`: Casos acumulados
- `total_vaccinations`: Vacinações acumuladas
- `people_vaccinated`: Pessoas vacinadas
- `total_deaths`: Mortes acumuladas
- `new_deaths`: Novas mortes diárias
- `new_deaths_smoothed`: Novas mortes suavizadas

---

## 🔄 Etapas do Projeto

### 1. **Pré-processamento**
- Filtro dos dados para o Afeganistão
- Seleção das colunas relevantes
- Substituição de valores `NA` por `0`
- Conversão da coluna `date` para o tipo `Date`

### 2. **Segmentação Temporal**
- Análise anual (2020, 2021, 2022, 2023)
- Análise por ondas epidêmicas:
  - **1ª Onda**: 26/04/2020 a 26/09/2020
  - **3ª Onda**: 26/04/2021 a 26/09/2021

### 3. **Análises Estatísticas**
Para cada onda, foram calculados:
- Média e desvio padrão de:
  - Novos casos
  - Novas mortes
  - Novas vacinações

### 4. **Visualizações**
- Histogramas das distribuições de novos casos
- Gráficos de linha para:
  - Novos casos e mortes (originais e suavizados)
  - Comparações entre ondas

---

## 📉 Exemplos de Resultados

### 🦠 1ª Onda:
- **Novos Casos**: Média ≈ `x`, Desvio padrão ≈ `y`
- **Novas Mortes**: Média ≈ `x`, Desvio padrão ≈ `y`
- **Novas Vacinações**: Média ≈ `x`, Desvio padrão ≈ `y`

### 🦠 3ª Onda:
- **Novos Casos**: Média ≈ `x`, Desvio padrão ≈ `y`
- **Novas Mortes**: Média ≈ `x`, Desvio padrão ≈ `y`
- **Novas Vacinações**: Média ≈ `x`, Desvio padrão ≈ `y`

(*Valores substituídos automaticamente no console do R.*)

---

## ▶️ Como Executar

1. Instale o pacote necessário:
```r
install.packages("readxl")
```
2. Baixe o Arquivo "CodigoFonte" e o [dataset](https://www.kaggle.com/datasets/imdevskp/corona-virus-report?select=covid_19_clean_complete.csv) utilizado.
## 📊 Resultados

### 🦠 Identificação das Ondas Epidêmicas

Nos gráficos das Figuras 3, 4 e 5, observa-se uma maior frequência de casos entre os meses de **maio a setembro**, tanto em 2020 quanto em 2021. Por isso, foram selecionadas essas duas grandes ondas para análise.

### 📈 Relação entre Casos e Mortes

A análise confirmou o que é intuitivo: **à medida que o número de casos aumenta, o número de mortes também cresce**. Isso foi estatisticamente validado com a **correlação de Pearson**, resultando em:

> **r = 0,842** → alta correlação positiva entre casos e mortes.

### 📊 Estatísticas Descritivas

| Ano  | Média de Casos | Desvio Padrão (Casos) | Média de Mortes | Desvio Padrão (Mortes) |
|------|----------------|------------------------|------------------|-------------------------|
| 2020 | 143,76         | 205,66                 | 7,06             | 9,24                    |
| 2021 | 289,66         | 506,66                 | 14,15            | 24,34                   |
| 2022 | 135,60         | 143,07                 | 1,35             | 2,40                    |
| 2023 | 90,06          | 97,64                  | 0,42             | 0,81                    |

- **2021** teve os maiores índices de casos e mortes.
- Em **2022**, a média de casos foi próxima à de 2020, mas a média de mortes caiu consideravelmente.
- Em **2023**, observou-se a menor média de mortes desde o início da pandemia.

### 💉 Impacto da Vacinação

A vacinação teve papel central na queda do número de mortes:

| Ano  | Média de Doses Diárias |
|------|------------------------|
| 2020 | 0                      |
| 2021 | 18,83                  |
| 2022 | 186,53                 |
| 2023 | 19,39                  |

Em 2022, o maior número de vacinas administradas (68.085 doses) coincidiu com a maior queda nas mortes, reforçando o impacto positivo da vacinação, mesmo num país com desafios estruturais como o **Afeganistão**.

### 🧪 Testes de Hipóteses

Para validar estatisticamente a relação entre ondas de contágio e aumento nas mortes:

- **2020**:
  - Hipótese nula: média de mortes = 7,06
  - Amostra de 153 dias, média amostral: 9,16, desvio padrão: 11,12
  - Valor de t = **2,335** > 1,975 (t crítico a 5%)
  - ✅ Hipótese nula rejeitada

- **2021**:
  - Valor de t = **6,331** > 1,975
  - ✅ Hipótese nula novamente rejeitada

Esses resultados confirmam, com significância estatística, que **em grandes ondas de casos, o número de mortes também aumenta**.

### ✅ Conclusão

Este estudo permitiu demonstrar estatisticamente que:

- O aumento no número de casos está diretamente ligado ao aumento nas mortes;
- A vacinação tem efeito positivo comprovado na redução da mortalidade;
- Testes de hipóteses reforçam essas conclusões com base em dados reais;
- Mesmo em um país com diversas dificuldades, **a ciência e a vacinação mostraram sua eficácia**.

Todos os dados e análises foram processados com algoritmos em **R** desenvolvidos pelo autor.

