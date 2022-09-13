# python の練習

## 🅰️
<https://www.amazon.co.jp/スクレイピング・ハッキング・ラボ-Pythonで自動化する未来型生活-技術の泉シリーズ（NextPublishing）-齊藤-貴義-ebook/dp/B08H1KBYG2>
を amazon prime での無料購読をして、その内容を試した。

- csv や excel ファイル出力は簡単にできる。

- 数行のコードで、気象庁のデータをグラフにする例もある。
(過去の月平均気温を取得して、折線グラフにする。)
データの数値部分に ] や ) が含まれている部分があるので、少しデータ補正をする
必要があった。
## まだ試していないこと
- mecab での text 解析例
## B

郵便番号と緯度経度の汲みの csv を python で作成し、
gas で zipcode を検索して、住所, 緯度、経度を得るy硫黄な Web アプリを作成した。

緯度軽度の情報、郵便番号の情報は <https://github.com/geolonia/japanese-addresses>
の github repogitory を clone して生成した csv を利用した。
この csv を python (pandas) で merget した。(住所のfuklname で)
merge( outer join) では値が決定できなかった行が 5 万件ほとある。
今は、住所を適宜短くして検索し、一致するものが見つかったら、その緯度・軽度を採用することで、全ての行の緯度・軽度を決定している。
(m実装にはす18時間ほどかかる。もっと短くできる方法もあるだろう...)

URL の例
<https://script.google.com/macros/s/AKfycbzWhSuv7LQ-yVUozIbnWAi8PBfQvfedX2bxxv2-FX1RbpHLWcHssTe_tTihfYHKa3E/exec>

(zipcode 指定を省略した場合は、 100-0001 が指定されたものとして処理する。
zipcode の - は指定してもしなくても良い)

<https://script.google.com/macros/s/AKfycbzWhSuv7LQ-yVUozIbnWAi8PBfQvfedX2bxxv2-FX1RbpHLWcHssTe_tTihfYHKa3E/exec?zipcode=9000000>
```bash
wget -q -O 1.txt "https://script.google.com/macrs/s/AKfycbzMdkNDAF06uDUaS7SVaXoAd7svX5ZKiXmq4-0cOTqorEj8S0dbOsgYA-x2Uvnc9JYR/exec?zipcode=9000000"
katouyouichis-MacBook-Pro-5365:japanese-addresses katoy$ cat 1.txt
{
  "items": {
    "郵便番号": 9000000,
    "full_name": "沖縄県那覇市以下に掲載がない場合",
    "緯度": 26.199562,
    "経度": 127.691306
  }
}
```
