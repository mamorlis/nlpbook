# 練習問題

## 1章

### 1

（回答例）

自然言語処理タスクの定義では、何を入力し、何を出力するかを決める。例えば、文書分類では文書を入力し、あらかじめ定めたカテゴリを出力する。英日機械翻訳では英語の文を入力し、日本語の訳文を出力する。

- 関連ノートブック:
  - [自然言語処理システムの開発サイクル（文分割・データ分割・計算量）](notebooks/ch1_design_cycle.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_design_cycle.ipynb)
  - [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)

**ノートブックで確認** (CPU) — 開発サイクルの演習で、入力と出力を決めたあとの前処理（文分割）とデータの分け方を確かめ、TF-IDF ベースラインの演習で、文書を入力してカテゴリを出力する文書分類を最小の構成で動かす。

### 2

（回答例）

分類タスクでは、全事例のうち正しく分類した割合を正解率、正例と予測したうち実際に正例だった割合を適合率、実際の正例のうち検出できた割合を再現率という。F1 は適合率と再現率の調和平均である。誤検出と見逃しのどちらを重く見るかによって、重視する尺度が変わる。

生成タスクでは、機械翻訳の BLEU や要約の ROUGE のように、生成した文と参照文の重なりを測る尺度が使われる。機械翻訳の品質推定では、原文とシステムの訳文から、参照訳なしで品質スコアを予測する。品質推定モデルの性能は、例えば人手評価との順位相関で測れる。

- 関連ノートブック:
  - [分類タスクの評価尺度と閾値調整（Fβ・特異度・不均衡データ・統計的有意差検定）](notebooks/ch1_evaluation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)
  - [機械翻訳の自動評価（BLEU）と対訳コーパスのノイズフィルタリング](notebooks/ch4_bleu_corpus.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_bleu_corpus.ipynb)
  - [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)
  - [機械翻訳の自動評価と人手評価の相関（BLEU・chrF・BERTScore・COMET・品質推定）](notebooks/ch4_mt_eval.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_mt_eval.ipynb)

**ノートブックで確認** (CPU / GPU) — 分類評価の演習で、閾値を変えたときの適合率と再現率の変化から、見逃しを減らしたい場合にどの閾値を選ぶかを説明し、2 つのシステムの差が有意かどうかを McNemar 検定とブートストラップ法で確かめる。自動評価と人手評価の相関の演習で、BLEU などの参照訳を使う尺度と品質推定が、人手評価とどの程度一致するかを比べる。

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
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)

### 5

（回答例）

従来のアプローチと比較した深層学習の欠点は以下の3つである。

1. ハルシネーションが起きる場合がある。
2. ハイパーパラメータの探索に時間がかかる。
3. 大規模モデルの学習には、多くのデータや GPU などの計算資源が必要になる。

- 関連ノートブック:
  - [半教師あり学習と遠距離教師あり学習（Yarowsky・共訓練・マルチインスタンス集約）](notebooks/ch1_semisupervised.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_semisupervised.ipynb)
  - [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)

**ノートブックで確認** (CPU) — 半教師あり学習の演習で、確信度の閾値を下げると誤ったラベルが混ざってセマンティックドリフトが起きることを確かめ、遠距離教師あり学習で偶然の共起によるノイズを見る。TF-IDF ベースラインの演習で、テストデータを見ずに素性を設計し直しても、構成的な否定を含む誤りが最後まで残ることを確かめる。

## 2章

### 1

（回答例）

文を対象とする場合は文法情報や意味情報などの細かい粒度の言語情報を用いた解析ができるという利点がある。一方、機械学習のアプローチを取る場合は、文単位でアノテーションされた訓練データが必要になる。

文書を対象とする場合は文書単位でアノテーションされたデータが容易に入手可能であるという利点がある。一方、具体的にどの部分が予測に寄与しているのかの根拠となる表現を分析しにくい。

