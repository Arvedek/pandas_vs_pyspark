# pandas_vs_pyspark

keep updating ....

|  | Pandas | Spark |
| :---: | :---: | :---: |DF
| How it works | Single Machine | Distributed computing framework |
| Transformation mechanism | not lazy evaluation | lazy evaluation |
| cache | | df.cache(), df.persist() |
| Insert row| Yes | NO (RDD based) |
| Create | read csv/excel, list/dict/ndarray | read csv, RDD |
|        | From spark df : pd_df = spark_df.toPandas() | From pd df ： spark df = spark.createDataFrame(pd_df) |
| index | index automatically created by default | no defualt index |
| Row structure| pd.Series pandas_dataframe | spark.sql.Row  spark_dataframe|
| Column structure| pd.Series pandas_dataframe | spark.sql.Column  spark_dataframe|
| Column Name | Duplicate name not allowed | Duplicate name allowed |
| Change Col Name| rename()| alias() |
| Add Col | df['new'] = 0 | df.withColumn('new',F.lit(0)) |  
| Change Col | df['new'] = 1 | df.withColumn('new',1) |
| View table | df | df.show() |
| Sort | df.sort() , df.sort_values(by = ['c1','c2']) | df.sort('c1','c2') |
| Slice | df.new, df['new'] | df['new'], df.select('new') |
| | df [0] | df.first() |
| | df.head(5) | df.head(5), df.take(5) |
| | df.loc(), df.iloc() | |
| filter | df[df['new']>=1] | df.filter(df['new']>=1) , df.where(F.col('new')>=1) |
| groupby | df.groupby('A').avg('B') | df.groupBy('A').avg('B'), df.groupBy('A').agg(F.avg('B')) |
| stats | df.describe() | df.describe() |
| shape | df.shape | df.count , len(df.columns) |
| concat | pd.concat(),pd.merge(), df.join() , df,append() | df,join() |
| missing | df.fillna() , df.dropna(), autofill NaNs | df.na.fill() , df.na.drop() ,no autofill NaNs|
| SQL | pd.read_sql(“SELECT .. FROM .. WHERE ..″) | df.registerTempTable(“TABLE”) <br /> sqlContext.sql(“SELECT .. FROM TABLE WHERE ..″) |
| apply function | pd.apply(func) | df.foreach(func) , df.rdd.foreach(func) |
| map reduce | map(func,list) , reduce(func, list) <br /> return seq|  df.map(func)，df.reduce(func) <br /> return seqRDDs |
| diff |  df.diff() |  |
