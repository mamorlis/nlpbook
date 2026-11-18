# 自然言語処理の教科書
小町守「自然言語処理の教科書」（技術評論社）のサポートサイトです。

姉妹サイトとして、自然言語処理の「やりたいこと」に対して「こうやればいい」をまとめた Google Colab ノートブック集 [NLP クックブック](https://github.com/mamorlis/nlpcookbook) も公開しています。本書で扱っている前処理・形態素解析・テキスト分類・固有表現抽出・文法誤り訂正・機械翻訳・要約・対話などの実装レシピも多数収録していますので、あわせてご活用ください。

## 演習

第1章から5章までは演習があります。ノートブック名をクリックすると GitHub 上で閲覧でき、「Open in Colab」をクリックすると Google Colab で直接実行できます。

### 第1章

- [分類・生成タスクの評価尺度と性質](notebooks/ch1_evaluation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)
  - 最終確認 2026/11/18
  - 分類タスクの評価尺度（正解率・適合率・再現率・F値、不均衡データでの正解率の罠、Macro/Micro 平均）と生成タスクの評価尺度（BLEU の修正 n-gram 適合率と簡潔性ペナルティ）を定義式から実装し、`scikit-learn` や `sacrebleu` と一致することを確認します。言い換えや否定反転の例を通じて表層一致尺度の限界も体験できます（CPU のみ・数秒で実行できます）。

### 第2章

- [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch2_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_tfidf_baseline.ipynb)
  - 最終確認 2026/11/18
  - [サンプルデータ](misc/covid-annotation.csv)を使い、TF-IDF + ロジスティック回帰で軽量ベースラインを構築します。予測に寄与している特徴量（重み）の可視化や、誤分類事例と `コメント` 列を照らし合わせたエラー分析を CPU のみ・数秒で体験できます。
- [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)
  - 最終確認 2026/10/20
  - Transformers 5 で動くように更新しました。東北大の BERT モデルの名前が `cl-tohoku` から `tohoku-nlp` に変わったので、合わせて変更しています。
  - 各自で作成したデータセットで演習いただくつもりでしたが、[サンプルデータ](misc/covid-annotation.csv)をダウンロードするように変更しました。
  - サンプルデータを1,000件（TRUE と FALSE が500件ずつ）に増やし、すべてのデータを使うようにしました（以前は50件だけ使っていたため、ほとんど推定できていませんでした）。ラベルの比率を揃えて訓練・開発・テストデータに分割し、正解率に加えて F1 でも評価します。テストデータでの正解率・F1 は0.95〜0.97程度です。
- [英日機械翻訳の品質推定](notebooks/ch2_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_qe.ipynb)
  - 最終確認 2026/10/21
  - データを WMT21・WMT22 の品質推定タスクで公開された英日翻訳のデータ（人手評価のスコア付き、それぞれ1,000文）に変更しました。WMT21 のデータで訓練し、WMT22 のデータでテストします。
  - 2021年以降更新されていない TransQuest の代わりに、Transformers の `Trainer` で XLM-R をファインチューニングするようにしました（TransQuest の MonoTransQuest と同じ構成です）。WMT22 の公式の評価尺度である Kendall's tau でも評価します。
  - 既存の品質推定モデル（COMET-QE）と比較するようにしました。英日のデータで訓練していない COMET-QE のほうが、800文でファインチューニングした XLM-R より人手評価との相関が高いことがわかります。

### 第3章

- [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)
  - 最終確認 2026/11/18
  - `SudachiPy` の分割単位（短単位・中単位・長単位）の違い、`SentencePiece` によるサブワード分割と未知語への振る舞い、BIO タグと CRF による固有表現認識（素性テンプレートによる精度変化と遷移重みの確認）を体験できます（CPU のみ・十数秒で実行できます）。
- [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
  - 最終確認 2026/11/18
  - Levenshtein 距離と隣接文字入れ替え（swap）を考慮した Damerau-Levenshtein 距離を動的計画法で実装し、スペル訂正の候補ランキングや n-gram 言語モデル（パープレキシティ）による誤り検出を体験できます（CPU のみ・数秒で実行できます）。
- [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)
  - 最終確認 2026/10/21
  - データを cLang-8 から、BEA-2019 共有タスクで公開された W&I+LOCNESS v2.1 に変更しました。W&I は非営利の研究・教育目的なら申請なしでダウンロードできるので、Lang-8 のデータの申請や cLang-8 の作成が不要になり、1つのノートブックで最後まで実行できます。
  - W&I の訓練データ（約3.4万文）で10エポック訓練し、T4 GPU で40分ほどで終わります。テストデータの正解は公開されていないので、開発データを半分に分けて開発データとテストデータにしています。
  - 学習率とエポック数を探索し、[GECToR の訓練ガイド](https://github.com/grammarly/gector/blob/master/docs/training_parameters.md)にならって最初の2エポックはエンコーダを固定して訓練する（`--cold_step_count 2`）ようにしました。Fast GECToR のこの機能にはバグがあるので、ノートブックの中でソースコードを1行修正しています。ERRANT で評価すると F0.5 は0.41程度です（最初の設定では0.26程度でした）。
  - Fast GECToR は2023年以降更新されていないため、ノートブックの中で `uv` を使って Python 3.10 の環境を作っています。

### 第4章

- [文書要約のベースラインと ROUGE 評価](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - 最終確認 2026/11/18
  - ROUGE-1 / ROUGE-2 / ROUGE-L を定義式から実装し、抽出型要約の 3 手法（リード法・TF-IDF スコアリング・TextRank）を比較します。ニュース型（冒頭結論）と後半結論型での手法ごとの得意・不得意や、抽出型要約の限界を確認できます（CPU のみ・数秒で実行できます）。
- [対話システムの基礎（ルールベースと検索型）](notebooks/ch4_dialogue.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_dialogue.ipynb)
  - 最終確認 2026/11/18
  - ELIZA 風の正規表現・テンプレートによるルールベース対話と、TF-IDF コサイン類似度を用いた用例検索型対話を実装し、未知発話に対するフォールバック設計やキャラクター一貫性の違いを確認できます（CPU のみ・数秒で実行できます）。
- [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - 最終確認 2026/10/21
  - 書籍で紹介している OpenNMT-py は2024年の v3.5.1 で開発が止まっているので、後継の [Eole](https://github.com/eole-nlp/eole) を使う演習に変更しました。コマンド名（`onmt_train` → `eole train` など）と設定ファイルの書き方が少し違いますが、演習の内容は同じです。
  - Google Colab の Python 3.13 では Eole の依存ライブラリがインストールできないため、ノートブックの中で `uv` を使って Python 3.12 の環境を作っています。
- 旧版：[OpenNMT-py によるニューラル機械翻訳演習](notebooks/ch4_opennmt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_opennmt.ipynb)
  - 最終確認 2026/10/20
  - 書籍に載せている OpenNMT-py（v3.5.1）のコマンドで演習したい場合はこちらを使ってください。Eole 版と同じく、`uv` で Python 3.12 の環境を作っています。
  - `fairseq` は2022年で開発が止まっていて、Google Colab では動かせません。

### 第5章

- [言語資源のクレンジングと重複排除（データリークの実験）](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)
  - 最終確認 2026/11/18
  - HTML タグ・URL 除去や Unicode 正規化（NFKC）、文字 n-gram の Jaccard 係数による近似重複検出を実装し、重複を除去せずにデータ分割した場合のデータリーク（評価の過大評価）を実験で確認できます（CPU のみ・数秒で実行できます）。
- [フレーズ分類ラベルアノテーションと品質管理](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - 最終確認 2026/11/16
  - 書籍に載せている演習例は楽天データセットによるものなので配布はできませんが、配布可能な宿泊レビュー風のサンプルデータ（100件）を作成し、スプレッドシート用の [Excel ファイル](misc/phrase-annotation.xlsx)と Colab 演習用の [CSV ファイル](misc/phrase-annotation.csv)を公開しました。
  - 2人の作業者による評価極性アノテーションから混同行列と Cohen の κ を計算し、不一致事例の分析・仕様書の改訂によって未知データでの一致率が向上するプロセスを体験できます。あわせて、3人以上の作業者に対する Fleiss の κ とクラウドソーシングでのスパマー検出、学習曲線や分類器の予測確率を用いたアノテーションミス検出も扱っています。

## 練習問題

第1章から第5章までは章末に練習問題があります。それぞれの章の練習問題の[回答例](exercise.md)を掲載します。

## 正誤表

[正誤表](errata.md)を掲載します。本に関する誤りを見つけた場合は教えていただけると嬉しいです。

## リンク

[Amazon のページ](https://amzn.to/3K0j914) で購入できます（書籍版、Kindle 版ともにあります）。
EPUB/PDF 版は[技術評論社のページ](https://gihyo.jp/dp/ebook/2024/978-4-297-13864-6)から購入できます。
