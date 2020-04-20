# 目次

- [1-1 Install Python](https://github.com/shingenpy/workshoptext/tree/master/tutorials/excel_and_webapi/1-setup#1-1-Install-Python)
- [1-2 Create directory to use this tutorial](https://github.com/shingenpy/workshoptext/tree/master/tutorials/excel_and_webapi/1-setup#1-2-Create-directory-to-use-this-tutorial)
- [1-3 Install openpyxl](https://github.com/shingenpy/workshoptext/tree/master/tutorials/excel_and_webapi/1-setup#1-3-Install-openpyxl)

# 1-1 Install Python
## windows 


## linux or Mac


# 1-2 Create directory to use this tutorial

まずは、本プロジェクト用のディレクトリを作成する

```
 # mkdir 20200420_works
 # cd 20200420_works
```

# 1-3 Install openpyxl
## 仮想化
Python の仮想化機構を使用して、本プロジェクト用の仮想化環境を作成する

作成後、仮想環境を有効化する

[linux/mac]

```
 # python --version 
 # python -m venv env
 # source env/bin/activate 
```

[Windows]

```
 # python --version
 # python -m venv env
 # env\\Scripts\\activate
```

## openpyxl のインストール
仮想化を有効にすると、プロンプトの先頭に (env) がつくようになる。

```
 (env)# pip install openpyxl 
```

[次へ進む](../2-use_openpyxl/README.md)
