# Análise do aumento percentual de jovens da Geração Z praticantes do catolicismo

## Resumo

Muito tem se comentado a respeito do retorno dos jovens da geração z ao catolicismo, bem como de sua maior aderência a valores conservadores num geral. O objetivo deste estudo é verificar a vercidade destas hipóteses. Para este fim, foi desenvolvida uma pipeline de dados no Databricks, utilizando notebooks, tabelas Delta Lake e um dashboard para ingestão, tratamento, modelagem e visualização de dados.

Os dados analisados foram coletados no banco de dados da World Values Survey (WVS), projeto de pesquisa global que estuda os valores e crenças socioculturais, políticos, econômicos e religiosos das pessoas em todo o mundo. Todo o processo de carga, limpeza e padronização, criação do modelo e análise e vizualização dos dados está registrado de forma objetiva e completa ao longo de 8 notebooks e um dashboard no DataBricks.



---

## Tecnologias Utilizadas

* **Databricks** (Notebooks)
* **Apache Spark (SQL / PySpark)**
* **Delta Lake**
* **GitHub** (versionamento)
* **Dashboards Databricks**

---

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

## Descrição da Pipeline

### 1. Camada Bronze – Ingestão de Dados

Responsável por receber os dados em seu formato original.

Principais características:

* Dados brutos (raw)
* Sem grandes transformações
* Persistência em tabelas Delta

Exemplos de operações:

* Leitura de arquivos externos
* Padronização mínima de colunas

---

### 2. Camada Silver – Tratamento e Limpeza

Nesta etapa ocorre o tratamento dos dados.

Principais atividades:

* Limpeza de valores inválidos (NULL, NaN, códigos especiais)
* Padronização de tipos de dados
* Criação de colunas derivadas
* Normalização de categorias

Objetivo: garantir **consistência e qualidade dos dados**.

---

### 3. Camada Gold – Modelagem Analítica

Camada voltada para consumo analítico.

Características:

* Criação de **tabelas fato e dimensões**
* Aplicação de **esquema estrela**
* Dados prontos para análises e dashboards

Exemplos:

* Tabelas dimensão (ex: sexo, idade, país, religião)
* Tabelas fato com métricas consolidadas

---

## Dashboards

Os dashboards foram criados diretamente no Databricks a partir das tabelas da camada Gold.

Eles permitem:

* Visualização interativa dos dados
* Análise de indicadores-chave
* Exploração por filtros (ex: país, período, categoria)

---

## Versionamento e Reprodutibilidade

* Os notebooks foram exportados e versionados neste repositório
* Toda a lógica de transformação está documentada em código
* A pipeline pode ser reproduzida executando os notebooks na ordem:

1. Bronze
2. Silver
3. Gold
4. Dashboards

---

## Como Executar

1. Importar os notebooks no Databricks
2. Ajustar caminhos de leitura, se necessário
3. Executar os notebooks seguindo a ordem das camadas
4. Atualizar os dashboards

---

## Observações Finais

Este projeto demonstra a construção de uma pipeline de dados moderna utilizando Databricks e Delta Lake, com foco em boas práticas de engenharia de dados e organização analítica.

---

## Autor

Projeto desenvolvido por **[Seu Nome]**
