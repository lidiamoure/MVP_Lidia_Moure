# Pipeline de Dados no Databricks

## Visão Geral

Este repositório documenta uma **pipeline de dados desenvolvida no Databricks**, utilizando notebooks, tabelas Delta Lake e dashboards para ingestão, tratamento, modelagem e visualização de dados.

A pipeline segue uma arquitetura em camadas (**Bronze, Silver e Gold**), garantindo qualidade, rastreabilidade e escalabilidade dos dados.

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
│   ├── 2 - Limpeza e padronização dos dados - Parte 1
│   ├── 3 - Limpeza e padronização dos dados - Parte 2
│   ├── 4 - Limpeza e padronização dos dados - Parte 3
│   ├── 5 - Criação do modelo
│   ├── 6 - Análise - Parte 1
│   ├── 7 - Análise - Parte 2
│   ├── 8 - Análise - Parte 3 (Dashboard)
│   └── analysis
│
├── dashboards/
│   └── dashboard_analytics
│
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
