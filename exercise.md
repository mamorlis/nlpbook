# 練習問題

## 1章

### 1

（回答例）

自然言語処理タスクの定義では、何を入力し、何を出力するかを決める。例えば、文書分類では文書を入力し、あらかじめ定めたカテゴリを出力する。英日機械翻訳では英語の文を入力し、日本語の訳文を出力する。

### 2

（回答例）

分類タスクでは、全事例のうち正しく分類した割合を正解率、正例と予測したうち実際に正例だった割合を適合率、実際の正例のうち検出できた割合を再現率という。$F_1$ は適合率と再現率の調和平均である。誤検出と見逃しのどちらを重く見るかによって、重視する尺度が変わる。

生成タスクでは、機械翻訳の BLEU や要約の ROUGE のように、生成した文と参照文の重なりを測る尺度が使われる。機械翻訳の品質推定では、原文とシステムの訳文から、参照訳なしで品質スコアを予測する。品質推定モデルの性能は、例えば人手評価との順位相関で測れる。

- 関連ノートブック:
  - [分類タスクの評価尺度と閾値調整（Fβ・特異度・不均衡データ）](notebooks/ch1_evaluation.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)）
  - [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)）
  - [文書要約のベースラインと ROUGE 評価](notebooks/ch4_summarization.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)）
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)）

**ノートブックで確認**（CPU） — 分類評価の演習で閾値 `0.55` と `0.70` を比べる。見逃しを減らしたい場合はどちらを選ぶか。適合率と再現率を根拠に説明する。

### 3

（回答例）

「深層学習は機械学習である」は真。「機械学習は深層学習である」は偽。深層学習は機械学習の一分野であるため。

### 4

（回答例）

従来のアプローチと比較した深層学習の利点は以下の4つである。

1. 流暢な言語生成が可能になった。
2. 事前学習済みモデルを使えば、用途ごとに用意する教師データを減らせる場合がある。
3. テキストと画像など、複数の種類の入力を同じモデルで扱えるようになった。
4. 自然言語による指示が可能になった。

- 関連ノートブック:
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)）

### 5

（回答例）

従来のアプローチと比較した深層学習の欠点は以下の3つである。

1. ハルシネーションが起きる場合がある。
2. ハイパーパラメータの探索に時間がかかる。
3. 大規模モデルの学習には、多くのデータや GPU などの計算資源が必要になる。

- 関連ノートブック:
  - [自然言語処理システムの開発サイクル（文分割・データ分割・計算量）](notebooks/ch1_design_cycle.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_design_cycle.ipynb)）
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)）

## 2章

### 1

（回答例）

文を対象とする場合は文法情報や意味情報などの細かい粒度の言語情報を用いた解析ができるという利点がある。一方、機械学習のアプローチを取る場合は、文単位でアノテーションされた訓練データが必要になる。

文書を対象とする場合は文書単位でアノテーションされたデータが容易に入手可能であるという利点がある。一方、具体的にどの部分が予測に寄与しているのかの根拠となる表現を分析しにくい。

- 関連ノートブック:
  - [評価極性辞書と文単位・文書単位の極性分析](notebooks/ch2_sentiment_lexicon.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)）
  - [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)）
  - [SVM カーネル（線形 vs RBF）と k 近傍法による根拠分析](notebooks/ch2_svm_knn.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_svm_knn.ipynb)）
  - [単語埋め込み（分散表現）と文脈付き埋め込みの比較](notebooks/ch2_word_embeddings.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_word_embeddings.ipynb)）
  - [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)）

### 2

（回答例）

多クラス分類問題は入力を複数あるクラスのどれか一つに分類する問題である。具体例としては、記事を「政治」「経済」「スポーツ」のいずれか一つに分類するタスクがある。

多ラベル分類問題は入力に対し複数あるラベルそれぞれについて分類する問題である（ラベルが n 個あれば 2^n 個の組み合わせがある）。具体例としては、同じ記事に「政治」と「スポーツ」を同時に付けるタスクがある。

- 関連ノートブック:
  - [多クラス分類と多ラベル分類（評価指標と共起）](notebooks/ch2_multilabel.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)）

### 3

（回答例）

参照文を用いた評価はシステム出力の評価の根拠の検証が容易であるという利点があるが、参照文の数が少ない場合に必ずしも適切に評価できないという問題がある。

一方、参照文を用いない評価は参照文の品質やカバー率に左右されないという利点があるが、品質推定モデルが対象言語・分野で人手評価とどの程度一致するかを検証する必要がある。

- 関連ノートブック:
  - [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)）
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)）

### 4

（回答例）

- 分類問題: 入力にクラス（離散値）を割り当てる問題。多クラス分類では複数の候補から一つを選ぶ。
- 回帰問題: 入力に対し実数値を出力する問題。出力間の順序関係を用いてランキング問題に変換することができる。
- ランキング問題: 入力に対しランキングを出力する問題。順位だけではスコアの差や絶対値は決まらず、間隔尺度や比例尺度を仮定する必要がない。

- 関連ノートブック:
  - [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)）
  - [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)）

## 3章

### 1

（回答例）

