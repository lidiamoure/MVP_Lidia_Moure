## Sobre os objetivos atingidos

Todas as perguntas feitas no presente estudo foram respondidas, conforme as evidências das análises descrevem. 

* Não se evidenciou crescimento percentual de católicos romanos ao longo das waves analisadas, apenas crescimento percentual recente (entre as waves 6 e 7).

* Não se evidenciou crescimento percentual de católicos romanos em relação ao montante "católicos romanos + protestantes"  ao longo das waves analisadas, apenas crescimento percentual recente (entre as waves 6 e 7).
Por conta destes resultados, foi feita a análise dos valores conservadores em relação a dois grupos: 

  * **Grupo 1**: 10 países que apresentaram maior crescimento percentual recente de católicos romanos em relação às outras religiões declaradas. 
  * **Grupo 2**: 10 países que apresentaram maior crescimento percentual recente de católicos romanos em relação ao montante "católicos romanos + protestantes".

* Nos dois grupos, não foi observada aderência expressiva aos valores conservadores analisados. Contudo, o Grupo 1 apresentou maior identificação com valores conservadores do que o Grupo 2.

## Dificuldades encontradas

### De modo geral

Por se tratar da primeira pipeline de dados desenvolvida pela autora, as dificuldades encontradas, em suma, residem na baixa familiaridade com as ferramentas e plataformas utilizadas. 

### Em relação à plataforma DataBricks

Foi dedicado bastante tempo ao processo de compreender a interface e funcionamento das tecnologias da plataforma Databricks, antes de iniciar a criação da pipeline em questão.

Encontrou-se dificuldade no processo de baixar e carregar os arquivos de _raw data_ no databricks através de comandos feitos nas células do notebook. Desse modo, foi necessário fazer o carregamento dos arquivos manualmente antes de realizar as análises. Reciprocamente, para possibilitar a execução da pipeline por terceiros, foi orientado o carregamento manual dos arquivos previamente disponibilizados num link. 

Foram realizados vários testes, em diferentes contas da plataforma Databricks, da execução da pipeline de dados criada. Neste processo, encontrou-se dificuldades na integração do GitHub com o Databricks. 

### Em relação aos dados brutos analisados

Foi decidido não incluir as Waves 1 e 2 nesta pipeline, devido quantidade de países participantes (poucos países) e a baixa equivalência entre as perguntas feitas nessas waves em relação às posteriores. 

Por mais que as Waves de 3 a 7 tenham sido escolhidas, há entre estas diferenças quanto ao grupo de países entrevistados e quanto às equivalências das perguntas feitas em cada ciclo. Para isso, foi necessário fazer uma seleção das perguntas presentes nas 5 waves que contemplassem os valores conservadores a serem analisados. Este processo requereu tempo e atenção aos detalhes conforme se consultava simultaneamente os arquivos utilizados para preparação de dados.

Tanto os atributos quanto as instâncias dos dados disponibilizados no WVS são originalmente preenchidos por números (INT) e siglas (strings). Para entender o significado de cada termo, faz-se necessário consultar documentos que mostram as equivalências (Estes documentos foram baixados do site da WVS e estão na pasta "Arquivos utilizados para preparação de dados" neste repositório do github). 

Tendo em vista estas circunstâncias, o processo de padronização dos dados foi moroso e requereu muita atenção aos detalhes.  


## Ideias para trabalhos futuros

* Utilizar os dados da Wave 8 do WVS, cuja liberação está prevista para dezembro de 2026. Uma vez que espera-se, conforme os resultados das análises indicam, que haja maior crescimento percentual de jovens da geração z praticantes do catolicismo. 

* Criar um _dashboard_ para ilustrar os resultados encontrados. Neste, estará presente um gráfico de mapa que indique através de um gradiente de cores a variação percentual do catolicismo por região. Cores mais quentes: variação maior. Cores mais frias: variação menor. 

* Fazer a análise da aderência a valores conservadores por países. Através da seleção dos 5 países em que houve maior crescimento percentual de católicos romanos dentre jovens da geração z. 

* Comparar, também, a aderência a valores conservadores de grupos amostrais de outras faixas etárias. 


