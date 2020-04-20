# 2-1 openpyxl とは
Python から Excel ファイルを操作可能な Python 製のソフトウェアです

# 2-2 Python で Excel 操作ができるソフトウェア一覧

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

# 2-3 ファイルの作成と保存とロード
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

## [Try] ファイルの作成・保存・読込を試す
1.Python をインタプリタモードで起動する
```
# python 
Python 3.6.8 (default, Aug  7 2019, 17:28:10)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

2.ワークブックを作成する

```
>>> from openpyxl import Workbook
>>> wb = Workbook()
```

3.名前を付けて保存し、python のインタプリタを停止する

```
>>> wb.save("sample.xlsx")
>>> exit()
```

4.Excel データを読み込む

```
>>> from openpyxl import load_workbook
>>> wb = load_workbook("sample.xlsx")
```

終わったら exit() で終了する

# 2-4 シートの操作
## シートを作成する
※ファイル作成時はデフォルトでシートが作成されている

シートを作成する場合は以下のようにする

```
wb.create_sheet("シート名")
```

## シートの一覧を取得する

```
wb.sheetnames
```

## シートを選択する
シートは変数に格納する

```
ws = wb["シート名"]
```

シート作成とともに、シートを選択した状態にする場合は以下のようにする

```
ws = wb.create_sheet("シート名")
```

## [Try] シート操作を試す

1. Python をインタプリタモードで起動する
```
# python 
Python 3.6.8 (default, Aug  7 2019, 17:28:10)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```
2.ワークブックをロードする

```
>>> from openpyxl import load_workbook
>>> wb = load_workbook("sample.xlsx")

```

3.シートの一覧を取得する

```
>>> wb.sheetnames
['Sheet']
```

4.シートを作成し、シートを一覧を取得する

```
>>> wb.create_sheet("TestSheet")
<Worksheet "TestSheet">
>>> wb.sheetnames
['Sheet', 'TestSheet']
```

5.シートを選択する

```
>>> ws = wb["TestSheet"]
>>> ws
<Worksheet "TestSheet">
```

6.ワークブックを保存する

```
>>> wb.save("sample.xlsx")
>>> exit()
```

# 2-5 セルの操作
この後はセルにデータの投入と参照について学びます。

フォントや色などの装飾については、公式ドキュメントを参照ください。

## セルデータの取得
単体では以下で取得する

```
ws["A1"].value
```

範囲で取得する場合は以下のようにする

```
ws["A1:A5"] # タプルで値が返ってくるため、データにアクセスするには一工夫が必要

```

## セルにデータ投入してみる

```
ws["A1"].value = "Hello World"

```

## [Try] セルにデータの投入する

1. Python 起動からシートの選択まで実施する

```
# python 
Python 3.6.8 (default, Aug  7 2019, 17:28:10)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> from openpyxl import load_workbook
>>> wb = load_workbook("sample.xlsx")
>>> ws = wb["TestSheet"]
```

2. セルを選択する

```
>>> cell = ws["A1"]
>>> cell
<Cell 'TestSheet'.A1>
```

3. セルにデータを投入する

```
>>> cell.value = "Hello World"
```

4. データを確認する

``` 
>>> cell.value
'Hello World'
>>> wb.save("sample.xlsx")
>>> exit()
```
## 2-6 [Try] List データを書き込む
1. Python 起動からシートの選択まで実施する

```
# python 
Python 3.6.8 (default, Aug  7 2019, 17:28:10)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> from openpyxl import load_workbook
>>> wb = load_workbook("sample.xlsx")
>>> ws = wb["Sheet"]
```

2. 書き込むデータを用意する

```
>>> fruits = [["apple"],["lemon"],["melon"]]
```

3. データを書き込む
```
>>> for i in fruits:
...     ws.append(i)
```

ファイルを開いて閲覧可能なら開いて確認する

## 2-7 [Try] 末尾にデータを追加する
1. Python 起動からシートの選択まで実施する

```
# python 
Python 3.6.8 (default, Aug  7 2019, 17:28:10)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> from openpyxl import load_workbook
>>> wb = load_workbook("sample.xlsx")
>>> ws = wb["TestSheet"]
```

2. 追加する

```
>>> ws.append(["banana"])
```

上記方法は想定しない箇所に追記する場合があります。

[戻る](../1-setup/README.md)
[進む](../3-create_method/README.md)
