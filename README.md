# 自然言語処理の教科書
小町守「自然言語処理の教科書」（技術評論社）のサポートサイトです。

# 演習

第2章から5章までは演習があります。それぞれの章の演習の Google Colab のリンクです。

## 第2章

- [日本語 BERT モデルによる文書分類](https://colab.research.google.com/drive/17ePJgkOvxzm3DIEKfuuDWpCenqaXOpsb)
  - 最終確認 2026/10/20
  - Transformers 5 で動くように更新しました。東北大の BERT モデルの名前が cl-tohoku から tohoku-nlp に変わったので、合わせて変更しています。
  - 各自で作成したデータセットで演習いただくつもりでしたが、サンプルデータをダウンロードするように変更しました。
- [機械翻訳の品質推定](https://colab.research.google.com/drive/1sxMCQCY8LQU9VobYspP4GO4WIote426w)
  - 最終確認 2026/10/20
  - 早期終了の設定が逆（相関係数を小さくする向き）になっていたのを修正しました。以前のバージョンより推定の精度が上がっています。また、学習中のチェックポイント保存を減らして、無料版の Google Colab でも数分で学習が終わるようにしました。
  - 各自で作成したデータセットで演習いただくつもりでしたが、サンプルデータをダウンロードするように変更しました。

## 第3章

- Fast GECToR と cLang-8 による英語誤り検出・訂正
  - [（1）データの準備](https://colab.research.google.com/drive/1AlRWUL5bz4NLjhvjm25bsjj7_9LDDm9R)（CPU で実行）
  - [（2）訓練と評価](https://colab.research.google.com/drive/19NSqluC9GO82hlJMSO3u38DGwZudizil)（GPU で実行）
  - 最終確認 2026/10/20
  - 無料版の Google Colab だと GPU の無料枠を使い切ってしまうので、データの準備（CPU）と訓練・評価（GPU）の2つのノートブックに分けました。（1）で作ったデータは Google Drive に保存し、（2）で読み込みます。Lang-8 のデータ（`lang-8-20111007-2.0.zip`）は各自で申請して入手し、Google Drive に置いてください。
  - 訓練データを10万文、2エポックに減らして、T4 GPU で30分ほどで訓練が終わるようにしました。cLang-8 の単語分割も使う文だけにして、データの準備にかかる時間を短くしています。
  - Fast GECToR は2023年以降更新されていないため、ノートブックの中で uv を使って Python 3.10 の環境を作っています。また、訓練後に ERRANT で評価するようにしました。

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
