---
title: files Parquet
---
Apache Parquet is a columnar, file-based storage format, originating in the Apache Hadoop ecosystem. It can be queried efficiently, is highly compressed, supports null values, and is non-spatial. It is supported by many Apache big data frameworks, such as Drill, Hive, and Spark.

Parquet is additionally supported by several large-scale query providers, such as Amazon AWS Athena, Google Cloud BigQuery, and Microsoft Azure Data Lake Analytics.


# [Home page DuckDB/Parquet](https://duckdb.org/docs/data/parquet)

## da csv a parquet

	import pandas as pd
	df = pd.read_csv('dati/progetti_esteso_2014-2020_20211231.csv', sep=';', error_bad_lines=False) #se ci sono errori
	pd.options.display.max_columns = None
	pd.options.display.max_rows = None
	df = df.astype(str) #se ci sono errori


## come leggere un parquet


## [Lettura di più file di parquet](https://duckdb.org/2021/06/25/querying-parquet.html)

## [Concatena in un unico file ](https://duckdb.org/2021/06/25/querying-parquet.html)


## query 
	lineitem = duckdb.query("SELECT * FROM 'lineitemsf1.snappy.parquet'").to_df()
	orders = duckdb.query("SELECT * FROM 'orders.parquet'").to_df()

## [FugueSQL](https://towardsdatascience.com/introducing-fuguesql-sql-for-pandas-spark-and-dask-dataframes-63d461a16b27) 
Python library that allows users to combine Python code and SQL commands. This gives users the flexibility to switch between Python and SQL within a Jupyter Notebook or a Python script.



## [Fugue e DuckDB preprocessing](https://github.com/khuyentran1401/Data-science/blob/master/productive_tools/Fugue_and_Duckdb/Fugue_and_Duckdb.ipynb)

	import pandas as pd
	import glob



	def process_files():
		filenames = glob.glob("crypto-binance/*/*/" + "*.csv")
		dfs = []
		for filename in filenames:
			df = pd.read_csv(filename)
			df['symbol'] = filename.split('/')[-1].split('.')[0]
			df['time'] = pd.to_datetime(df['Open_time'], unit='ms')
			df = df.drop(['Open_time'], axis=1)
			dfs.append(df)

		# Concatenate all data into one DataFrame
		big_frame = pd.concat(dfs, ignore_index=True)
		big_frame.to_parquet("raw.parquet")
		
	process_files()

## [Fugue and DuckDB: Fast SQL Code in Python](https://towardsdatascience.com/fugue-and-duckdb-fast-sql-code-in-python-e2e2dfc0f8eb)

Optimize Your SQL Code with Python and DuckDB
guardare:
* la pagina web
* la prova in ipynb

![](https://miro.medium.com/max/700/1*t76iHEV7wTwqXDDpUSXtXg.png)


## siti da finire di studiare

## Introducing FugueSQL — SQL for Pandas, Spark, and Dask DataFrames
An End-To-End SQL Interface for Data Science and Analytics 

https://colab.research.google.com/drive/1e1beWqYOcFidKl2IxHtxT5s9i_6KYuNY#scrollTo=vujLPgUqHztl

[Writing Parquet Files in Python with Pandas, PySpark, and Koalas](https://mungingdata.com/python/writing-parquet-pandas-pyspark-koalas/)

https://www.learnpythonwithrune.org/load-files-with-pandas-csv-and-excel-and-parquet-files/

