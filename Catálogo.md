## 📊 Catálogo de Dados

## Tabela: fact_wave_all
- Camada: Gold
- Descrição: Tabela fato com dados consolidados da pesquisa WVS.



| Coluna                     | Tipo   | Descrição |
|---------------------------|--------|-----------|
| country_code              | int    | Código do país do entrevistado. |
| year_survey               | int    | Ano em que a pesquisa foi aplicada. |
| age                       | int    | Idade da pessoa entrevistada. |
| wave_chronology           | int    | Número da wave (onda) da pesquisa. |
| religion_major_group      | string | Religião declarada pelo entrevistado. |
| sex                       | string | Sexo da pessoa entrevistada. |
| important_religion        | string | Grau de importância da religião na vida do entrevistado. |
| men_better_leaders        | string | Opinião sobre se homens são melhores líderes políticos que mulheres. |
| child_religious_faith     | string | Qualidade a ser incentivada nas crianças: fé religiosa. |
| housewife_fulfilling      | string | Opinião se ser dona de casa é tão gratificante quanto trabalhar fora. |
| attendance_services       | string | Frequência de participação em cultos religiosos. |
| religious_person          | string | Autodeclaração como pessoa religiosa. |
| importance_god            | string | Grau de importância de Deus na vida do entrevistado. |
| university_more_for_boys  | string | Opinião se a universidade é mais importante para meninos do que para meninas. |
| men_priority_jobs         | string | Opinião se homens devem ter prioridade em empregos em caso de escassez. |
| neighbors_homosexuals     | string | Rejeição a homossexuais como vizinhos. |
| confidence_churches       | string | Grau de confiança nas igrejas como instituição. |
| justifiable_homosexuality | string | Grau de justificabilidade da homossexualidade (escala de 0 a 10). |
| justifiable_abortion      | string | Grau de justificabilidade do aborto (escala de 0 a 10). |
| justifiable_divorce       | string | Grau de justificabilidade do divórcio (escala de 0 a 10). |
| justifiable_euthanasia    | string | Grau de justificabilidade da eutanásia (escala de 0 a 10). |
| justifiable_prostitution  | string | Grau de justificabilidade da prostituição (escala de 0 a 10). |


## Tabela: dim_country

- Camada: Gold
- Descrição: Tabela dimensão com dados consolidados da pesquisa WVS.

| Coluna                     | Tipo   | Descrição |
|---------------------------|--------|-----------|
| country_code              | int    | Código do país do entrevistado. |
| country                   | string | Nome do país |


## Tabela: dim_age

- Camada: Gold
- Descrição: Tabela dimensão com dados consolidados da pesquisa WVS.

| Coluna                     | Tipo   | Descrição |
|---------------------------|--------|-----------|
| age                       | int    | Idade do entrevistado. |
| age_range                 | string | Intervalo em que a idade do entrevistado está: 15 - 25 anos; > 25 anos; idade não informada|

## Tabela: dim_age_range

- Camada: Gold
- Descrição: Tabela dimensão com dados consolidados da pesquisa WVS.

| Coluna                     | Tipo   | Descrição |
|---------------------------|--------|-----------|
| age_range                 | string | Intervalo em que a idade do entrevistado está: 15 - 25 anos; > 25 anos; idade não informada|


## Tabela: dim_wave

- Camada: Gold
- Descrição: Tabela dimensão com dados consolidados da pesquisa WVS.
  
| Coluna                     | Tipo   | Descrição |
|---------------------------|--------|-----------|
| Wave                      | int    | Número identificador do ciclo da pesquisa |
