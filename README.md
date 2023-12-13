# Escolha o idioma / Choose the language
- [Português (BR)](README.md)
- [English](README_EN.md)

  
# Time Travel usando Pyspark

Viagem no tempo no contexto de rollback significa reverter um sistema de computador para um estado anterior, garantindo a integridade dos dados. Ao contrário de edições diretas, ele desfaz alterações retornando a um ponto anterior consistente, sendo valioso para lidar com operações falhas em bancos de dados.

## Code:

from delta.tables import *

deltaTable = DeltaTable.forPath(spark, "abfss://layer@tech.dfs.core.windows.net/sample/path/table)

latestHistory = deltaTable.history(); 

display(latestHistory)   

df_read = spark.read.format("delta").option("timestampAsOf", "2022-12-23 21:08:24.659").load("abfss://layer@tech.dfs.core.windows.net/sample/path/table)


## Informações:
### from delta.tables import *:
-- Importa as classes e métodos necessários da biblioteca delta.tables.

### deltaTable = DeltaTable.forPath(spark, "abfss://layer@tech.dfs.core.windows.net/exemplo/de/path/tabela")
-- Cria uma referência a uma Delta Table específica localizada no caminho fornecido. A variável deltaTable agora representa a Delta Table localizada no caminho especificado.

### latestHistory = deltaTable.history()
-- Recupera o histórico de operações realizadas na Delta Table. Isso inclui informações sobre as versões da tabela, as operações realizadas em cada versão e as datas associadas a essas operações. O resultado é armazenado na variável latestHistory.

### display(latestHistory)
-- Exibe o histórico obtido anteriormente. display é uma função usada para visualizar resultados em ambientes como o Databricks, por exemplo.

### df_read = spark.read.format("delta").option("timestampAsOf", "2022-12-23 21:08:24.659").load("abfss://layer@tech.dfs.core.windows.net/exemplo/de/path/tabela")
-- Lê dados da Delta Table em um DataFrame do Spark. A opção "timestampAsOf" especifica uma versão específica dos dados para ler, neste caso, a versão correspondente à data e hora fornecidas ("2022-12-23 21:08:24.659").

Em resumo, este código trabalha com Delta Tables no contexto do Apache Spark, permitindo acesso ao histórico da tabela e leitura de dados de uma versão específica com base em informações de carimbo de data e hora.