系列ラベリングタスクは、文字や単語などのリスト（系列）を入力とし、そのそれぞれの要素に対してラベルを出力するタスクである。
具体例としては、単語列を入力として各単語に人名や組織名などの固有表現タグ（BIO タグなど）を出力する固有表現認識、文字列や単語列を入力として単語境界ラベルや品詞ラベルを出力する形態素解析（単語分割・品詞推定）、単語列を入力として各単語に対する正誤ラベルや編集操作ラベル（保持・削除・追加・置換）を出力する文法誤り検出・訂正などがある。

- 関連ノートブック:
  - [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)）
  - [単語ラティス・Viterbi アルゴリズムと CRF vs MEMM](notebooks/ch3_viterbi_crf.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)）
  - [ガゼッティア（辞書）による固有表現認識とサブワード・BIO ラベル整合](notebooks/ch3_ner_gazetteer_subword.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)）
  - [BERT による固有表現認識（Token Classification）](notebooks/ch3_bert_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_bert_ner.ipynb)）

### 2

（回答例）

SVM や CRF などの機械学習手法で系列ラベリング問題を解く際に、モデル実行時にデータから動的に素性を展開するための仕組みである。すべての素性を人手で一つひとつ書き下すことなく、前後のトークンの表層形や品詞などを参照するユニグラム素性や、複数の素性を組み合わせたバイグラム（組合せ）素性などを簡潔に定義・抽出することができる。

- 関連ノートブック:
  - [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)）
  - [単語ラティス・Viterbi アルゴリズムと CRF vs MEMM](notebooks/ch3_viterbi_crf.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)）

### 3

（回答例）

入力の各単語に対して「保持」「削除」「追加」「置換」といった編集タグを出力する問題として定式化し、訓練データに一定回数以上出現した訂正候補に出力を絞ることで、適合率の高い訂正システムを構築できる（また、自己回帰モデルのように 1 単語ずつ生成する必要がないため高速に動作する）という利点がある。
一方、訓練データに出現しない未知の誤りや、大幅な語順の入れ替え・書き換えを伴う誤りを訂正しにくいため、再現率に課題があるという欠点がある。

- 関連ノートブック:
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)）
  - [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)）

## 4章

### 1

（回答例）

- テキスト平易化・言い換え（パラフレーズ生成）・文体変換: 言語は「同じ」、意味は「同じ」、長さは「固定しない」。
- 見出し生成（タイトル生成）: 言語は「同じ」、意味は「要点を保つ」、長さは「違う（短くなる）」。
- 質問応答・質問生成: 言語は「同じ」、意味は「違う」、長さは「違う（または同じ）」。
- クロスリンガル要約（異言語間要約）: 言語は「違う」、意味は「要点を保つ」、長さは「違う（短くなる）」。

- 関連ノートブック:
  - [文書要約のベースラインと ROUGE 評価](notebooks/ch4_summarization.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)）

### 2

（回答例）

偽。系列変換タスクとはテキスト（単語列）を入力として別のテキスト（単語列）を出力するタスクのことであり、機械翻訳はその代表例である。統計的機械翻訳は機械翻訳を統計ベースのアプローチ（翻訳モデルと言語モデルの組み合わせ）で解く手法であり、系列変換タスクであることに変わりはない。

- 関連ノートブック:
  - [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)）
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)）

### 3

（回答例）

深層学習による系列変換タスクの成功を支えた主な技術革新は以下の 3 つである。

1. エンコーダ・デコーダモデル：入力を処理するエンコーダと出力を 1 トークンずつ生成する自己回帰型のデコーダをニューラルネットワークで結合し、条件付き確率を直接推定することで、従来手法のようなつなぎ目の違和感がなく流暢なテキスト生成が可能になった。
2. アテンション機構と Transformer：出力生成時に入力のどの部分を参照するかを動的に重み付けするアテンション機構（クロスアテンション）により、長文でも妥当性の高い生成が可能になった。さらに自己アテンションを用いた Transformer により、長距離の文脈を考慮しつつ並列計算による大規模な学習が可能になった。
3. 自己教師あり学習と事前学習モデル：大規模な生テキストから自己教師あり学習によって構築された事前学習モデル（大規模言語モデル）により、対象タスクの大規模な教師データがなくても流暢で高精度なテキスト生成が可能になった。

- 関連ノートブック:
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)）
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)）

## 5章

### 1

（回答例）

偽。日本の著作権法第30条の4では、情報解析などの非享受目的に必要な範囲で、著作権者の許諾なく利用できる場合がある。この規定は、著作権者の利益を不当に害する場合には適用されない。それ以外にも配慮すべき点がある。具体的には、言語資源やサービスのライセンス・利用規約（教育・研究目的限定で商用利用が不可である場合や、利用可能な組織の範囲が限定されている場合など）、個人情報やセンシティブなデータの保護、Web クローリング時の `robots.txt` によるアクセス制限やサーバ負荷といった技術的・道義的な問題、組織のコンプライアンスなどに配慮する必要がある。

- 関連ノートブック:
  - [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)）

### 2

（回答例）

偽。複数の作業者が同じデータに対して独立にタグ付け（アノテーション）を行い、作業者間の一致率を測定することで、ラベル付けの一貫性を定量的に測ることができる。代表的な指標として、偶然に一致する割合を考慮して補正した Kappa 係数（2 人の場合は Cohen の Kappa、各項目に同じ人数が名義ラベルを付ける場合は Fleiss の Kappa）が広く用いられている。

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
