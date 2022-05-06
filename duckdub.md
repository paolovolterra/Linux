# [DUCKDB](https://github.com/duckdb/duckdb)

https://duckdb.org/docs/api/odbc/windows


* per excel & co serve l'[ODBC](https://duckdb.org/docs/api/odbc/windows) che si trova [QUI](https://github.com/duckdb/duckdb/releases/download/v0.3.3/duckdb_odbc-windows-amd64.zip) 
* il caricamento si fa sempre nello stesso modo 

![](https://datamonkeysite.files.wordpress.com/2022/04/image-2.png)

## trasformare un csv e salvarlo in parquet
```python
from pathlib import Path
import pandas as pd

df = pd.read_csv('crm1.csv')

Path('crm1.csv').stat().st_size

df.to_parquet('crm1.parquet')

Path('crm1.parquet').stat().st_size

import duckdb
lineitem = duckdb.query("SELECT * FROM 'crm1.parquet' where gender='Male'").to_df()
lineitem.sample(20)
```
