# 練習問題

## 1章

### 1

（回答例）

何が入力で何が出力であるかを規定するもの。

### 2

（回答例）

分類タスクの評価尺度には正解ラベルとの一致率によって計算する正解率、適合率・再現率、そして F 値が代表的である。
生成タスクの評価尺度にはリファレンスを用いた評価尺度である BLEU や ROUGE が用いられている。また、リファレンスを用いない品質推定という手法もある。

- 関連ノートブック:
  - [分類・生成タスクの評価尺度と性質](notebooks/ch1_evaluation.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)）
  - [文書要約のベースラインと ROUGE 評価](notebooks/ch4_summarization.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)）
  - [英日機械翻訳の品質推定](notebooks/ch2_qe.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_qe.ipynb)）

### 3

（回答例）

「深層学習は機械学習である」は真。「機械学習は深層学習である」は偽。深層学習は機械学習の一分野であるため。

### 4

（回答例）

従来のアプローチと比較した深層学習の利点は以下の4つである。

1. 流暢な言語生成が可能になった。
2. 必ずしも大規模な教師データを準備する必要がなくなった。
3. マルチモーダル処理の垣根がなくなった。
4. 自然言語による指示が可能になった。

### 5

（回答例）

従来のアプローチと比較した深層学習の欠点は以下の3つである。

1. ハルシネーションが起きる場合がある。
2. ハイパーパラメータの探索に時間がかかる。
3. データや GPU など多くの計算資源が必要である。

## 2章

### 1

（回答例）

文を対象とする場合は文法情報や意味情報などの細かい粒度の言語情報を用いた解析ができるという利点がある。一方、機械学習のアプローチを取る場合は、文単位でアノテーションされた訓練データが必要になる。

文書を対象とする場合は文書単位でアノテーションされたデータが容易に入手可能であるという利点がある。一方、具体的にどの部分が予測に寄与しているのかの根拠となる表現を分析しにくい。

- 関連ノートブック:
  - [評価極性辞書（否定・逆接ルール）と機械学習の比較](notebooks/ch2_sentiment_lexicon.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)）
  - [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch2_tfidf_baseline.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_tfidf_baseline.ipynb)）
  - [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)）

### 2

（回答例）

多クラス分類問題は入力を複数あるクラスのどれか一つに分類する問題である。具体例としては、スパム分類タスクがある。

多ラベル分類問題は入力に対し複数あるラベルそれぞれについて分類する問題である（ラベルが n 個あれば 2^n 個の組み合わせがある）。具体例としては、記事のカテゴリ分類タスクがある。

- 関連ノートブック:
  - [多クラス分類と多ラベル分類（評価指標と共起）](notebooks/ch2_multilabel.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)）

### 3

（回答例）

参照文を用いた評価はシステム出力の評価の根拠の検証が容易であるという利点があるが、参照文の数が少ない場合に必ずしも適切に評価できないという問題がある。

一方、参照文を用いない評価は参照文の品質やカバー率に左右されないという利点があるが、多言語に対応した言語モデルの存在を仮定しているという問題がある。

- 関連ノートブック:
  - [分類・生成タスクの評価尺度と性質](notebooks/ch1_evaluation.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)）
  - [英日機械翻訳の品質推定](notebooks/ch2_qe.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_qe.ipynb)）

### 4

（回答例）

- 分類問題: 入力に対し複数のクラス（離散値）を出力する問題。それぞれのクラス間には依存関係はない。
- 回帰問題: 入力に対し実数値を出力する問題。出力間の順序関係を用いてランキング問題に変換することができる。
- ランキング問題: 入力に対しランキングを出力する問題。回帰問題に変換することはできないが、出力が間隔尺度や比例尺度のような性質に従うという仮定が必要ない。

- 関連ノートブック:
  - [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)）

## 3章

### 1

（回答例）

系列ラベリングタスクは、文字や単語などのリスト（系列）を入力とし、そのそれぞれの要素に対してラベルを出力するタスクである。
具体例としては、単語列を入力として各単語に人名や組織名などの固有表現タグ（BIO タグなど）を出力する固有表現認識、文字列や単語列を入力として単語境界ラベルや品詞ラベルを出力する形態素解析（単語分割・品詞推定）、単語列を入力として各単語に対する正誤ラベルや編集操作ラベル（保持・削除・追加・置換）を出力する文法誤り検出・訂正などがある。

- 関連ノートブック:
  - [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)）

### 2

（回答例）

SVM や CRF などの機械学習手法で系列ラベリング問題を解く際に、モデル実行時にデータから動的に素性を展開するための仕組みである。すべての素性を人手で一つひとつ書き下すことなく、前後のトークンの表層形や品詞などを参照するユニグラム素性や、複数の素性を組み合わせたバイグラム（組合せ）素性などを簡潔に定義・抽出することができる。

- 関連ノートブック:
  - [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)）

