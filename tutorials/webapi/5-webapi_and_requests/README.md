せっかくなので、Python から WebAPI にアクセスする方法を紹介します

# Get リクエスト

```
# python
Python 3.7.0 (v3.7.0:1bf9cc5093, Jun 27 2018, 04:59:51) [MSC v.1914 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import requests
>>> url = "http://localhost:8000/"
>>> response = requests.get(url)
>>> response
<Response [200]>
>>> response.text
'{"Hello":"World"}'
>>>
```

このような感じで requests モジュールを使用することで API にアクセスができます

[back](../4-webapi_and_excel/README.md)
[next](../6-challenge/README.md)
