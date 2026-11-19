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

文を対象にすると、「立地は便利だった」「部屋が狭かった」のような異なる評価を切り分けられる。一方、文だけでは前後の文脈が分からない場合があり、文単位で教師あり学習するには通常、文ごとのラベルを用意する。

文書を対象にすると、レビュー全体に付いた星などを教師ラベルとして使える場合がある。一方、文書全体にラベルを1つ付けるだけでは、どの文が評価の根拠かは分かりにくい。

- 関連ノートブック:
  - [評価極性辞書と文単位・文書単位の極性分析](notebooks/ch2_sentiment_lexicon.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)）
  - [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)）
  - [SVM カーネル（線形 vs RBF）と k 近傍法による根拠分析](notebooks/ch2_svm_knn.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_svm_knn.ipynb)）
  - [単語埋め込み（分散表現）と文脈付き埋め込みの比較](notebooks/ch2_word_embeddings.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_word_embeddings.ipynb)）
  - [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)）

### 2

（回答例）

多クラス分類では、定められたクラスから一つを選ぶ。例えば、ニュース記事を「政治」「経済」「スポーツ」のいずれか一つに分類する。

多ラベル分類では、入力に当てはまるラベルをすべて付ける。例えば、同じニュース記事に「政治」と「スポーツ」を付けられる。ラベルが $n$ 種類なら、ラベルを一つも付けない場合を含め、最大 $2^n$ 通りの組み合わせがある。

- 関連ノートブック:
  - [多クラス分類と多ラベル分類（評価指標と共起）](notebooks/ch2_multilabel.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)）

### 3

（回答例）

参照文を用いる評価では、システムの出力と参照文を見比べて、スコアの根拠を調べられる。一方、参照文の数が少ないと、意味が合っていても参照文と異なる言い回しを低く評価することがある。

参照文を用いない評価では、入力ごとに参照文を作る手間を省ける。一方、自動品質推定を使う場合は、対象の言語や分野で推定値が人手評価とどの程度一致するかを検証する必要がある。

- 関連ノートブック:
  - [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)）
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)）

### 4

（回答例）

- **分類**では、入力にカテゴリを割り当てる。5段階評価を通常の多クラス分類として扱う場合、モデルは1カテゴリを選び、段階間の順序や間隔は標準的な損失に反映されない。
- **回帰**では、入力に対して数値を予測する。例えば文章の品質を実数値で予測する。二乗誤差で学習する場合は、予測値と正解値の数値的な差を使う。
- **ランキング**では、候補の順序を予測する。回帰の予測値を並べ替えて順位を作ることもできるが、順位だけから項目間のスコア差や絶対値は決まらない。

- 関連ノートブック:
  - [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)）
  - [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)）

## 3章

### 1

（回答例）

系列ラベリングタスクは、文字や単語などのリスト（系列）を入力とし、そのそれぞれの要素に対してラベルを出力するタスクである。
具体例としては、単語列を入力として各単語に人名や組織名などの固有表現タグ（例えば `B-PER` は人名の開始、`I-PER` はその続き、`O` は固有表現の範囲外）を出力する固有表現認識、文字列や単語列を入力として単語境界ラベルや品詞ラベルを出力する形態素解析（単語分割・品詞推定）、単語列を入力として各単語に対する正誤ラベルや編集操作ラベル（保持・削除・追加・置換）を出力する文法誤り検出・訂正などがある。

- 関連ノートブック:
  - [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)）
  - [単語ラティス・Viterbi アルゴリズムと CRF vs MEMM](notebooks/ch3_viterbi_crf.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)）
  - [ガゼッティア（辞書）による固有表現認識とサブワード・BIO ラベル整合](notebooks/ch3_ner_gazetteer_subword.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)）
  - [BERT による固有表現認識（Token Classification）](notebooks/ch3_bert_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_bert_ner.ipynb)）

### 2

（回答例）

SVM や CRF などの機械学習手法で系列ラベリング問題を解く際に、モデル実行時にデータから動的に素性を展開するための仕組みである。すべての素性を人手で一つひとつ書き下すことなく、前後のトークンの表層形や品詞などを参照するユニグラム素性や、複数の素性を組み合わせたバイグラム（組合せ）素性などを簡潔に定義・抽出することができる。例えば、「対象単語の品詞」と「直前の単語と対象単語の表層形の組」を指定しておくと、各位置に実際の品詞や表層形を当てはめて素性を作れる。

