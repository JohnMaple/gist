
### Rquests包

> 发送Get请求

```python
import requests
import json

url = 'http://localhost:8080/v1/crowd'
headers = {'appkey': '123456'}
response = requests.post(url=url, headers=headers)

print response.text
response_json = response.json()
```


> 发送Post请求

```python
import requests
import json

url = 'http://localhost:8080/v1/crowd'
headers = {'appkey': '123456'}
data = {'start': 1,
        'limit': 300
    }
    
response = requests.post(url=url, data=json.dumps(data), headers=headers)

print response.text
response_json = response.json()
```
 
    
    