- 関連ノートブック:
  - [評価極性辞書と文単位・文書単位の極性分析](notebooks/ch2_sentiment_lexicon.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)
  - [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)
  - [SVM カーネル（線形 vs RBF）・k 近傍法・ナイーブベイズによる文書分類と根拠分析](notebooks/ch2_svm_knn.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_svm_knn.ipynb)
  - [文章の品質推定と解釈可能なシステム設計（接続表現ハイライト・線形モデルの根拠提示・特徴量ベース vs 微調整）](notebooks/ch2_writing_quality.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_writing_quality.ipynb)
  - [単語埋め込み（分散表現）と文脈付き埋め込みの比較](notebooks/ch2_word_embeddings.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_word_embeddings.ipynb)
  - [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)

**ノートブックで確認** (CPU / GPU) — 評価極性分析の演習で、複数文のレビューを文書単位でまとめて判定した場合と文単位に分けた場合を比べ、根拠となる文をどう特定できるかを確かめる。TF-IDF・SVM・BERT の演習では、同じテスト分割での誤分類事例を比べ、文書単位の分類器がどの表現に頼っているかを確かめる。

### 2

（回答例）

多クラス分類問題は入力を複数あるクラスのどれか一つに分類する問題である。具体例としては、記事を「政治」「経済」「スポーツ」のいずれか一つに分類するタスクがある。

多ラベル分類問題は入力に対し複数あるラベルそれぞれについて分類する問題である（ラベルが n 個あれば 2^n 個の組み合わせがある）。具体例としては、同じ記事に「政治」と「スポーツ」を同時に付けるタスクがある。

- 関連ノートブック:
  - [多クラス分類と多ラベル分類（評価指標と訓練 CV による閾値選択）](notebooks/ch2_multilabel.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)

**ノートブックで確認** (CPU) — 多ラベル分類の演習で、Top-1 の多クラス分類と閾値による多ラベル分類を比べ、Subset Accuracy と Micro-F1 の差が開く理由を予測確率の表から説明する。ラベルの共起が強いときに Classifier Chains が効くことも確かめる。

### 3

（回答例）

参照文を用いた評価はシステム出力の評価の根拠の検証が容易であるという利点があるが、参照文の数が少ない場合に必ずしも適切に評価できないという問題がある。

一方、参照文を用いない評価は参照文の品質やカバー率に左右されないという利点があるが、品質推定モデルが対象言語・分野で人手評価とどの程度一致するかを検証する必要がある。

- 関連ノートブック:
  - [機械翻訳の自動評価（BLEU）と対訳コーパスのノイズフィルタリング](notebooks/ch4_bleu_corpus.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_bleu_corpus.ipynb)
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)
  - [機械翻訳の自動評価と人手評価の相関（BLEU・chrF・BERTScore・COMET・品質推定）](notebooks/ch4_mt_eval.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_mt_eval.ipynb)

**ノートブックで確認** (CPU / GPU) — BLEU の演習で、参照訳が 1 つの場合と複数の場合のスコアの差や、言い換え・否定に対する BLEU の挙動を確かめる。自動評価と人手評価の相関の演習で、参照訳を使う評価と品質推定の人手評価との相関を同じデータで比べ、参照訳を増やすと相関が上がることを確かめる。品質推定の演習では、人手評価との順位相関と大きく外した翻訳の事例を見る。

### 4

（回答例）

- 分類問題: 入力にクラス（離散値）を割り当てる問題。多クラス分類では複数の候補から一つを選ぶ。
- 回帰問題: 入力に対し実数値を出力する問題。出力間の順序関係を用いてランキング問題に変換することができる。
- ランキング問題: 入力に対しランキングを出力する問題。順位だけではスコアの差や絶対値は決まらず、間隔尺度や比例尺度を仮定する必要がない。

- 関連ノートブック:
  - [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)
  - [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)

**ノートブックで確認** (CPU) — 順序尺度の演習で、多クラス分類・回帰の四捨五入・境界を調整した回帰を比べ、QWK と Strict 正解率の違いを確かめる。ランキングの演習で、スコアを単調に変換しても Pairwise ランキングの順位が変わらないことを確かめる。

## 3章

### 1

（回答例）

系列ラベリングタスクは、文字や単語などのリスト（系列）を入力とし、そのそれぞれの要素に対してラベルを出力するタスクである。
具体例としては、単語列を入力として各単語に人名や組織名などの固有表現タグ（BIO タグなど）を出力する固有表現認識、文字列や単語列を入力として単語境界ラベルや品詞ラベルを出力する形態素解析（単語分割・品詞推定）、単語列を入力として各単語に対する正誤ラベルや編集操作ラベル（保持・削除・追加・置換）を出力する文法誤り検出・訂正などがある。

