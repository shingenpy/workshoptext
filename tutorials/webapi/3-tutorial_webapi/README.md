# 3-1 HelloWorld

まずは、HelloWorld を表示する WebAPI を作成します

以下を写経してください。

ファイル名は main.py で作成してください。

```
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}
```

上記、出来たら実行してみます

```
# uvicorn main:app --reload
:
:
Application startup complete
```

Application startup complete と表示されたらOKです

ウェブブラウザでアクセスしてみます

http://localhost:8000/ にアクセスしてみてください

```
{"Hello":"World"} 
```

と表示されたら成功です

この後は各種データにアクセスしてみます

# 3-2 List
まずは Python のリストデータにアクセスします

先ほどの main.py の末尾に以下のコードを追記してください

```
fruits = ["apple"]

@app.get("/id/{item_id}")
def read_from_index(item_id: int):
    return {"item_id": item_id, "q": fruits[item_id]}
```

ウェブブラウザでアクセスしてみます。

http://localhost:8000/id/0 にアクセスしてみてください。

```
{"item_id":0,"q":"apple"} 
```

と表示されたら成功です。

この後はデータにアクセスしてみます

# 3-3 Dict
つぎは辞書データにアクセスします。

先ほどの main.py の末尾に以下のコードを追記してください

```
color = {"red":"apple","yellow":"lemon"}

@app.get("/color/{color_name}")
def read_from_color(color_name: str):
    return {"color": color_name,"q": color[color_name]}
```

ウェブブラウザでアクセスしてみます

http://localhost:8000/color/yellow にアクセスしてみてください。

```
{"color":"yellow","q":"lemon"}
```

と表示されたら成功です。

# 3-4 Model 
pydantic モジュールの DataModel を使います

※本当は dataclass を使う予定でしたが、dataclass は  python3.6 では標準ではないため 使ってません

データ型として型ヒントに使うことができます。

```
from fastapi import FastAPI
from pydantic import BaseModel # 追記

class User(BaseModel):
    name: str
    age: int
    gender: str
 :
 :
@app.get("/users/{user_id}")
def read_user(user_id: int, q: str = None):
    return {"user_id": user_id, "q": q}

@app.put('/users/{user_id}')
def update_user(user_id: int, q: item: Item):
    return {"user_name": user,name. "user_id": user_id}
```

ウェブブラウザでアクセスしてみます

ここで Swagger UI を使ってみます

http://localhost:8000/docs にアクセスしてみてください。

Swagger UI では、作成した API の使い方など詳しくみることができます

API を試してみることができますので、いろいろ試してみてください。

[back](../2-setup/README.md)
[next](../4-webapi_and_excel/README.md)
