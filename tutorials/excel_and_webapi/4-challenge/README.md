# 4-1 [Try] set_data でカラムを 3 カラムを設定できるようにする
例）set_data('john', 25, 'man') を実行することで、excel ファイルに追記される

```
def set_data(name, year, gender):
    :
    :
```

# 4-2 [Try] 4-1 で作成した関数にデータのバリデーション機能を入れる

- 例) 年齢の値にマイナスが入った場合にエラーが発生するなど


```
def set_data(name, year, gender):
    :
    ws.append([name, year, gender])
    :
    :
    wb.save(...)

```

# 4-3 [Try] 削除、変更メソッドを作る

```
def delete_data():
    :

```

```
def modify_data():
    :
```

# 4-4 [Try] init, set, get を持つクラスで書き直す
