pubg-bluezone-predictor
====

本ツールは PLAYERUNKNOWN'S BATTLEGROUNDS の安置予測を練習することを目的として作られた、PC向けWebアプリケーションです。

[こちら](https://kagijpn.github.io/pubg-bluezone-predictor/top/)
から本ツールを利用することが出来ます。

利用推奨環境
Google chrome

※ **AdBlock** 系をブラウザに導入していると、正常に動作しません。

また、初めてお使いの方は下記の[利用方法](#利用方法)をご一読ください。

## 利用方法

本ツールは**あらかじめ用意されている試合データを使って利用する**ことも可能ですが、**自分自身で練習用の試合データを作る**ことも可能です。

- [あらかじめ用意されている試合データを使う](#あらかじめ用意されている試合データを使って利用する場合)
- [自分自身で練習用の試合データを作る](#自分自身で練習用の試合データを作る場合)

### あらかじめ用意されている試合データを使って利用する場合
本ツールであらかじめ用意している試合データはいくつかあります。

[こちら](https://github.com/KagiJPN/pubg-bluezone-predictor/tree/master/blue-zone-predictor-core/app/resource)のページに飛ぶと、_〇〇.json_ をいう名前のリンクがあると思います。

そのリンクを押下すると少し下のほうに試合データが表示され、**Raw**, **Blame**, **History** とボタンが並んでいると思います。

その内の**Raw**にカーソルを合わせて右クリックをして、名前を付けて保存をして頂くと　_〇〇.json_　という形式でファイルを保存することができます。

その json ファイルを[トップページ](https://kagijpn.github.io/pubg-bluezone-predictor/top/)で読み込ませることで、ツールを利用することが出来ます。

安置読み練習ツールの利用方法は[こちら](#安置読み練習ツールの利用方法)でご確認ください。

### 自分自身で練習用の試合データを作る場合

本ツールでは、自分自身で試合データを作る事が可能です。

大きく分けて3つの手順を踏む必要があります。

1. [PUBG Developer Portal](https://developer.pubg.com/)で _API Key_ を発行する。詳細は[こちら](#APIKeyの発行方法)
2. [試合検索ページ](https://kagijpn.github.io/pubg-bluezone-predictor/players/)にて、_API Key_ 、 _Platform_ 、_PUBG NAME_ を入力して、自身がプレイした試合一覧を表示する。詳細は[こちら](#試合検索ページの使い方)
3. 試合一覧ページで表示されるデータをコピーして、json ファイルを作成する。詳細は[こちら](#試合一覧ページの使い方)

#### APIKEYの発行方法
[PUBG Developer Portal](https://developer.pubg.com/)で API Key を取得します。

 **GET YOUR OWN API KEY**というところを押して、言われた通りに進めていき、会員登録(無料)をします。(英語のサイトですが、そこまで難しい操作はありません)
 
 最終的に、下記のようなページにいくので、**API KEY** と書かれているところの文字列をコピーしておいてください。 

![pubg-apikey](https://raw.githubusercontent.com/KagiJPN/pubg-bluezone-predictor/master/docs/resource/img/pubg-apikey.JPG)

### tips
本ツールも API Key は複数登録可能です。
[PUBG Developer Portal](https://developer.pubg.com/)のアカウント１つで最大5つまで API Key を発行することが出来ます。
5つ発行して登録することをお勧めします。

#### 試合検索ページの使い方
[試合検索ページ](https://kagijpn.github.io/pubg-bluezone-predictor/players/)に飛ぶとこの様な画面が出てきます。
![search-page](https://raw.githubusercontent.com/KagiJPN/pubg-bluezone-predictor/master/docs/resource/img/search-page.JPG)

- API KEY というところに、先ほどコピーしておいた文字列をペーストして、右側の**ADD**ボタンを押下してください。
- 正常に追加されると、画像のように追加した API KEY が表示されます。
- 後は、プラットフォームと検索を掛けたい PUBG NAME を入力して、右側の**SEARCH**を押下してください。

押下したら、[試合一覧ページ](#試合一覧ページの使い方)に遷移します。

#### 試合一覧ページの使い方
正常な値で遷移されたら、このような画面に飛びます。
![matches-page](https://raw.githubusercontent.com/KagiJPN/pubg-bluezone-predictor/master/docs/resource/img/matches-page.JPG)

ここでは、実際に試合データを作るページとなります。

追加したい試合の右側の**ADD**ボタンを押下してください。押下すると、右側のテキストエリアに試合データが追加されていきます。

追加したい試合をすべてADDし終わったら、テキストエリアをクリックしてください。
自動的にコピーされた状態になります。

そうしたら試合データの整形に入ります。

- まずはメモ帳などのテキストを編集できるエディタを開いてください。(jsonをフォーマットできるエディタだと便利)
- まず初めに、```[]```を記入してください。
- ```[]``` を記入したら、その中にコピーされた試合データをペーストしてください。
- 最後に、ペーストされた試合データの一番最後の , (カンマ)を削除してください。
- 最終的に下記のような形になったら保存してください。保存したファイルは拡張子が ```.json``` になるようにファイル名を保存・編集してください。
```
[
    {"createdAt":"2/17 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/16 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/15 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/14 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/13 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/12 20:48" ~~~ "radius":126.09056640625}]}
]
```

##### tips
json データですが、生成されたものを足し合わせて一つのファイルにすることも可能です。
その場合は

```
[
    {"createdAt":"1/17 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"1/16 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"1/15 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"1/14 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"1/13 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"1/12 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/17 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/16 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/15 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/14 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/13 20:48" ~~~ "radius":126.09056640625}]},
    {"createdAt":"2/12 20:48" ~~~ "radius":126.09056640625}]}
]
```
のような形になるように、自身で整形を行ってください。

つまり、一度データを保存しておけば、月日が経つににつれて、どんどん試合データが増えていくということになります。もちろん、期間やマップによってファイルを分けるというこうとも出来ます。

※一番最後に **,** (カンマ)があると json として正しい形式ならないので注意してください。

安置読み練習ツールの利用方法は[こちら](#安置読み練習ツールの利用方法)でご確認ください。

## 安置読み練習ツールの利用方法

1. まず始めに、試合データの読み込みを行います。

**LOAD**を押すとファイルを選択することが出来ます。json 形式の試合データを読み込んでください。

2. 試合一覧から安置読みをしたいマッチを選択します。

下記の画像のように、左側に試合一覧が表示されます。
緑色のリンクを押すと、右側にマップが表示されます。

![pubg-predictor1](https://raw.githubusercontent.com/KagiJPN/pubg-bluezone-predictor/master/docs/resource/img/pubg-predictor1.JPG)

3. 安置予測の練習をする。

最初に表示される赤い円をクリックして、ドラッグ&ドロップをすると、円を動かすことが出来ます。「次の安置はここだ」って思ったところに赤い円を配置したら、画面上側の**矢印(⇒)** か **spaceキー** を押下してください。

画面上に表示されている表の **Current** は現在選択している試合の予測と実際の円の一致した割合が表示されます。

 **Total** は各試合の予測と実際の円の一致した割合の平均が表示されます。

 **矢印(⇒)** か **spaceキー** を押下後に実際の円が表示されます(白色)
 
 最後のフェーズまでいったら、赤い円(予測円)は表示されなくなります。
 そうしたら次の試合(緑色のリンク)を選択してください。

![pubg-predictor2](https://raw.githubusercontent.com/KagiJPN/pubg-bluezone-predictor/master/docs/resource/img/pubg-predictor2.JPG)

### tips
- 最終安置までやらなくても、別の試合に切り替えることは可能です。
- 左側のリストの **Date** や **Map** をクリックすると、昇順・降順に並べ替えることが出来ます。

## さいごに
分かりづらい説明も多々あると思います。
なにか分からないことがありましたら、私の[ディスコードサーバー](https://discord.gg/tQp8NEN)までお気軽にご連絡ください！

改善案や提案なども[ディスコードサーバー](https://discord.gg/tQp8NEN)にて、随時受け付けております。
より良いツールにアップデートするためにも、ぜひともご協力のほどよろしくお願い申し上げます。

ちなみに、[こちら](https://github.com/KagiJPN/pubg-bluezone-predictor/issues)に今後の アップデート・修正情報 をまとめています。
アップデートした内容や最新情報は、[ディスコードサーバー](https://discord.gg/tQp8NEN) にて通知していきます。

最後に、Web開発の協力者も募集してます！
私はWeb開発は趣味でしか行ったことが無いので、あまり得意ではありません。もし興味ある方がいたら是非一緒になにか作りましょう！

本ツールは、Github Pages を使い、外部依存のフレームワークも使っていないため pure で 
ecology で fabulous なものとなっています。
