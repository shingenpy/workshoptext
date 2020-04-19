# 1-1 openpyxl とは
Python から Excel ファイルを操作可能な Python 製のソフトウェアです

# 1-2 Python で Excel 操作ができるソフトウェア一覧

* python-xlsx 
  * https://github.com/python-excel/xlrd
  * https://github.com/python-excel/xlwt
  * https://github.com/python-excel/xlutils

* XlsxWriter
  * https://xlsxwriter.readthedocs.io/getting_started.html
書き込み専用である

* Xlwing
  * https://www.xlwings.org/
有償版、無償版あり
他の 3 つのソフトウェアと違い Excel 本体が必要であるが、Excel で使用できる機能は網羅している

# 1-3 ファイルの作成と保存とロード
## ファイルの作成には Workbook を import する

```
from openpyxl import Workbook
wb = Workbook()
```

## ファイルの保存

```
wb.save("ファイル名")
```

## ファイルのロードには load_workbook を import する

```
from openpyxl import load_workbook
wb = load_workbook("ファイル名")
```

## 一通りやってみる
Python をインタプリタモードで起動する
```
# python 
Python 3.6.8 (default, Aug  7 2019, 17:28:10)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

ワークブックを作成する

```
>>> from openpyxl import Workbook
>>> wb = Workbook()
```

名前を付けて保存し、python のインタプリタを停止する

```
>>> wb.save("sample.xlsx")
>>> exit()
```

excel データを読み込む

```
>>> from openpyxl import load_workbook
>>> wb = load_workbook("sample.xlsx")
```

# 1-4 シートの操作
## シートの作成する

## シートの一覧する

## シートを選択する

# 1-5 セルの操作


# 1-6 List データを投入する


# 1-7 追加でデータを投入する


