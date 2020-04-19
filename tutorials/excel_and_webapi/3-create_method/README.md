# 3-1 [Try] 初期化用の関数の作成を行う
この関数はファイルの作成を行う

とりあえず、それっぽく書いてみます。
```
from openpyxl import Workbook

DATAPATH = "data.xlsx"

def init_excel():
    Workbook().save(DATAPATH)

if __name__ == "__main__":
    "init_excel()
```

上の書き方がだと、実行するたびにファイルが再作成されてしまう

ファイルがあるかどうかの判定を行う

```
from openpyxl import Workbook
import os 

DATAPATH = "data.xlsx"

def init_excel():
    if not os.path.exists(DATAPATH): # ファイルの有無を確認している
        Workbook().save(DATAPATH)
    else:
        print("File Exists") 

if __name__ == "__main__":
    init_excel()
```

# 3-2 [Try] データ取得用関数の作成
この関数はデータを取得する

とりあえず、それっぽいものを作る
```
from openpyxl import load_workbook
DATAPATH = "data.xlsx"

def get_data(index_number):
    wb = load_workbook(DATAPATH)
    ws = wb.active
    return ws["A{}".format(index_number)].value
```

上記、メソッドだと以下の問題が発生する

- a.DATAPATH にファイルがない場合はエラーが発生する
- b.変数 index_number に 0 以下の数値が入るとエラーが発生する
- c.一次元以上のデータを扱えない

まずは、a b を対応する。
```
from openpyxl import load_workbook
import os
DATAPATH = "data.xlsx"

def get_data(index_number):
    if os.path.exists(DATAPATH):
        wb = load_workbook(DATAPATH)
    else:
        print("Excel file not exists")
        exit()
    ws = wb.active
    if index_number <= 0:
        exit()
    return ws["A{}".format(index_number)].value
```
c　については、必要になったら変更するようにする

# 3-3 [Try] データを投入用の関数を作成する
この関数はデータを末尾に追加する

```
def set_data(name):
    if os.path.exists(DATAPATH):
        wb = load_workbook(DATAPATH)
    else:
        print("Excel file not exists")
        exit()
    ws = wb.active
    ws.append([name])
```

# 3-4 [Try] コマンドラインからデータを投入できる python スクリプトを作成する



[前のページへ戻る](../2-use_openpyxl/README.md)
