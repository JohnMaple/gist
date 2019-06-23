
# soup 解析html

> 查找节点

```python
import requests
from bs4 import BeautifulSoup

response = requests.get("https://www.locahost.com/")
print response.text

soup = BeautifulSoup(response.text, "lxml")

for child in soup.select("#home_latest")[0].children:
    print child
```
