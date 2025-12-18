# Análise do aumento percentual de jovens da Geração Z praticantes do catolicismo

## Resumo

Muito tem se comentado a respeito do retorno dos jovens da geração z ao catolicismo, bem como de sua maior aderência a valores conservadores num geral. O objetivo deste estudo é verificar a vercidade destas hipóteses. Para este fim, foi desenvolvida uma pipeline de dados no Databricks, utilizando notebooks, tabelas Delta Lake e um dashboard para ingestão, tratamento, modelagem e visualização de dados.

Os dados analisados foram coletados no banco de dados da World Values Survey (WVS), projeto de pesquisa global que estuda os valores e crenças socioculturais, políticos, econômicos e religiosos das pessoas em todo o mundo. Todo o processo de carga, limpeza e padronização, criação do modelo e análise e vizualização dos dados está registrado de forma objetiva e completa ao longo de 8 notebooks e um dashboard no DataBricks.


## Estrutura do Projeto

```
├── notebooks/
│   ├── 1 - Carregamento dos arquivos
│   ├── 2 - Limpeza e padronização dos dados - Parte 1   ## Seleção das colunas úteis para a composição do modelo.
│   ├── 3 - Limpeza e padronização dos dados - Parte 2   ## Reestruturação dos valores numéricos das instâncias para texto. 
│   ├── 4 - Limpeza e padronização dos dados - Parte 3   ## União das tabelas padronizadas em uma única tabela fato.
│   ├── 5 - Criação do modelo
│   ├── 6 - Análise - Parte 1              ## Análise do crescimento percentual do catolicismo.
│   ├── 7 - Análise - Parte 2              ## Análise dos valores conservadores dos jovens ao longo do tempo.
│   └──  8 - Análise - Parte 3 (Dashboard)  ## Análise dos valores conservadores dos jovens ao longo do tempo, com ênfase nos países com maior crescimento percentual de católicos. 
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
* 
  Foram selecionados 5 arquivos csv, correspondentes as waves 3, 4, 5, 6 e 7 da WVS. As waves 1 e 2 não foram selecionadas devido ao número limitado de países inclusos nestas e à falta de correspondência entre as perguntas feitas nos outros ciclos.
### Transformação dos dados
* 
  #### Notebook 1 - Carregamento dos dados:
  *
  Os **arquivos csv** foram carregados no **schema staging**. 
*  
  #### Notebook 2 - Limpeza e padronização dos dados - Parte 1: 
  *
  Os arquivos csv foram **transformados em tabelas**  e dispostos ** schema bronze**, utilizando a linguagem python. 
 * 
  #### Notebook 3 - Limpeza e padronização dos dados - Parte 2: 
*  
  Foram **selecionadas as colunas pertinentes** ao estudo - **atributos de identificação** do entrevistado (país, idade, sexo), perguntas sobre **valores religiosos** (frequência com que vai à igreja, importância da religião na vida do entrevistado) e sobre **valores conservadores** num geral (opinião sobre aborto, eutanásia, papel da mulher na sociedade, homosexualidade e divórcio). Após isto, as **colunas foram renomeadas**, de acordo com os arquivos .pdf de correspondência de códigos disponibilizados no site da WVS.
*
Por fim, foram substituidas as instâncias da coluna "religion_major_group" por valores em texto correspondentes, de acordo com os arquivos .pdf de correspondência de códigos disponibilizados no site da WVS.
*
Foi utilizada a linguagem SQL.  

 #### Notebook 4 - Limpeza e padronização dos dados - Parte 3: 
*
Foram unidas as 5 tabelas criadas em uma só. 
*
Foram substituídos os valores numéricos das instâncias remanescentes por valores em texto correspondentes, de acordo com os arquivos .pdf de correspondência de códigos disponibilizados no site da WVS. A tabela foi disposta no **schema silver**
*
Foram utilizadas as linguagens SQL e Spark SQL.


 #### Notebook 5 - Criação do modelo: 
 *
 Criação da **tabela fato e das tabelas dimensão**. Disposição destas no **schema gold**.

## Tecnologias Utilizadas

* **Databricks** (Notebooks)
* **Apache Spark (SQL / PySpark)**
* **Delta Lake**
* **GitHub** (versionamento)
* **Dashboards Databricks**

---
