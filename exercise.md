# 練習問題

各練習問題の回答例に加えて、対応する演習ノートブックと、姉妹サイト [NLP クックブック](https://github.com/mamorlis/nlpcookbook) の関連レシピへのリンクを掲載しています。

## 1章

### 1

（回答例）

自然言語処理タスクの定義では、何を入力し、何を出力するかを決める。例えば、文書分類では文書を入力し、あらかじめ定めたカテゴリを出力する。英日機械翻訳では英語の文を入力し、日本語の訳文を出力する。

- 関連ノートブック:
  - [自然言語処理システムの開発サイクル（文分割・データ分割・計算量）](notebooks/ch1_design_cycle.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_design_cycle.ipynb)
  - [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)
- NLP クックブックの関連レシピ:
  - [1. データの収集と入出力](https://github.com/mamorlis/nlpcookbook#1-データの収集と入出力)：[データ分割 01-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/01_data_io/data_split.ipynb)
  - [3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)：[文分割 03-29](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sentence_split_ja.ipynb)
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[TF-IDF 12-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/tfidf_logreg_ja.ipynb)
  - [付録 A. Colab と Python の小技](https://github.com/mamorlis/nlpcookbook#付録-a-colab-と-python-の小技)：[日本語 matplotlib A-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/A_colab_python_tips/matplotlib_ja.ipynb)

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
- NLP クックブックの関連レシピ:
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[不均衡データ・しきい値調整 12-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/imbalanced.ipynb)
  - [14. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#14-評価指標と統計的検定)：[適合率・再現率・F1 14-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/prf_manual.ipynb)・[ブートストラップ信頼区間 14-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/bootstrap_ci.ipynb)・[統計的検定 14-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/significance_test.ipynb)・[自動評価と人手評価の相関 14-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/metric_correlation.ipynb)
  - [27. 機械翻訳](https://github.com/mamorlis/nlpcookbook#27-機械翻訳)：[品質推定 27-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_quality_estimation.ipynb)・[品質推定の学習 27-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_qe_train.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[適合率・再現率・F1 B-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/prf_scratch.ipynb)

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
- NLP クックブックの関連レシピ:
  - [21. 大規模言語モデル (LLM)](https://github.com/mamorlis/nlpcookbook#21-大規模言語モデル-llm)：[Few-shot プロンプト 21-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/21_llm/llm_few_shot.ipynb)

**ノートブックで確認** (GPU) — LLM プロンプトの演習で、事前学習済みモデルに自然言語の指示だけを与えるゼロショットと、3 件の例を添える few-shot で分類・要約・翻訳が動くことを確かめる。

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
- NLP クックブックの関連レシピ:
  - [17. 意味解析](https://github.com/mamorlis/nlpcookbook#17-意味解析)：[関係抽出 17-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/17_semantics/relation_extraction.ipynb)・[関係分類 17-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/17_semantics/relation_classification.ipynb)・[仮説だけからの含意予測（ショートカット学習） 17-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/17_semantics/nli_hypothesis_only.ipynb)
  - [18. 語の意味と意味の変化](https://github.com/mamorlis/nlpcookbook#18-語の意味と意味の変化)：[ブートストラッピング 18-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/18_lexical_semantics/bootstrapping.ipynb)・[意味ドリフト 18-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/18_lexical_semantics/semantic_drift.ipynb)
  - [21. 大規模言語モデル (LLM)](https://github.com/mamorlis/nlpcookbook#21-大規模言語モデル-llm)：[入力長と応答待ち時間の計測 21-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/21_llm/llm_prefill_decode.ipynb)

**ノートブックで確認** (CPU / GPU) — 半教師あり学習の演習で、確信度の閾値を下げると誤ったラベルが混ざってセマンティックドリフトが起きることを確かめ、遠距離教師あり学習で偶然の共起によるノイズを見る。TF-IDF ベースラインの演習で、テストデータを見ずに素性を設計し直しても、構成的な否定を含む誤りが最後まで残ることを確かめる。LLM プロンプトの演習で、根拠文書を与えないときにハルシネーションが起き、根拠文書を添えると抑えられることを確かめる。

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
- NLP クックブックの関連レシピ:
  - [6. 単語ベクトル](https://github.com/mamorlis/nlpcookbook#6-単語ベクトル)：[word2vec の学習 06-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/word2vec_train.ipynb)・[学習済みの日本語単語ベクトル 06-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/pretrained_vectors_ja.ipynb)・[単語ベクトルの可視化 06-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/word_vectors_viz.ipynb)・[単語類似度による評価 06-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/wordsim_eval.ipynb)・[対訳辞書による単語ベクトルの写像 06-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/cross_lingual_word_vectors.ipynb)
  - [8. Transformers の基本操作](https://github.com/mamorlis/nlpcookbook#8-transformers-の基本操作)：[文脈付き単語ベクトル 08-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/08_transformers/contextual_word_vectors.ipynb)
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[TF-IDF 12-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/tfidf_logreg_ja.ipynb)・[特徴量の重み 12-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/feature_importance.ipynb)・[エラー分析 12-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/error_analysis.ipynb)・[BERT 12-21](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/bert_finetune.ipynb)
  - [13. 感情分析と意見・有害表現の分析](https://github.com/mamorlis/nlpcookbook#13-感情分析と意見有害表現の分析)：[極性辞書 13-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/13_sentiment/sentiment_lexicon.ipynb)・[二重否定・婉曲・皮肉の極性判定 13-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/13_sentiment/implicit_sentiment_ja.ipynb)・[スタンス検出 13-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/13_sentiment/stance_detection_ja.ipynb)
  - [18. 語の意味と意味の変化](https://github.com/mamorlis/nlpcookbook#18-語の意味と意味の変化)：[慣用句・機能表現の検出 18-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/18_lexical_semantics/idiom_detection.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[PPMI+SVD B-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/ppmi_svd.ipynb)

**ノートブックで確認** (CPU / GPU) — 評価極性分析の演習で、複数文のレビューを文書単位でまとめて判定した場合と文単位に分けた場合を比べ、根拠となる文をどう特定できるかを確かめる。TF-IDF・SVM・BERT の演習では、同じテスト分割での誤分類事例を比べ、文書単位の分類器がどの表現に頼っているかを確かめる。

### 2

（回答例）

多クラス分類問題は入力を複数あるクラスのどれか一つに分類する問題である。具体例としては、記事を「政治」「経済」「スポーツ」のいずれか一つに分類するタスクがある。

多ラベル分類問題は入力に対し複数あるラベルそれぞれについて分類する問題である（ラベルが n 個あれば 2^n 個の組み合わせがある）。具体例としては、同じ記事に「政治」と「スポーツ」を同時に付けるタスクがある。

- 関連ノートブック:
  - [多クラス分類と多ラベル分類（評価指標と訓練 CV による閾値選択）](notebooks/ch2_multilabel.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)
- NLP クックブックの関連レシピ:
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[マルチラベル 12-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/multilabel.ipynb)

**ノートブックで確認** (CPU) — 多ラベル分類の演習で、Top-1 の多クラス分類と閾値による多ラベル分類を比べ、Subset Accuracy と Micro-F1 の差が開く理由を予測確率の表から説明する。ラベルの共起が強いときに Classifier Chains が効くことも確かめる。

### 3

（回答例）

参照文を用いた評価はシステム出力の評価の根拠の検証が容易であるという利点があるが、参照文の数が少ない場合に必ずしも適切に評価できないという問題がある。

一方、参照文を用いない評価は参照文の品質やカバー率に左右されないという利点があるが、品質推定モデルが対象言語・分野で人手評価とどの程度一致するかを検証する必要がある。

- 関連ノートブック:
  - [機械翻訳の自動評価（BLEU）と対訳コーパスのノイズフィルタリング](notebooks/ch4_bleu_corpus.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_bleu_corpus.ipynb)
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)
  - [機械翻訳の自動評価と人手評価の相関（BLEU・chrF・BERTScore・COMET・品質推定）](notebooks/ch4_mt_eval.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_mt_eval.ipynb)
- NLP クックブックの関連レシピ:
  - [14. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#14-評価指標と統計的検定)：[BERTScore 14-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/bertscore.ipynb)・[自動評価と人手評価の相関 14-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/metric_correlation.ipynb)
  - [27. 機械翻訳](https://github.com/mamorlis/nlpcookbook#27-機械翻訳)：[BLEU 27-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/bleu.ipynb)・[chrF・TER 27-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/chrf_ter.ipynb)・[COMET 27-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/comet.ipynb)・[品質推定 27-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_quality_estimation.ipynb)・[品質推定の学習 27-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_qe_train.ipynb)

**ノートブックで確認** (CPU / GPU) — BLEU の演習で、参照訳が 1 つの場合と複数の場合のスコアの差や、言い換え・否定に対する BLEU の挙動を確かめる。自動評価と人手評価の相関の演習で、参照訳を使う評価と品質推定の人手評価との相関を同じデータで比べ、参照訳を増やすと相関が上がることを確かめる。品質推定の演習では、人手評価との順位相関と大きく外した翻訳の事例を見る。

### 4

（回答例）

- 分類問題: 入力にクラス（離散値）を割り当てる問題。多クラス分類では複数の候補から一つを選ぶ。
- 回帰問題: 入力に対し実数値を出力する問題。出力間の順序関係を用いてランキング問題に変換することができる。
- ランキング問題: 入力に対しランキングを出力する問題。順位だけではスコアの差や絶対値は決まらず、間隔尺度や比例尺度を仮定する必要がない。

- 関連ノートブック:
  - [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)
  - [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)
- NLP クックブックの関連レシピ:
  - [19. 検索](https://github.com/mamorlis/nlpcookbook#19-検索)：[ランキング評価 19-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/19_search/ranking_metrics.ipynb)
  - [23. LLM の評価と分析](https://github.com/mamorlis/nlpcookbook#23-llm-の評価と分析)：[一対比較・Elo 23-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/23_llm_analysis/pairwise_judge_elo.ipynb)
  - [30. 言語教育・リーダビリティ・自動採点](https://github.com/mamorlis/nlpcookbook#30-言語教育リーダビリティ自動採点)：[自動採点・QWK 30-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/30_language_education/essay_scoring.ipynb)・[ルーブリック採点 30-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/30_language_education/rubric_scoring.ipynb)

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
- NLP クックブックの関連レシピ:
  - [3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)：[MeCab ユーザー辞書 03-17](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/mecab_userdic.ipynb)・[Sudachi の分割単位 03-18](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_split.ipynb)・[Sudachi ユーザー辞書 03-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_userdic.ipynb)・[KyTea 分野適応 03-26](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/kytea_train.ipynb)
  - [7. サブワードとトークナイザ](https://github.com/mamorlis/nlpcookbook#7-サブワードとトークナイザ)：[Subword Regularization 07-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/07_subword/subword_regularization.ipynb)・[word_ids 07-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/07_subword/word_ids.ipynb)
  - [16. 固有表現抽出](https://github.com/mamorlis/nlpcookbook#16-固有表現抽出)：[BIO タグへの変換 16-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/spans_to_bio.ipynb)・[BERT 16-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/bert_ner_finetune.ipynb)
  - [31. 日本語入力（かな漢字変換）](https://github.com/mamorlis/nlpcookbook#31-日本語入力かな漢字変換)：[ユニグラム変換 31-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/31_japanese_input/kkc_unigram.ipynb)・[バイグラム変換 31-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/31_japanese_input/kkc_bigram.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[HMM 品詞タガー B-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/hmm_tagger.ipynb)・[Viterbi B-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/viterbi.ipynb)

**ノートブックで確認** (CPU / GPU) — 固有表現認識の基礎の演習で、BIO タグ単位の評価とエンティティ単位の評価の違いを確かめ、BERT による NER の演習で、すべて `O` と予測するベースラインでもトークン正解率は高くなることを確かめる。形態素解析・Viterbi の演習では、単語分割や仮名漢字変換も系列ラベリング（またはラティス上の探索）として解けることを確かめる。

### 2

（回答例）

SVM や CRF などの機械学習手法で系列ラベリング問題を解く際に、モデル実行時にデータから動的に素性を展開するための仕組みである。すべての素性を人手で一つひとつ書き下すことなく、前後のトークンの表層形や品詞などを参照するユニグラム素性や、複数の素性を組み合わせたバイグラム（組合せ）素性などを簡潔に定義・抽出することができる。

- 関連ノートブック:
  - [固有表現認識の基礎（ガゼッティア・BIO タグ・素性テンプレートと CRF・サブワード整合）](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - [単語ラティス・仮名漢字変換・CRF vs MEMM・Pointwise 予測](notebooks/ch3_viterbi_crf.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)
- NLP クックブックの関連レシピ:
  - [16. 固有表現抽出](https://github.com/mamorlis/nlpcookbook#16-固有表現抽出)：[CRF 16-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/crf_tagger.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[MEMM vs CRF B-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/memm_vs_crf_scratch.ipynb)

**ノートブックで確認** (CPU) — 固有表現認識の基礎の演習で、素性テンプレートを段階的に増やしたときの抽出精度と学習された遷移重みを比べる。Viterbi・CRF の演習で、同じ素性でも MEMM が誤り CRF が正しく識別できる例を、局所的な遷移確率と大域的なスコアから説明する。

### 3

（回答例）

入力の各単語に対して「保持」「削除」「追加」「置換」といった編集タグを出力する問題として定式化し、訓練データに一定回数以上出現した訂正候補に出力を絞ることで、適合率の高い訂正システムを構築できる（また、自己回帰モデルのように 1 単語ずつ生成する必要がないため高速に動作する）という利点がある。
一方、訓練データに出現しない未知の誤りや、大幅な語順の入れ替え・書き換えを伴う誤りを訂正しにくいため、再現率に課題があるという欠点がある。

- 関連ノートブック:
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
  - [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)
- NLP クックブックの関連レシピ:
  - [2. 文字列処理と正規化](https://github.com/mamorlis/nlpcookbook#2-文字列処理と正規化)：[編集距離 02-24](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/02_string/edit_distance.ipynb)
  - [29. 文法誤り訂正と文章校正](https://github.com/mamorlis/nlpcookbook#29-文法誤り訂正と文章校正)：[編集抽出 29-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/edit_extraction.ipynb)・[ERRANT 29-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/errant.ipynb)・[M2 形式 29-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/m2_format.ipynb)・[GEC F0.5 評価 29-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/gec_f05.ipynb)・[スペル訂正 29-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/spelling_correction.ipynb)・[擬似誤りデータによる日本語 GEC の学習 29-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/gec_synthetic_train.ipynb)・[LLM による日本語の誤り訂正 29-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/gec_ja_llm.ipynb)・[マスク言語モデルによる誤り検出 29-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/ged_mlm.ipynb)・[日本語の校正 29-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/proofreading_ja.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[n-gram 言語モデル B-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/ngram_lm_scratch.ipynb)・[編集距離スペル訂正 B-25](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/spelling_correction_scratch.ipynb)

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
  - [19. 検索](https://github.com/mamorlis/nlpcookbook#19-検索)：[MMR 19-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/19_search/mmr_diversify.ipynb)
  - [20. 質問応答](https://github.com/mamorlis/nlpcookbook#20-質問応答)：[質問生成 20-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/20_qa/question_generation.ipynb)
  - [28. 要約と平易化](https://github.com/mamorlis/nlpcookbook#28-要約と平易化)：[LexRank 28-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/extractive_summary.ipynb)・[ROUGE 28-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/rouge_ja.ipynb)・[Lead-3 28-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/lead3_baseline.ipynb)・[事実整合性検査 28-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/summary_faithfulness.ipynb)・[見出し生成 28-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/headline_generation.ipynb)・[T5 による見出し生成 28-13](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/t5_finetune.ipynb)・[テキスト平易化 28-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/text_simplification.ipynb)・[語彙平易化 28-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/lexical_simplification.ipynb)・[文体変換 28-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/style_transfer_ja.ipynb)・[表からの文章生成 (data-to-text) 28-17](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/data_to_text.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[BLEU・ROUGE B-23](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/bleu_rouge_scratch.ipynb)・[TextRank・LexRank B-24](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/textrank_lexrank_scratch.ipynb)

**ノートブックで確認** (CPU) — 文書要約の演習で、抽出型要約の手法を ROUGE で比べ、ハルシネーションを含む要約のほうが忠実な言い換えより ROUGE が高くなる例から、意味の保ち方が違うタスクを表層の一致で評価する難しさを確かめる。

### 2

（回答例）

偽。系列変換タスクとはテキスト（単語列）を入力として別のテキスト（単語列）を出力するタスクのことであり、機械翻訳はその代表例である。統計的機械翻訳は機械翻訳を統計ベースのアプローチ（翻訳モデルと言語モデルの組み合わせ）で解く手法であり、系列変換タスクであることに変わりはない。

- 関連ノートブック:
  - [翻訳メモリと統計的機械翻訳の基礎（IBM Model 1・フレーズベース SMT）](notebooks/ch4_smt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt.ipynb)
  - [機械翻訳の自動評価（BLEU）と対訳コーパスのノイズフィルタリング](notebooks/ch4_bleu_corpus.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_bleu_corpus.ipynb)
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
- NLP クックブックの関連レシピ:
  - [27. 機械翻訳](https://github.com/mamorlis/nlpcookbook#27-機械翻訳)：[対訳コーパス 27-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/parallel_corpus.ipynb)・[BLEU 27-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/bleu.ipynb)・[chrF・TER 27-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/chrf_ter.ipynb)・[COMET 27-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/comet.ipynb)・[品質推定 27-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_quality_estimation.ipynb)・[Moses SMT 27-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/moses_smt.ipynb)・[NMT 27-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/nmt_from_scratch.ipynb)・[擬似対訳フィルタ 27-13](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/pseudo_parallel_filter.ipynb)・[用語集制約翻訳 27-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/terminology_constrained_translation.ipynb)・[LLM による翻訳 27-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/llm_translation.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[IBM Model 1 B-21](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/ibm_model1_scratch.ipynb)

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
- NLP クックブックの関連レシピ:
  - [8. Transformers の基本操作](https://github.com/mamorlis/nlpcookbook#8-transformers-の基本操作)：[デコード比較 08-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/08_transformers/generation_decoding.ipynb)
  - [9. 言語モデルの確率と内部を調べる](https://github.com/mamorlis/nlpcookbook#9-言語モデルの確率と内部を調べる)：[アテンションの可視化 09-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/09_lm_analysis/attention_viz.ipynb)
  - [21. 大規模言語モデル (LLM)](https://github.com/mamorlis/nlpcookbook#21-大規模言語モデル-llm)：[Few-shot プロンプト 21-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/21_llm/llm_few_shot.ipynb)・[ツール呼び出し 21-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/21_llm/llm_tool_calling.ipynb)
  - [23. LLM の評価と分析](https://github.com/mamorlis/nlpcookbook#23-llm-の評価と分析)：[一対比較・Elo 23-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/23_llm_analysis/pairwise_judge_elo.ipynb)
  - [24. LLM の学習と調整](https://github.com/mamorlis/nlpcookbook#24-llm-の学習と調整)：[タスク算術とモデルマージ 24-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/24_llm_training/task_arithmetic_merge.ipynb)
  - [25. RAG（検索拡張生成）](https://github.com/mamorlis/nlpcookbook#25-rag検索拡張生成)：[最小の RAG 25-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_minimal.ipynb)・[質問書き換え 25-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_query_rewrite.ipynb)・[出典検証 25-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_citation.ipynb)・[回答拒否 25-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_refusal.ipynb)・[エージェント型 RAG 25-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_agent.ipynb)
  - [26. 対話システム](https://github.com/mamorlis/nlpcookbook#26-対話システム)：[スロットフィリング 26-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/slot_filling.ipynb)・[対話状態追跡の評価 26-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/dst_eval.ipynb)・[対話履歴の管理 26-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/chat_history.ipynb)・[ペルソナ 26-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/persona_prompt.ipynb)・[複数ターンの RAG 26-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/chat_rag.ipynb)・[ガードレール 26-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/dialogue_guardrail.ipynb)・[対話評価 26-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/dialogue_eval.ipynb)・[音声対話 26-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/voice_dialogue.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[ELIZA 方式 B-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/eliza_rule.ipynb)

**ノートブックで確認** (CPU / GPU) — 要約の演習で、Pointer-Generator のコピー機構が未知の固有表現や数値を補う仕組みを確かめる。対話システムの演習で、RAG による知識接地型の対話を確かめ、第 7 節では事前学習済みの LLM による生成ベースの応答を用例検索型・テンプレート型と比べて、流暢さとハルシネーションの関係を見る。LLM プロンプトの演習で、ゼロショットと few-shot の違いやデコード戦略の違いを確かめる。

## 5章

### 1

（回答例）

偽。日本の著作権法第30条の4では、情報解析などの非享受目的に必要な範囲で、著作権者の許諾なく利用できる場合がある。この規定は、著作権者の利益を不当に害する場合には適用されない。それ以外にも配慮すべき点がある。具体的には、言語資源やサービスのライセンス・利用規約（教育・研究目的限定で商用利用が不可である場合や、利用可能な組織の範囲が限定されている場合など）、個人情報やセンシティブなデータの保護、Web クローリング時の `robots.txt` によるアクセス制限やサーバ負荷といった技術的・道義的な問題、組織のコンプライアンスなどに配慮する必要がある。

- 関連ノートブック:
  - [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)
- NLP クックブックの関連レシピ:
  - [1. データの収集と入出力](https://github.com/mamorlis/nlpcookbook#1-データの収集と入出力)：[重複除去 01-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/01_data_io/dedup_clean.ipynb)
  - [2. 文字列処理と正規化](https://github.com/mamorlis/nlpcookbook#2-文字列処理と正規化)：[NFKC 02-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/02_string/nfkc.ipynb)
  - [16. 固有表現抽出](https://github.com/mamorlis/nlpcookbook#16-固有表現抽出)：[PII マスク 16-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/pii_mask.ipynb)

**ノートブックで確認** (CPU) — クレンジングの演習で、近似重複を除かずにデータを分割したときのデータリークの影響を確かめ、個人情報 (PII) のマスキングとスパムの除外の挙動を確かめる。

### 2

（回答例）

偽。複数の作業者が同じデータに対して独立にタグ付け（アノテーション）を行い、作業者間の一致率を測定することで、ラベル付けの一貫性を定量的に測ることができる。代表的な指標として、偶然に一致する割合を考慮して補正した Kappa 係数（2 人の場合は Cohen の Kappa、各項目に同じ人数が名義ラベルを付ける場合は Fleiss の Kappa）が広く用いられている。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - [機械学習によるコーパス品質管理と能動学習](notebooks/ch5_corpus_quality.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_corpus_quality.ipynb)
- NLP クックブックの関連レシピ:
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[学習曲線 12-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/learning_curve.ipynb)・[能動学習 12-17](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/active_learning.ipynb)・[ラベル誤り検出 12-19](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/label_noise.ipynb)
  - [14. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#14-評価指標と統計的検定)：[一致度 14-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/agreement.ipynb)

**ノートブックで確認** (CPU) — アノテーションの演習で、仕様書の改訂前後で Cohen の $\kappa$ がどう変わるかを確かめる。コーパス品質管理の演習で、改訂前後のラベルで学習した分類器の比較、予測確率によるラベル誤りの候補の抽出、能動学習によるラベル付けの効率化を確かめる。

### 3

（回答例）

クラウドソーシングを用いるときに気をつけるべき点は以下の 3 つである。

1. 作業者は自然言語処理の専門家ではなく個別の綿密なやりとりも難しいため、迷わず作業できるようタスク仕様や指示をわかりやすく設計すること。
2. 高度なアノテーションや試行錯誤が必要な実験的タスクには向かないため、作業内容をある程度定型的に切り出せるタスクに適用すること。
3. 真面目に作業しないスパマーが混じる可能性があるため、あらかじめ答えがわかっている問題を混ぜてチェックしたり、承認率が高い作業者に限定して依頼したりするなどの品質管理を行うこと。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
- NLP クックブックの関連レシピ:
  - [14. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#14-評価指標と統計的検定)：[一致度 14-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/agreement.ipynb)

**ノートブックで確認** (CPU) — アノテーションの演習で、チェック問題の正答率と他の作業者との一致率からスパマーを見つけ、除外の前後で Fleiss の $\kappa$ と多数決ラベルの正解率がどう変わるかを確かめる。欠損を含む評価行列でも、Krippendorff の $\alpha$ で効果を測れることを確かめる。

### 書籍 5-3 節（辞書作成）の関連ノートブック

- 関連ノートブック:
  - [形態素解析のユーザ辞書作成と単体テスト](notebooks/ch5_dictionary.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_dictionary.ipynb)
- NLP クックブックの関連レシピ:
  - [3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)：[専門用語抽出 03-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/term_extraction.ipynb)・[MeCab ユーザー辞書 03-17](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/mecab_userdic.ipynb)・[Sudachi 正規化 03-19](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_normalize.ipynb)・[Sudachi ユーザー辞書 03-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_userdic.ipynb)・[Janome ユーザー辞書 03-22](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/janome_userdic.ipynb)

**ノートブックで確認** (CPU) — ユーザ辞書の演習で、誤った分割や表記ゆれをユーザ辞書で直し、単体テストで確かめる。分野コーパスと背景コーパスの比較（PMI と対数尤度比）で専門用語の候補を自動で抽出して辞書に登録すると、未知の評価文の分割が改善し、既存のテストにも回帰がないことを確かめる。

### 書籍 5-5 節（パイプラインと高速化）の関連ノートブック

- 関連ノートブック:
  - [パイプライン処理のモジュール分割と前後処理・デバッグ](notebooks/ch5_toolkit_pipeline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_pipeline.ipynb)
  - [パイプラインの高速化・スケーラビリティとボトルネック計測](notebooks/ch5_toolkit_benchmark.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_benchmark.ipynb)
- NLP クックブックの関連レシピ:
  - [付録 A. Colab と Python の小技](https://github.com/mamorlis/nlpcookbook#付録-a-colab-と-python-の小技)：[処理時間計測 A-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/A_colab_python_tips/timing.ipynb)・[JSON Lines 入出力 A-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/A_colab_python_tips/jsonl_io.ipynb)・[巨大ファイルのストリーム処理 A-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/A_colab_python_tips/large_file_stream.ipynb)

**ノートブックで確認** (CPU) — パイプライン分割の演習で、モジュールの差し替え、前処理・後処理のアブレーション、中間出力の差分による原因の特定、回帰テストによる検出を確かめる。高速化の演習で、プロセス起動のコスト、行列積の実装による速度の違い、アムダールの法則に基づく段階的な高速化を確かめる。

## 謝辞

練習問題の検討については東京都立大学システムデザイン学部情報科学科（当時）の長谷川諒さん、増子凱斗さん、江渡友美華さん、田中日加吏さん、そして自然言語処理研究室の皆さんにご協力いただきました。ありがとうございました。
