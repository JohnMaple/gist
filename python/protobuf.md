
### protobuf和json转换

> protobuf转json

```python
import sys

import requests
from flask import Flask, request

from src.protoc2json import proto
from google.protobuf import json_format

reload(sys)
sys.setdefaultencoding('utf8')

app = Flask(__name__)


@app.route('/protobuf', methods=['POST'])
def on_protobuf():
    bidRequest = proto.BidRequest()
    bidRequest.ParseFromString(request.get_data())
    json_str = json_format.MessageToJson(bidRequest)
    print json_str
    return 'OK'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=12345, debug=True)

```



> json转protobuf

```python
import sys

import requests
from flask import Flask, request

from src.protoc2json import proto
from google.protobuf import json_format
import warnings

reload(sys)
sys.setdefaultencoding('utf8')
warnings.filterwarnings('ignore')


def request(url):
    json = '''
    {
        "id": "e65dffcc50ed166c1",
    }
    '''

    bidRequest = proto.BidRequest()
    json_format.Parse(json, bidRequest)

    json_str = json_format.MessageToJson(bidRequest)
    print json_str

    print '------------------------------------'

    headers = {'Content-Type': 'application/x-protobuf'}
    resp = requests.post(url, data=bidRequest.SerializeToString(), headers=headers)
    bidResponse = proto.BidResponse()
    bidResponse.ParseFromString(resp.content)
    resp_json_str = json_format.MessageToJson(bidResponse)
    print resp_json_str


if __name__ == '__main__':
    url = 'http://localhost/v1/protobuf'

    request(url)

```