## 📊 Catálogo de Dados

## Tabela: fact_wave_all
- Camada: Gold
- Descrição: Tabela fato com dados consolidados da pesquisa WVS.



## Tabela: fact_wave_all
- **Origem dos dados**: **World's Values Survey**
- **Camada:** Gold  
- **Descrição:** Tabela fato com dados da pesquisa World Values Survey, contendo informações demográficas e respostas relacionadas a religião, valores sociais e opiniões.
- **Domínio**: O domínio dos valores dos dados pode ser consultado nos code notebooks de cada wave, no seguinte diretório: Arquivos utilizados para preparação de dados/Code_Notebook

| Coluna | Tipo | Descrição |
|------|------|-----------|
| country_code | INT | Código do país |
| year_survey | INT | Ano em que a pesquisa foi aplicada |
| age | INT | Idade da pessoa entrevistada |
| wave_chronology | INT | Número da wave em questão |
| religion_major_group | STRING | Religião declarada |
| sex | STRING | Sexo da pessoa entrevistada |
| important_religion | STRING | Pergunta: O quão importante a religião é na sua vida? |
| men_better_leaders | STRING | Pergunta: De modo geral, homens são melhores líderes políticos que mulheres? |
| child_religious_faith | STRING | Enumerar qualidades que devem ser incentivadas às crianças em casa: Fé religiosa |
| housewife_fulfilling | STRING | Pergunta: Ser dona de casa é tão gratificante quanto trabalhar fora? |
| attendance_services | STRING | Pergunta: Com que frequência você vai a cultos religiosos? |
| religious_person | STRING | Pergunta: Você se considera uma pessoa religiosa? |
| importance_god | STRING | Pergunta: O quão importante é Deus em sua vida? |
| university_more_for_boys | STRING | Pergunta: Você concorda que ir à universidade é mais importante para um menino do que para uma menina? |
| men_priority_jobs | STRING | Pergunta: Em caso de escassez de empregos, homens devem ter prioridade em relação às mulheres? |
| neighbors_homosexuals | STRING | Lista: Mencione o tipo de pessoas que você não gostaria de ter como vizinho: \"Homosexuais\" |
| confidence_churches | STRING | Pergunta: Você confia nas igrejas como instituição? |
| justifiable_homosexuality | STRING | Pergunta: Numa escala de 0 a 10, em que 0 é \"Nunca justificável\" e 10 é \"Sempre justificável\", o quão justificável para você é a homossexualidade? |
| justifiable_abortion | STRING | Pergunta: Numa escala de 0 a 10, em que 0 é \"Nunca justificável\" e 10 é \"Sempre justificável\", o quão justificável para você é o aborto? |
| justifiable_divorce | STRING | Pergunta: Numa escala de 0 a 10, em que 0 é \"Nunca justificável\" e 10 é \"Sempre justificável\", o quão justificável para você é o divórcio? |
| justifiable_euthanasia | STRING | Pergunta: Numa escala de 0 a 10, em que 0 é \"Nunca justificável\" e 10 é \"Sempre justificável\", o quão justificável para você é a eutanásia? |
| justifiable_prostitution | STRING | Pergunta: Numa escala de 0 a 10, em que 0 é \"Nunca justificável\" e 10 é \"Sempre justificável\", o quão justificável para você é a prostituição? |


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
| Wave                      | int    | Número identificador do ciclo da pesquisa: 3, 4, 5, 6 ou 7 |

## View: v_countries_growth_catholicism

Camada: Gold

Descrição: View análitica que retorna os 10 países que apresentaram maior crescimento percentual de católicos romanos, cujos entrevistados tinham entre 15 e 25 anos no momento em que a pesquisa foi aplicada.

| Coluna                | Tipo   | Descrição                                                                                                                             |
| --------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| country               | string | Nome do país.                                                                                                                         |
| country_code          | int    | Código do país.                                                                                                                       |
| catholic_growth_slope | double | Inclinação da regressão linear indicando crescimento (valor positivo) ou declínio (valor negativo) do catolicismo ao longo das waves. |


## View: v_countries_growth_catholicism_pct_catholic_protestant_waves_6_to_7

Camada: Gold

Descrição: View análitica que retorna os 10 países que apresentaram maior crescimento percentual de católicos romanos entre as waves 6 e 7, cujos entrevistados tinham entre 15 e 25 anos no momento em que a pesquisa foi aplicada.

| Coluna       | Tipo   | Descrição                                                                                          |
| ------------ | ------ | -------------------------------------------------------------------------------------------------- |
| country      | string | Nome do país.                                                                                      |
| country_code | int    | Código do país.                                                                                    |
| trend_slope  | double | Inclinação da regressão linear indicando crescimento (valor positivo) ou declínio (valor negativo)  da proporção entre católicos e protestantes ao longo das waves analisadas. |
| n_waves      | int    | Quantidade de waves consideradas no cálculo da tendência.                                          |


## View: view_top_catholicprotestants

Camada: Gold

Descrição: View análitica que retorna os 10 países que apresentaram maior crescimento percentual de católicos romanos, em relação ao montante "católicos romanos + protestantes", entre as waves 6 e 7, cujos entrevistados tinham entre 15 e 25 anos no momento em que a pesquisa foi aplicada.

| Coluna  | Tipo   | Descrição     |
| ------- | ------ | ------------- |
| country | string | Nome do país. |
