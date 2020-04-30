# excel method 

以下は [yuukis](https://gist.github.com/yuukis/3e53bd3a214da3e6b72f78f343155200)さんから頂いたスクリプトを今回用に機能を追加させていただきました。

ご協力ありがとうございます。

```
from openpyxl import Workbook, load_workbook
import os

DATAPATH = "data2.xlsx"

def init():
    if not os.path.exists(DATAPATH):
        Workbook().save(DATAPATH)
    else:
        print("File Exists")

def get_name_from_index(index_number: int) -> str:
    if os.path.exists(DATAPATH):
        wb = load_workbook(DATAPATH)
    else:
        print("Excel file not exists")
        exit()
    ws = wb.active
    if index_number <= 0:
        exit()
    return ws["A{}".format(index_number)].value

def get_data_from_name(name) -> dict:
    if os.path.exists(DATAPATH):
        wb = load_workbook(DATAPATH)
    else:
        print("Excel file not exists")
        exit()
    
    ws = wb.active

    for i in range(1,ws.max_row+1):
        if ws["A{}".format(i)].value == name:
            return {"name": ws["A{}".format(i)].value,"age": ws["B{}".format(i)].value,"gender": ws["C{}".format(i)].value}
    return {"message":"Nothing"}
    
def insert_data(name: str, age: int, gender: str):
    if os.path.exists(DATAPATH):
        wb = load_workbook(DATAPATH)
    else:
        print("Excel file not exists")
        exit()
    
    ws = wb.active
    ws.append([name, age, gender])
    wb.save(DATAPATH)
```

今回はすべて関数で書きましたが、前回の課題で提出いただいた
[excel_meibo.py](https://gist.github.com/k0syam/cb7076d58bc4061434cd94584025a9e9) 
のように
[dataclass](https://docs.python.org/ja/3/library/dataclasses.html)やクラスを使うとすっきりかけます

ご協力ありがとうございました。

※ pdataclass は python3.7 以降で使えるようになっています

# about type hint

python3.5 から型ヒントと呼ばれる機能が追加されています。

https://docs.python.org/ja/3.5/library/typing.html

例
```
# python3
Python 3.6.8 (default, Aug  7 2019, 17:28:10)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> def add(x: int, y:int) -> int:
...     return x + y
...
>>> add(1,2)
3
>>> add('2', 3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in add
TypeError: must be str, not int
```

このように、型ヒントを追加するだけで簡単なデータバリデーションをすることが可能です。
