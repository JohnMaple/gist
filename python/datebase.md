
### pymysql连接mysqlq

```python
import pymysql

con = pymysql.connect(host='127.0.0.1', port=3306, user='root', passwd='123456', db='database_name', charset='utf8')
cursor = con.cursor()

query_sql = 'select id,name from table_name where id = %s' % (100)
print query_sql

cursor.execute(query_sql)
con.commit()

article = cursor.fetchone()
if not article:
    exit(0)
    
print article
    
cursor.close()
con.close()
```
