# Análise do aumento percentual de jovens da Geração Z praticantes do catolicismo

## Introdução

Muito tem se discutido sobre o crescimento percentual de jovens da geração z praticantes do catolicismo, bem como de sua maior aderência a valores conservadores num geral. O objetivo deste estudo é verificar a vercidade destas hipóteses. Para este fim, foi desenvolvida uma pipeline de dados no Databricks, utilizando notebooks, tabelas Delta Lake para ingestão, tratamento, modelagem e visualização de dados.

Os dados analisados foram coletados no banco de dados da *_World Values Survey_* (WVS), projeto de pesquisa global que estuda os valores e crenças socioculturais, políticos, econômicos e religiosos das pessoas em todo o mundo. Todo o processo de carga, limpeza e padronização, criação do modelo e análise e vizualização dos dados está registrado de forma objetiva e completa ao longo de 7 notebooks no DataBricks.

Os ciclos de pesquisa do WVS são classificados em "Waves". A Wave mais recente, Wave 7, é datada de 2017 a 2022. Neste período, os jovens da geração z tinham de 15 a 25 anos de idade. Por conta disso, as análises foram feitas considerando os entrevistados desta **faixa etária** em cada Wave. 

## Estrutura do Projeto

```
├── notebooks/
│   ├── 0 - Preparação     ## Cria schemas, volumes e catálogos necessários para desenvolvimento da pipeline.
│   │           
│   ├── 1 - Carregamento dos arquivos  ## Carrega os arquivos utilizados no esquema staging
│   │ 
│   ├── 2 - Limpeza e padronização dos dados - Parte 1   ## Seleção das colunas úteis para a composição do modelo.
│   │ 
│   ├── 3 - Limpeza e padronização dos dados - Parte 2   ## Reestruturação dos valores numéricos das instâncias para texto.
│   │ 
│   ├── 4 - Limpeza e padronização dos dados - Parte 3   ## União das tabelas padronizadas em uma única tabela fato.
│   │ 
│   ├── 5 - Criação do modelo              ## Criação das tabelas fato e dimensão que compõe o modelo.
│   │ 
│   ├── 6 - Análise - Parte 1              ## Análise do crescimento percentual do catolicismo.
│   │ 
│   └── 7 - Análise - Parte 2              ## Análise dos valores conservadores ao longo do tempo.
│ 
│
├── Arquivos usados para preparação de dados/       ## Estes arquivos estão disponíveis no site da WVS
│   └── Variaveis_e_equivalências.xlsx    ## Este arquivo mostra a equivalência entre os códigos dos nomes das colunas do modelo e seus respectivos significados.
│   └── Code_Notebook/                    ## Esta pasta armazena 5 arquivos pdf (um para cada wave) que mostram a equivalência entre os códigos das instâncias de cada coluna do modelo e seus respectivos significados.
│
│
├── Modelo relacional
│   └── Modelo.pdf       ## Diagrama do modelo relacional criado
│
├── Evidência das análises/
│   ├── Evidências_Análises_Parte1.pdf    ## Evidencia as análises feitas no notebook "6 - Análise - Parte 1"
│   ├── Evidências_Análises_Parte1.pdf    ## Evidencia as análises feitas no notebook "7 - Análise - Parte 2"
│
├── Catálogo.md
├── Referências.md
├── Auto_avaliacao.md
└── README.md
```

---
---

## Objetivos

* Verificar a **variação percentual** de jovens católicos ao longo do tempo.
* Verificar a **variação percentual** de jovens católicos em relação ao montante "católicos + Protestantes" ao longo do tempo.
* **Ranquear os países** com maior variação percentual.
* Correlacionar os resultados encontrados à aderência a valores conservadores.

## Qualidade dos dados

- A base de dados escolhida não apresentou problemas de qualidade _per se_. Os arquivos CSV tinham delimitadores claros, com atomicidade presente e não foram encontradas duplicidade ou inconsistências.
- Contudo, tanto o nome das colunas quanto as instâncias delas são originalmente preenchidas com siglas (string) e números (INT). Para possibilitar a análise dos dados, foi feita a substituição destas siglas e números pelos dados correspondentes. Estes, são disponibilizados nos arquivos de correspondência e code notebooks no site da WVS. Estes arquivos também estão disponíveis na seguinte pasta deste repositório: "Arquivos utilizados para preparação de dados".
- A limpeza e padronização dos dados foi feita ao longo de três notebooks no Databricks. Foram utilizadas as linguagens SQL e Python.
  
