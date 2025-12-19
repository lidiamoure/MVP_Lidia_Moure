# Análise do aumento percentual de jovens da Geração Z praticantes do catolicismo

## Resumo

Muito tem se discutido a respeito do retorno dos jovens da geração z ao catolicismo, bem como de sua maior aderência a valores conservadores num geral. O objetivo deste estudo é verificar a vercidade destas hipóteses. Para este fim, foi desenvolvida uma pipeline de dados no Databricks, utilizando notebooks, tabelas Delta Lake para ingestão, tratamento, modelagem e visualização de dados.

Os dados analisados foram coletados no banco de dados da World Values Survey (WVS), projeto de pesquisa global que estuda os valores e crenças socioculturais, políticos, econômicos e religiosos das pessoas em todo o mundo. Todo o processo de carga, limpeza e padronização, criação do modelo e análise e vizualização dos dados está registrado de forma objetiva e completa ao longo de 7 notebooks no DataBricks.


## Estrutura do Projeto

```
├── notebooks/
│   ├── 1 - Carregamento dos arquivos
│   ├── 2 - Limpeza e padronização dos dados - Parte 1   ## Seleção das colunas úteis para a composição do modelo.
│   ├── 3 - Limpeza e padronização dos dados - Parte 2   ## Reestruturação dos valores numéricos das instâncias para texto. 
│   ├── 4 - Limpeza e padronização dos dados - Parte 3   ## União das tabelas padronizadas em uma única tabela fato.
│   ├── 5 - Criação do modelo              ## Criação das tabelas fato e dimensão que compõe o modelo.
│   ├── 6 - Análise - Parte 1              ## Análise do crescimento percentual do catolicismo.│  
│   └── 7 - Análise - Parte 2              ## Análise dos valores conservadores dos jovens ao longo do tempo.
│  
│
├── dashboards/
│   └── MVP_WVS
│
├── Catálogo.md
├── Referência.md
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

#### Notebook 5 – Criação do modelo
- Criação da **tabela fato** e das **tabelas dimensão**.
- As tabelas foram dispostas no **schema `gold`**.
- 
## Análise dos dados

#### Notebook 6 – Análise dos dados (Parte 1)
- Cálculo da **variação percentual de católicos romanos** ao longo das waves.
- Cálculo da **variação percentual de católicos romanos** ao longo das waves, em comparação ao **montante de católicos + protestantes**.
- Identificação dos **países com maior crescimento percentual de católicos romanos**, tanto em termos absolutos quanto **em relação aos protestantes**.

#### Notebook 7 – Análise dos dados (Parte 2)
- Cálculo do **percentual de aderência a valores conservadores** entre os entrevistados.

#### Notebook 8 – Análise dos dados (Parte 3)
- Análise dos **valores conservadores nos países com maior crescimento do catolicismo**.
- Comentários e interpretações baseados nos **insights apresentados no dashboard** criado no Databricks.




## Tecnologias Utilizadas

* **Databricks** (Notebooks)
* **Apache Spark (SQL / PySpark)**
* **Delta Lake**
* **GitHub** (versionamento)
* **Dashboards Databricks**

---
