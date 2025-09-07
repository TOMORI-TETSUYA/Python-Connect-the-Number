# コネクト・ザ・ナンバーズ

このゲームはPythonの``randint()``関数を使って点のx座標とｙ座標をランダムに決め、画面のあっちこっちに<br>
点が置かれるようにしている。<br>
``no_mouse_down()``関数を使って、プレイヤー正しい点をクリックすれば、点と点が線でつながれる。<br>
間違えた点か、画面上の点ではないところをクリックしたときあｈ、すべての線が消えてしまい、<br>
プレイヤーはゲームの最初からやり直しになります。<br>
すべての点を線でつないだらゲーム終了。<br>
<br>

# フローチャート
<img width="1652" height="3840" alt="Untitled diagram _ Mermaid Chart-2025-09-06-233258" src="https://github.com/user-attachments/assets/01086913-a493-422d-b27c-a23c41028040" />

プレイヤーが点をクリックしたか、そしてクリックした点は変数**next_dot**の値と同じ番号かをチェックしている。<br>
繋がっていない点が無くなるまでプログラムを動き続けます。<br>

## 事前準備

Pygame Zeroのインストール(Windows環境)<br>

1. コマンドプロンプトを開く<br>
2. パッケージマネージャーをインストールする<br>
```
python -m pip install -U pip
```
3. pygameのインストール<br>
   パッケージマネージャーをインストールしたら下記の<br>
   命令文を入力しENTERキーを押すこれでPygameがインストールされます。<br>
   ```
   pip install pygame
   ```
4. Pygame Zeroのインストール<br>
   最後に下記の命令文を入力しENTERキーを押す。<br>
   これでPygame Zeroがインストールされる。<br>
   ```
   pip install pgzero
   ```

# プログラミング

**1. 準備**<br>
IDLEを起動しFileメニューからNew Fileを選んで<br>
新しいファイルを作成する。<br>
<img width="204" height="308" alt="スクリーンショット 2025-09-07 072707" src="https://github.com/user-attachments/assets/a817ac8b-b29d-442b-a2c4-761a8657a1a6" />
<br>
**2. セーブする**<br>
フォルダーを新しく作成し、**Fileメニュー**内の**Save As**を選び**numbers.py**という名前で保存。<br>
<br>
**3. 画像用フォルダー**<br>
新しくimagesというフォルダを作成しConnect the Numberのフォルダの中に保存<br>
<br>
**4. 画像をセットする**<br>
Connect the Number用画像を保存する。<br>
<br>
**5. モジュールを組み入れる**<br>
プログラミングの準備が終わったら、IDLEファイルに戻り<br>
以下のソースコードを1行目に入力する。<br>
```
from random import randint
```
> [!TIP]
> **random**(ランダム)モジュールから``randint()``関数を
> 組み入れる。

**6. 画像サイズを設定する**<br>
ゲームの画面サイズを設定します。<br>
下記ソースコードを続けて書き加えます。<br>
```
WIDTH = 400
HEIGHT = 400
```
> [!TIP]
> 画像サイズをグローバル変数にセット。
> 単位はピクセル。

**7. リストを準備する**<br>
点を入れておくリストだけでなく、点を繋ぐ線を入れておくリストも必要。<br>
それと、次にクリックされるはずの点の番号を入れておく変数も必要。<br>
これらのリスト変数を作成。<br>

**ソースコード**<br>
```
dots = []
lines = []

next_dot = 0
```
**解説**

```
dots = []
lines = []
```
> [!NOTE]
> この2つのグローバルリストに点と線を入れます。

```
next_dot = 0
```
> [!NOTE]
> このグローバル変数には最初の0が代入されてます。
> 次にどの点をクリックすべきかを示すための変数。

**グローバル変数とローカル変数**

> [!IMPORTANT]
> 変数にはグローバル変数とローカル変数の2種類があります。
> グローバル変数はソースコードのどこでも使えますが、
> ローカル変数は、そのローカル変数が定義されたか関数の中でしか使えません。
> 関数の中でグローバル変数の値を変えたいときは、*global**というキーワードに
> 続けて変数の名前を書いておくこと。

**8. アクターをセット**<br>
このゲームのアクターは点が10個の設定。ループで10個の点を作り、それぞれの<br>
位置はランダムに決めてアクターリストに加えていく。<br>

**ソースコード**
```
for dot in range(0, 10):

    actor = Actor("dot")

    actor.pos = randint(20, WIDTH - 20), \

    randint(20, HEIGHT - 20)

    dots.append(actor)
```

**解説**

```
for dot in range(0, 10):
```
> [!NOTE]
> ループの回数は10回に設定

```
    actor = Actor("dot")
```

> [!NOTE]
> imagesフォルダーの点の画像を使って、
> 新しいアクターを作成。

```
   actor.pos = randint(20, WIDTH - 20), \
```

> [!NOTE]
> 点の画像全体が画面に表示されるよう、画面から
> 少なくとも20ピクセル離れた位置に点を置くように設定。

**8. アクターを描く**<br>
``draw()``関数を使って点を番号と一緒に画面に表示する。<br>
``screen.draw.text()``関数は文字列を引数として受け取るようにいるが、<br>
変数**number**に入っているのは整数のため。<br>
そのため``str()``関数を使って整数を文字列を文字列に変えなければならない。<br>

**ソースコード**
```
def draw():

    screen.fill("black")

    number = 1

    for dot in dots:

        screen.draw.text(str(number), \

                            (dot.pos[0], dot.pos[1] + 12))

        dot.draw()

        number = number + 1
```

**解説**

```
    screen.fill("black")
```

> [!NOTE]
> 背景色を黒に設定

```
    number = 1
```

> [!NOTE]
> 直前にクリックした点の番号を
> 入れておくための変数を作成。

```
    for dot in dots:

        screen.draw.text(str(number), \

                            (dot.pos[0], dot.pos[1] + 12))
```

> [!NOTE]
> この部分で、点を番号と一緒に
> 画面に描いている

