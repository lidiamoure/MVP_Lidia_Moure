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
- Foram selecionados **5 arquivos CSV**, correspondentes às **waves 3, 4, 5, 6 e 7** da *World Values Survey (WVS)*.
- As **waves 1 e 2** não foram utilizadas devido:
  - ao

## Tecnologias Utilizadas

* **Databricks** (Notebooks)
* **Apache Spark (SQL / PySpark)**
* **Delta Lake**
* **GitHub** (versionamento)
* **Dashboards Databricks**

---
