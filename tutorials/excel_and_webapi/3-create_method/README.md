# 3-1 [Try] 初期化用の関数の作成を行う
この関数はファイルの作成を行う

とりあえず、それっぽく書いてみます。

init.py
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

init.py
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

get.py
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

get.py
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

add.py 
```
def set_data(name):
    if os.path.exists(DATAPATH):
        wb = load_workbook(DATAPATH)
    else:
        print("Excel file not exists")
        exit()
    ws = wb.active
    ws.append([name])
    wb.save(DATAPATH)
```

# 3-4 [Try] コマンドラインからデータを投入できる python スクリプトを作成する
まずは、コマンドラインから情報を取得するスクリプトを書く

exadd.py
```
import 

args = sys.argv

if __name__ == '__main__':
    print(args)
```

実行してみよう

```
 (env) # python exadd.py 1 a b 3
 ['exedd.py', '1', 'a', 'b', '3']
```

- 全引数はスクリプトを含めてリストとして返される
- 数値・文字列にかかわらず、文字列として返される


次に先ほど作った add.py を再利用する

```
import sys
import add

args = sys.argv

if __name__ == '__main__':
    print(args[1])
    add.set_data(args[1])
```

ちなみに、Python でコマンドを作成する場合以下ソリューションが便利である
* [argparse](https://docs.python.org/ja/3/howto/argparse.html)

[前のページへ戻る](../2-use_openpyxl/README.md)
/
[次のページへ進む](../4-challenge/README.md)