- 関連ノートブック:
  - [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)）
  - [単語ラティス・Viterbi アルゴリズムと CRF vs MEMM](notebooks/ch3_viterbi_crf.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)）

### 3

（回答例）

入力位置ごとに「保持」「削除」「追加」「置換」などの編集タグを選ぶ。出力候補をあらかじめ定め、各位置のタグを並列に予測できる。必要に応じて、編集後の文に再びタグを付けて訂正する。
一方、用意したタグの組み合わせで表しにくい語順の変更や大幅な書き換えは取りこぼしやすく、再現率が下がることがある。

- 関連ノートブック:
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)）
  - [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)）

## 4章

### 1

（回答例）

| タスク | 言語 | 意味 | 長さ |
| --- | --- | --- | --- |
| テキスト平易化・言い換え・文体変換 | 同じ | 元の意味をおおむね保つ | 固定しない |
| 見出し生成 | 同じ | 要点を残し、詳細は省く | 通常は短くなる |
| 同一言語での質問応答・質問生成 | 同じ | 質問と回答など、役割の異なる内容を出力する | 固定しない |
| クロスリンガル要約 | 異なる | 要点を残し、詳細は省く | 通常は短くなる |

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

1. エンコーダ・デコーダモデル：入力を処理するエンコーダと出力を 1 トークンずつ生成する自己回帰型のデコーダをニューラルネットワークで結合し、条件付き確率を直接推定することで、入力全体を条件として自然な語順の出力を学習できるようになった。
2. アテンション機構と Transformer：出力生成時に入力のどの部分を参照するかを動的に重み付けするアテンション機構（クロスアテンション）により、入力の離れた位置にある情報も出力生成時に参照できるようになった。さらに自己アテンションを用いた Transformer により、長距離の文脈を考慮しつつ訓練時に系列内の位置を並列に処理しやすくなった。
3. 自己教師あり学習と事前学習モデル：大規模な生テキストから自己教師あり学習によって構築された事前学習モデル（大規模言語モデル）により、対象タスクで用意する教師データが少ない場合にも、事前学習で得た知識を活用できるようになった。

- 関連ノートブック:
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)）
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)）

## 5章

### 1

（回答例）

偽。日本の著作権法第30条の4では、情報解析など、著作物に表現された思想や感情の享受を目的としない利用について、必要な範囲で許諾なしに利用できる場合がある。著作権者の利益を不当に害する場合はこの規定の対象外となる。データを扱う際は、ライセンスやサービスの利用規約、個人情報の保護、クローリング時の `robots.txt` やサーバ負荷にも配慮する。[著作権法第30条の4](https://laws.e-gov.go.jp/law/345AC0000000048#Mp-At_30_4)

- 関連ノートブック:
  - [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)）

### 2

（回答例）

偽。複数の作業者が同じ事例を独立にアノテーションし、単純一致率や、偶然の一致を補正した κ 係数を計算すると、ラベル付けの一貫性を測れる。例えば2人の名義ラベルには Cohen の κ、各事例に同じ人数が名義ラベルを付ける場合には Fleiss の κ を使える。一致度が高くても仕様自体の妥当性は別途確認する。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと品質管理](notebooks/ch5_annotation.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)）

### 3

（回答例）

クラウドソーシングを用いるときに気をつけるべき点は以下の 3 つである。

1. 作業者は自然言語処理の専門家ではなく個別の綿密なやりとりも難しいため、迷わず作業できるようタスク仕様や指示をわかりやすく設計すること。
2. 高度なアノテーションや試行錯誤が必要な実験的タスクには向かないため、作業内容をある程度定型的に切り出せるタスクに適用すること。
3. 答えが確定しているチェック問題を混ぜ、作業者間の一致度も確認するなど、複数の手がかりで品質を点検すること。不一致が多い場合は、作業者の回答だけでなく仕様の曖昧さも調べる。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと品質管理](notebooks/ch5_annotation.ipynb)（[Open in Colab](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)）

## 謝辞

練習問題の検討については東京都立大学システムデザイン学部情報科学科（当時）の長谷川諒さん、増子凱斗さん、江渡友美華さん、田中日加吏さん、そして自然言語処理研究室の皆さんにご協力いただきました。ありがとうございました。