## Descrição do modelo criado

Foi criado um modelo tipo **_Snow Flake_** com uma tabela dimensão e quatro tabelas fatos.

### Tabela fato

* **fact_wave_all**: Reúne as informações de identificação dos entrevistados (país, sexo, faixa etária), as respostas das perguntas feitas e a ciclo de pesquisa em questão.

### Tabelas dimensão

* **dim_country**: Reúne o nome dos países e seu código correspondente.

* **dim_age**: Reúne os valores distintos das idades dos entrevistados ao longo das waves e a faixa etária correspondente a cada idade. 

* **dim_age_range**: Reúne os valores distintos das faixas etárias. 

* **dim_wave**: Reúne os valores distintos que identificam cada Wave. 








## ETL

### Extração dos dados
- Foram selecionados **5 arquivos CSV**, correspondentes às **waves 3, 4, 5, 6 e 7** da *World Values Survey (WVS)*.
- As **waves 1 e 2** não foram utilizadas devido:
  - ao **número limitado de países** incluídos;
  - à **falta de correspondência entre as perguntas** realizadas nos ciclos posteriores.

### Transformação dos dados

#### Notebook 1 – Carregamento dos dados
- Os **arquivos CSV** foram carregados no **schema `staging`**.

#### Notebook 2 – Limpeza e padronização dos dados (Parte 1)
- Os arquivos CSV foram **transformados em tabelas** e dispostos no **schema `bronze`**.
- Linguagem utilizada: **Python**.

#### Notebook 3 – Limpeza e padronização dos dados (Parte 2)
- Foram **selecionadas as colunas pertinentes ao estudo**, incluindo:
  - **Atributos de identificação** do entrevistado (país, idade e sexo);
  - Perguntas sobre **valores religiosos** (frequência de ida à igreja e importância da religião);
  - Perguntas sobre **valores conservadores**, como:
    - aborto;
    - eutanásia;
    - papel da mulher na sociedade;
    - homossexualidade;
    - divórcio.
- As **colunas foram renomeadas** conforme os arquivos **PDF de correspondência de códigos** disponibilizados no site da WVS.
- As instâncias da coluna **`religion_major_group`** foram substituídas por **valores textuais correspondentes**, com base nos mesmos arquivos.
- Linguagem utilizada: **SQL**.

#### Notebook 4 – Limpeza e padronização dos dados (Parte 3)
- As **5 tabelas** foram **unificadas em uma única tabela**.
- Os **valores numéricos remanescentes** foram substituídos por **valores textuais correspondentes**, conforme os arquivos de correspondência da WVS.
- A tabela final foi disposta no **schema `silver`**.
- Linguagens utilizadas: **SQL** e **Spark SQL**.

### Carregamento dos dados 

#### Notebook 5 – Criação do modelo
- Criação da **tabela fato** e das **tabelas dimensão**.
- As tabelas foram dispostas no **schema `gold`**.

## Análise dos dados

#### Notebook 6 – Análise dos dados (Parte 1)
- Cálculo da **variação percentual de católicos romanos** ao longo das waves.
- Cálculo da **variação percentual de católicos romanos** ao longo das waves, em comparação ao **montante de católicos + protestantes**.
- Identificação dos **países com maior crescimento percentual de católicos romanos**, tanto em termos absolutos quanto **em relação aos protestantes**.

#### Notebook 7 – Análise dos dados (Parte 2)
- Análise dos **valores conservadores nos países com maior crescimento recente do catolicismo** em relação às outras religiões declaradas e em relação ao montante "católicos + protestantes".


## Tecnologias Utilizadas

* **Databricks** (Notebooks)
* **Apache Spark (SQL / PySpark)**
* **Delta Lake**
* **GitHub** (versionamento)
* **dbdiagram.io** (criação do arquivo PDF do modelo)

---
## Como executar:

1. Clonar esse repositório no databricks
2. Executar o notebook "0 - Preparação"
3. Baixar os arquivos deste link: https://drive.google.com/drive/folders/1uCnXJ8QNg-JwJIq6bFxo5jfSmprNFkmC?usp=drive_link e carregá-los no seguinte caminho do databricks: "mvp_wvs.staging.wvs"
4. Seguir com a execução dos demais notebooks.