- 関連ノートブック:
  - [固有表現認識の基礎（ガゼッティア・BIO タグ・素性テンプレートと CRF・サブワード整合）](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - [BERT による固有表現認識（Token Classification）](notebooks/ch3_bert_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_bert_ner.ipynb)
  - [形態素解析とサブワード分割（分割単位・正規化・未知語処理・Subword Regularization）](notebooks/ch3_morphology_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)
  - [単語ラティス・仮名漢字変換・CRF vs MEMM・Pointwise 予測](notebooks/ch3_viterbi_crf.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)

**ノートブックで確認** (CPU / GPU) — 固有表現認識の基礎の演習で、BIO タグ単位の評価とエンティティ単位の評価の違いを確かめ、BERT による NER の演習で、すべて `O` と予測するベースラインでもトークン正解率は高くなることを確かめる。形態素解析・Viterbi の演習では、単語分割や仮名漢字変換も系列ラベリング（またはラティス上の探索）として解けることを確かめる。

### 2

（回答例）

SVM や CRF などの機械学習手法で系列ラベリング問題を解く際に、モデル実行時にデータから動的に素性を展開するための仕組みである。すべての素性を人手で一つひとつ書き下すことなく、前後のトークンの表層形や品詞などを参照するユニグラム素性や、複数の素性を組み合わせたバイグラム（組合せ）素性などを簡潔に定義・抽出することができる。

- 関連ノートブック:
  - [固有表現認識の基礎（ガゼッティア・BIO タグ・素性テンプレートと CRF・サブワード整合）](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - [単語ラティス・仮名漢字変換・CRF vs MEMM・Pointwise 予測](notebooks/ch3_viterbi_crf.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)

**ノートブックで確認** (CPU) — 固有表現認識の基礎の演習で、素性テンプレートを段階的に増やしたときの抽出精度と学習された遷移重みを比べる。Viterbi・CRF の演習で、同じ素性でも MEMM が誤り CRF が正しく識別できる例を、局所的な遷移確率と大域的なスコアから説明する。

### 3

（回答例）

入力の各単語に対して「保持」「削除」「追加」「置換」といった編集タグを出力する問題として定式化し、訓練データに一定回数以上出現した訂正候補に出力を絞ることで、適合率の高い訂正システムを構築できる（また、自己回帰モデルのように 1 単語ずつ生成する必要がないため高速に動作する）という利点がある。
一方、訓練データに出現しない未知の誤りや、大幅な語順の入れ替え・書き換えを伴う誤りを訂正しにくいため、再現率に課題があるという欠点がある。

- 関連ノートブック:
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
  - [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)

**ノートブックで確認** (CPU / GPU) — 編集距離・言語モデルの演習で、雑音のある通信路モデルによる訂正と、編集単位の F0.5 評価（何も直さないベースラインや過剰訂正の扱い、参照訂正の数の影響）を確かめる。Fast GECToR の演習で、誤り検出の閾値を変えると適合率と再現率がどう変わるかと、見逃しと過剰訂正の事例を確かめる。後半の節では、誤りタイプ別の再現率（語順 R:WO は 0.05 程度）と、編集タグ 1 回で表せない正解の編集（約 12%）がほとんど直せないことを確かめ、回答例の「再現率に課題がある」理由を考える。語順の誤りは 2 つのタグで表せることが多いが、離れた位置のタグを両方当てる必要があるため直しにくい。

## 4章

### 1

（回答例）

- テキスト平易化・言い換え（パラフレーズ生成）・文体変換: 言語は「同じ」、意味は「同じ」、長さは「固定しない」。
- 見出し生成（タイトル生成）: 言語は「同じ」、意味は「要点を保つ」、長さは「違う（短くなる）」。
- 質問応答・質問生成: 言語は「同じ」、意味は「違う」、長さは「違う（または同じ）」。
- クロスリンガル要約（異言語間要約）: 言語は「違う」、意味は「要点を保つ」、長さは「違う（短くなる）」。

- 関連ノートブック:
  - [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
- NLP クックブックの関連レシピ:
  - [20. 質問応答](https://github.com/mamorlis/nlpcookbook#20-質問応答)：[質問生成 20-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/20_qa/question_generation.ipynb)
  - [28. 要約と平易化](https://github.com/mamorlis/nlpcookbook#28-要約と平易化)：[見出し生成 28-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/headline_generation.ipynb)・[T5 による見出し生成 28-13](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/t5_finetune.ipynb)・[テキスト平易化 28-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/text_simplification.ipynb)・[語彙平易化 28-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/lexical_simplification.ipynb)・[文体変換 28-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/style_transfer_ja.ipynb)

**ノートブックで確認** (CPU) — 文書要約の演習で、抽出型要約の手法を ROUGE で比べ、ハルシネーションを含む要約のほうが忠実な言い換えより ROUGE が高くなる例から、意味の保ち方が違うタスクを表層の一致で評価する難しさを確かめる。

### 2

（回答例）

偽。系列変換タスクとはテキスト（単語列）を入力として別のテキスト（単語列）を出力するタスクのことであり、機械翻訳はその代表例である。統計的機械翻訳は機械翻訳を統計ベースのアプローチ（翻訳モデルと言語モデルの組み合わせ）で解く手法であり、系列変換タスクであることに変わりはない。

- 関連ノートブック:
  - [翻訳メモリと統計的機械翻訳の基礎（IBM Model 1・フレーズベース SMT）](notebooks/ch4_smt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt.ipynb)
  - [機械翻訳の自動評価（BLEU）と対訳コーパスのノイズフィルタリング](notebooks/ch4_bleu_corpus.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_bleu_corpus.ipynb)
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)

**ノートブックで確認** (CPU / GPU) — 統計的機械翻訳の演習で、IBM Model 1 で語彙の翻訳確率を学習し、翻訳モデルと言語モデルを組み合わせたフレーズベース SMT で語順の違う訳文を作る。BLEU・コーパスの演習で対訳のノイズを取り除くと単語アライメントが改善することを確かめ、Eole の演習でニューラル機械翻訳の訓練と評価を一通り行う。

### 3

（回答例）

深層学習による系列変換タスクの成功を支えた主な技術革新は以下の 3 つである。

1. エンコーダ・デコーダモデル：入力を処理するエンコーダと出力を 1 トークンずつ生成する自己回帰型のデコーダをニューラルネットワークで結合し、条件付き確率を直接推定することで、従来手法のようなつなぎ目の違和感がなく流暢なテキスト生成が可能になった。
2. アテンション機構と Transformer：出力生成時に入力のどの部分を参照するかを動的に重み付けするアテンション機構（クロスアテンション）により、長文でも妥当性の高い生成が可能になった。さらに自己アテンションを用いた Transformer により、長距離の文脈を考慮しつつ並列計算による大規模な学習が可能になった。
3. 自己教師あり学習と事前学習モデル：大規模な生テキストから自己教師あり学習によって構築された事前学習モデル（大規模言語モデル）により、対象タスクの大規模な教師データがなくても流暢で高精度なテキスト生成が可能になった。

- 関連ノートブック:
  - [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - [対話システムの基礎（ルールベース・検索型・タスク指向対話・検索拡張生成 RAG・評価・生成ベース）](notebooks/ch4_dialogue.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_dialogue.ipynb)
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)

**ノートブックで確認** (CPU / GPU) — 要約の演習で、Pointer-Generator のコピー機構が未知の固有表現や数値を補う仕組みを確かめる。対話システムの演習で、RAG による知識接地型の対話を確かめ、第 7 節では事前学習済みの LLM による生成ベースの応答を用例検索型・テンプレート型と比べて、流暢さとハルシネーションの関係を見る。LLM プロンプトの演習で、ゼロショットと few-shot の違いやデコード戦略の違いを確かめる。

## 5章

### 1

（回答例）

偽。日本の著作権法第30条の4では、情報解析などの非享受目的に必要な範囲で、著作権者の許諾なく利用できる場合がある。この規定は、著作権者の利益を不当に害する場合には適用されない。それ以外にも配慮すべき点がある。具体的には、言語資源やサービスのライセンス・利用規約（教育・研究目的限定で商用利用が不可である場合や、利用可能な組織の範囲が限定されている場合など）、個人情報やセンシティブなデータの保護、Web クローリング時の `robots.txt` によるアクセス制限やサーバ負荷といった技術的・道義的な問題、組織のコンプライアンスなどに配慮する必要がある。

- 関連ノートブック:
  - [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)

**ノートブックで確認** (CPU) — クレンジングの演習で、近似重複を除かずにデータを分割したときのデータリークの影響を確かめ、個人情報 (PII) のマスキングとスパムの除外の挙動を確かめる。

### 2

（回答例）

偽。複数の作業者が同じデータに対して独立にタグ付け（アノテーション）を行い、作業者間の一致率を測定することで、ラベル付けの一貫性を定量的に測ることができる。代表的な指標として、偶然に一致する割合を考慮して補正した Kappa 係数（2 人の場合は Cohen の Kappa、各項目に同じ人数が名義ラベルを付ける場合は Fleiss の Kappa）が広く用いられている。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - [機械学習によるコーパス品質管理と能動学習](notebooks/ch5_corpus_quality.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_corpus_quality.ipynb)

**ノートブックで確認** (CPU) — アノテーションの演習で、仕様書の改訂前後で Cohen の $\kappa$ がどう変わるかを確かめる。コーパス品質管理の演習で、改訂前後のラベルで学習した分類器の比較、予測確率によるラベル誤りの候補の抽出、能動学習によるラベル付けの効率化を確かめる。

### 3

（回答例）

クラウドソーシングを用いるときに気をつけるべき点は以下の 3 つである。

1. 作業者は自然言語処理の専門家ではなく個別の綿密なやりとりも難しいため、迷わず作業できるようタスク仕様や指示をわかりやすく設計すること。
2. 高度なアノテーションや試行錯誤が必要な実験的タスクには向かないため、作業内容をある程度定型的に切り出せるタスクに適用すること。
3. 真面目に作業しないスパマーが混じる可能性があるため、あらかじめ答えがわかっている問題を混ぜてチェックしたり、承認率が高い作業者に限定して依頼したりするなどの品質管理を行うこと。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)

**ノートブックで確認** (CPU) — アノテーションの演習で、チェック問題の正答率と他の作業者との一致率からスパマーを見つけ、除外の前後で Fleiss の $\kappa$ と多数決ラベルの正解率がどう変わるかを確かめる。欠損を含む評価行列でも、Krippendorff の $\alpha$ で効果を測れることを確かめる。

### 書籍 5-3 節（辞書作成）の関連ノートブック

- 関連ノートブック:
  - [形態素解析のユーザ辞書作成と単体テスト](notebooks/ch5_dictionary.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_dictionary.ipynb)

**ノートブックで確認** (CPU) — ユーザ辞書の演習で、誤った分割や表記ゆれをユーザ辞書で直し、単体テストで確かめる。分野コーパスと背景コーパスの比較（PMI と対数尤度比）で専門用語の候補を自動で抽出して辞書に登録すると、未知の評価文の分割が改善し、既存のテストにも回帰がないことを確かめる。

### 書籍 5-5 節（パイプラインと高速化）の関連ノートブック

- 関連ノートブック:
  - [パイプライン処理のモジュール分割と前後処理・デバッグ](notebooks/ch5_toolkit_pipeline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_pipeline.ipynb)
  - [パイプラインの高速化・スケーラビリティとボトルネック計測](notebooks/ch5_toolkit_benchmark.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_benchmark.ipynb)

**ノートブックで確認** (CPU) — パイプライン分割の演習で、モジュールの差し替え、前処理・後処理のアブレーション、中間出力の差分による原因の特定、回帰テストによる検出を確かめる。高速化の演習で、プロセス起動のコスト、行列積の実装による速度の違い、アムダールの法則に基づく段階的な高速化を確かめる。

## 謝辞

練習問題の検討については東京都立大学システムデザイン学部情報科学科（当時）の長谷川諒さん、増子凱斗さん、江渡友美華さん、田中日加吏さん、そして自然言語処理研究室の皆さんにご協力いただきました。ありがとうございました。
