# 自然言語処理の教科書
小町守「自然言語処理の教科書」（技術評論社）のサポートサイトです。

# 演習

第2章から5章までは演習があります。それぞれの章の演習の Google Colab のリンクです。

## 第2章

- [日本語 BERT モデルによる文書分類](https://colab.research.google.com/drive/17ePJgkOvxzm3DIEKfuuDWpCenqaXOpsb)
  - 最終確認 2025/04/01
  - 各自で作成したデータセットで演習いただくつもりでしたが、サンプルデータをダウンロードするように変更しました。
- [機械翻訳の品質推定](https://colab.research.google.com/drive/1sxMCQCY8LQU9VobYspP4GO4WIote426w)
  - 最終確認 2025/04/01
  - 各自で作成したデータセットで演習いただくつもりでしたが、サンプルデータをダウンロードするように変更しました。

## 第3章

- [Fast GECToR と cLang-8 による英語誤り検出・訂正](https://colab.research.google.com/drive/19NSqluC9GO82hlJMSO3u38DGwZudizil)
  - データの前処理に結構時間がかかり、無料版の Google Colab だと GPU の無料枠を使い切ってしまうようなので、データの前処理部分を別にやるよう Notebook を修正予定です。

## 第4章

- [Eole によるニューラル機械翻訳演習](https://colab.research.google.com/drive/1dYI2McofLYgSEMdB6c3C2KB4eoaVMYA6)
  - 最終確認 2026/10/20
  - 書籍で紹介している OpenNMT-py は2024年の v3.5.1 で開発が止まっているので、後継の [Eole](https://github.com/eole-nlp/eole) を使う演習に変更しました。コマンド名（`onmt_train` → `eole train` など）と設定ファイルの書き方が少し違いますが、演習の内容は同じです。
  - Google Colab の Python 3.13 では Eole の依存ライブラリがインストールできないため、ノートブックの中で uv を使って Python 3.12 の環境を作っています。
- 旧版：[OpenNMT-py によるニューラル機械翻訳演習](https://colab.research.google.com/drive/1D-GVWcqZ3WhH_oxgGnXQowKaTCUdBFuG)
  - 最終確認 2026/10/20
  - 書籍に載せている OpenNMT-py（v3.5.1）のコマンドで演習したい場合はこちらを使ってください。Eole 版と同じく、uv で Python 3.12 の環境を作っています。
  - fairseq は2022年で開発が止まっていて、Google Colab では動かせません。

## 第5章

書籍に載せている演習例は楽天データセットによるものなので配布はできませんが、配布可能なデータセットでのアノテーション例（Google Spreadsheet）を公開予定です。

# 練習問題

第1章から第6章までは章末に練習問題があります。それぞれの章の練習問題の[回答例](exercise.md)を掲載します。

# 正誤表

[正誤表](errata.md)を掲載します。本に関する誤りを見つけた場合は教えていただけると嬉しいです。

# リンク

[Amazon のページ](https://amzn.to/3K0j914) で購入できます（書籍版、Kindle 版ともにあります）。
EPUB/PDF 版は[技術評論社のページ](https://gihyo.jp/dp/ebook/2024/978-4-297-13864-6)から購入できます。
