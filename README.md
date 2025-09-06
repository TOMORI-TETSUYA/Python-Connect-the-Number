# コネクト・ザ・ナンバーズ

このゲームはPythonの``randint()``関数を使って点のx座標とｙ座標をランダムに決め、画面のあっちこっちに<br>
点が置かれるようにしている。<br>
``no_mouse_down()``関数を使って、プレイヤー正しい点をクリックすれば、点と点が線でつながれる。<br>
間違えた点か、画面上の点ではないところをクリックしたときあｈ、すべての線が消えてしまい、<br>
プレイヤーはゲームの最初からやり直しになります。<br>
すべての点を線でつないだらゲーム終了。<br>
<br>

# フローチャート
<img width="1654" height="3840" alt="Untitled diagram _ Mermaid Chart-2025-09-06-214743" src="https://github.com/user-attachments/assets/213564ba-3570-492f-9171-88773d694514" />

プレイヤーが点をクリックしたか、そしてクリックした点は変数**next_dot**の値と同じ番号かをチェックしている。<br>
繋がっていない点が無くなるまでプログラムを動き続けます。<br>

## 事前準備

Pygame Zeroのインストール(Windows環境)<br>

1. コマンドプロンプトを開く<br>
2. パッケージマネージャーをインストールする<br>
```
python -m pip install -U pip
```
4. pygameのインストール<br>
   パッケージマネージャーをインストールしたら下記の<br>
   命令文を入力しENTERキーを押すこれでPygameがインストールされます。<br>
   ```
   pip install pygame
   ```
5. Pygame Zeroのインストール<br>
   最後に下記の命令文を入力しENTERキーを押す。<br>
   これでPygame Zeroがインストールされる。<br>
   ```
   pip install pgzero
   ```

# プログラミング

**1. 準備**<br>
IDLEを起動しFileメニューからNew Fileを選んで<br>
新しいファイルを作成する。<br>
![スクリーンショット 2025-09-07 072729](https://github.com/user-attachments/assets/f0b76d79-24f1-4346-9100-3b596b02c49b)

**2. セーブする**<br>
フォルダーを新しく作成し、**Fileメニュー**内の**Save As**を選び**numbers.py**という名前で保存。

