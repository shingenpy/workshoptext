# 目次

# 2-1 Create directory to use this tutorial

まずは、本プロジェクト用のディレクトリを作成する

```
 # mkdir <todays_date>_works
 # cd <todays_date>_works
```

# 2-2 Install Software
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

## 各種ソフトウェアをインストール
仮想化を有効にすると、プロンプトの先頭に (env) がつくようになる。

以下のソフトウェアをインストールする

 * [openpyxl](https://openpyxl.readthedocs.io/en/stable/index.html)
 * [fastapi](https://fastapi.tiangolo.com/)
 * [uvicorn](https://www.uvicorn.org/)

```
 (env)# pip install openpyxl fastapi uvicorn 
```

[back](../1-before/README.md)
[next](../3-tutorial_webapi/README.md)
