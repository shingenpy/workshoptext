# WebAPI と Excel 
この章では、前回の勉強会で作成した Python ファイルを使用して、FastAPI と連携します。
簡単な Get リクエストと Put メソッドを追加します

# Get Method

excel からデータを取得できることを確認する

先ほど main.py で作成した read_user 関数を修正します。

```
from fastapi import FastAPI
from pydantic import BaseModel 
import excel # 追記
:
:
@app.get("/users/{user_id}")
def read_user(user_id: int, q: str = None):
    data = excel.get_name_from_index(user_id)
    return {"user_id": user_id, "q": data}
```

http://localhost:8000/users/1 にアクセスしてみてください。

{"user_id":1,"q":"taro"} のように Excel ファイルの A1 が表示されていれば問題なしです

終わったら、Swagger UI でも確認してみてください

# Put Method

excel にデータを投入できることを確認します

先に excel.py に以下の関数を追加します

ファイルの末尾を返す関数です

```
def get_row():
    if os.path.exists(DATAPATH):
        wb = load_workbook(DATAPATH)
    else:
        print("Excel file not exists")
        exit()    
    return wb.active.max_row
```

次に main.py の update_user 関数を修正します

自動的に末尾に追記するので、user_id の指定は必要ないです

```
@app.put('/users/')
def update_user(user: User):
    data = excel.insert_data(user.name, user.age, user.gender)
    return {"user_name": user.name, "id": excel.get_row()}
```

登録時に user_id を返します

試してましょう！

[back](../3-webapi_and_excel/README.md)
[next](../5-webapi_and_requests/README.md)