### 3

（回答例）

入力の各単語に対して「保持」「削除」「追加」「置換」といった編集タグを出力する問題として定式化し、訓練データに一定回数以上出現した訂正候補に出力を絞ることで、適合率の高い訂正システムを構築できる（また、自己回帰モデルのように 1 単語ずつ生成する必要がないため高速に動作する）という利点がある。
一方、訓練データに出現しない未知の誤り訂正や、大幅な語順の入れ替え・書き換えを伴う誤りの訂正ができないため、再現率に課題があるという欠点がある。

- 関連ノートブック:
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)）
  - [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)）

## 4章

### 1

（回答例）

- テキスト平易化・言い換え（パラフレーズ生成）・文体変換: 言語は「同じ」、意味は「同じ」、長さは「同じ」。
- 文圧縮・見出し生成（タイトル生成）: 言語は「同じ」、意味は「同じ」、長さは「違う（短くなる）」。
- 質問応答・質問生成: 言語は「同じ」、意味は「違う」、長さは「違う（または同じ）」。
- クロスリンガル要約（異言語間要約）: 言語は「違う」、意味は「同じ」、長さは「違う（短くなる）」。

- 関連ノートブック:
  - [文書要約のベースラインと ROUGE 評価](notebooks/ch4_summarization.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)）

### 2

（回答例）

偽。系列変換タスクとはテキスト（単語列）を入力として別のテキスト（単語列）を出力するタスクのことであり、機械翻訳はその代表例である。統計的機械翻訳は機械翻訳を統計ベースのアプローチ（翻訳モデルと言語モデルの組み合わせ）で解く手法であり、系列変換タスクであることに変わりはない。

- 関連ノートブック:
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)）

### 3

（回答例）

深層学習による系列変換タスクの成功を支えた主な技術革新は以下の 3 つである。

1. エンコーダ・デコーダモデル：入力を処理するエンコーダと出力を 1 トークンずつ生成する自己回帰型のデコーダをニューラルネットワークで結合し、条件付き確率を直接推定することで、従来手法のようなつなぎ目の違和感がなく流暢なテキスト生成が可能になった。
2. アテンション機構と Transformer：出力生成時に入力のどの部分を参照するかを動的に重み付けするアテンション機構（クロスアテンション）により、長文でも妥当性の高い生成が可能になった。さらに自己アテンションを用いた Transformer により、長距離の文脈を考慮しつつ並列計算による大規模な学習が可能になった。
3. 自己教師あり学習と事前学習モデル：大規模な生テキストから自己教師あり学習によって構築された事前学習モデル（大規模言語モデル）により、対象タスクの大規模な教師データがなくても流暢で高精度なテキスト生成が可能になった。

- 関連ノートブック:
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)）

## 5章

### 1

（回答例）

偽。日本の現行の著作権法では情報解析を目的とする場合は原則として著作権者の同意なくデータを利用できるが、それ以外にも配慮すべき点がある。具体的には、言語資源やサービスのライセンス・利用規約（教育・研究目的限定で商用利用が不可である場合や、利用可能な組織の範囲が限定されている場合など）、個人情報やセンシティブなデータの保護、Web クローリング時の `robots.txt` によるアクセス制限やサーバ負荷といった技術的・道義的な問題、組織のコンプライアンスなどに配慮する必要がある。

- 関連ノートブック:
  - [言語資源のクレンジングと重複排除（データリークの実験）](notebooks/ch5_data_cleaning.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)）

### 2

（回答例）

偽。複数の作業者が同じデータに対して独立にタグ付け（アノテーション）を行い、作業者間の一致率を測定することで言語資源の質を定量的に測ることができる。代表的な指標として、偶然に一致する割合を考慮して補正した Kappa 係数（2 人の場合は Cohen の Kappa、3 人以上の場合は Fleiss の Kappa）が広く用いられている。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと品質管理](notebooks/ch5_annotation.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)）

### 3

（回答例）

クラウドソーシングを用いるときに気をつけるべき点は以下の 3 つである。

1. 作業者は自然言語処理の専門家ではなく個別の綿密なやりとりも難しいため、迷わず作業できるようタスク仕様や指示をわかりやすく設計すること。
2. 高度なアノテーションや試行錯誤が必要な実験的タスクには向かないため、作業内容をある程度定型的に切り出せるタスクに適用すること。
3. 真面目に作業しないスパマーが混じる可能性があるため、あらかじめ答えがわかっている問題を混ぜてチェックしたり、承認率が高い作業者に限定して依頼したりするなどの品質管理を行うこと。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと品質管理](notebooks/ch5_annotation.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)）

## 謝辞

練習問題の検討については東京都立大学システムデザイン学部情報科学科（当時）の長谷川諒さん、増子凱斗さん、江渡友美華さん、田中日加吏さん、そして自然言語処理研究室の皆さんにご協力いただきました。ありがとうございました。
