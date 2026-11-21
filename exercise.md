# 練習問題

## 1章

### 1

（回答例）

自然言語処理タスクの定義では、何を入力し、何を出力するかを決める。例えば、文書分類では文書を入力し、あらかじめ定めたカテゴリを出力する。英日機械翻訳では英語の文を入力し、日本語の訳文を出力する。

### 2

（回答例）

分類タスクでは、全事例のうち正しく分類した割合を正解率、正例と予測したうち実際に正例だった割合を適合率、実際の正例のうち検出できた割合を再現率という。F1 は適合率と再現率の調和平均である。誤検出と見逃しのどちらを重く見るかによって、重視する尺度が変わる。

生成タスクでは、機械翻訳の BLEU や要約の ROUGE のように、生成した文と参照文の重なりを測る尺度が使われる。機械翻訳の品質推定では、原文とシステムの訳文から、参照訳なしで品質スコアを予測する。品質推定モデルの性能は、例えば人手評価との順位相関で測れる。

- 関連ノートブック:
  - [分類タスクの評価尺度と閾値調整（Fβ・特異度・不均衡データ）](notebooks/ch1_evaluation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)
  - [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)
  - [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)

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
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)

### 5

（回答例）

従来のアプローチと比較した深層学習の欠点は以下の3つである。

1. ハルシネーションが起きる場合がある。
2. ハイパーパラメータの探索に時間がかかる。
3. 大規模モデルの学習には、多くのデータや GPU などの計算資源が必要になる。

- 関連ノートブック:
  - [自然言語処理システムの開発サイクル（文分割・データ分割・計算量・遠距離教師あり学習）](notebooks/ch1_design_cycle.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_design_cycle.ipynb)
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)

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

**ノートブックで確認**（CPU / GPU） — 評価極性分析の演習（第3節）で、混在レビューに対する文書一括判定 (ML) と文単位の辞書＋ルールのみ集約・ハイブリッド重みづけ集約を比べ、根拠文がどう特定されるか確認する。あわせて SVM・k-NN・ナイーブベイズの演習でラプラス平滑化 `alpha` (`1.0` vs `0.1` vs `1e-9`) による Log-Loss や対数尤度比の変化に加え、不均衡訓練データ（`TRUE` 60 件 vs `FALSE` 400 件）上で `MultinomialNB` の `TRUE` 再現率低下（TF-IDF `1-3gram, alpha=0.2` で `0.360`・Macro-F1 `0.643`）を `ComplementNB` がどう改善するか（`norm=False` で再現率 `0.700`・Macro-F1 `0.817`、TWCNB 構成では `norm=True` で再現率 `0.880`・Macro-F1 `0.840`）確かめる。さらに文章の品質推定演習で `LogisticRegression` の信頼度提示、線形 `SVR` の素性重みと寄与内訳、少データ (N=12) で過剰なファインチューニングが引き起こす過学習（未知 QWK `0.828` → `0.750`）と破壊的忘却（一般文意味類似度保持率 `0.869` → `0.097`）を確認し、同一テスト分割上で TF-IDF と日本語 BERT (v3) の誤分類事例を比べる。

### 2

（回答例）

多クラス分類問題は入力を複数あるクラスのどれか一つに分類する問題である。具体例としては、記事を「政治」「経済」「スポーツ」のいずれか一つに分類するタスクがある。

多ラベル分類問題は入力に対し複数あるラベルそれぞれについて分類する問題である（ラベルが n 個あれば 2^n 個の組み合わせがある）。具体例としては、同じ記事に「政治」と「スポーツ」を同時に付けるタスクがある。

- 関連ノートブック:
  - [多クラス分類と多ラベル分類（評価指標と訓練 CV による閾値選択）](notebooks/ch2_multilabel.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)

**ノートブックで確認**（CPU） — 多ラベル分類の演習で、Top-1 多クラス分類、標準閾値 `0.50`、訓練データの 4 分割 CV で選んだ閾値 `0.35` の結果を比べる。Subset Accuracy と Micro-F1 / Samples-F1 の差がなぜ開くか、複合トピック記事の予測確率表から説明する。

### 3

（回答例）

参照文を用いた評価はシステム出力の評価の根拠の検証が容易であるという利点があるが、参照文の数が少ない場合に必ずしも適切に評価できないという問題がある。

一方、参照文を用いない評価は参照文の品質やカバー率に左右されないという利点があるが、品質推定モデルが対象言語・分野で人手評価とどの程度一致するかを検証する必要がある。

- 関連ノートブック:
  - [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)
  - [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)

**ノートブックで確認**（CPU / GPU） — BLEU 演習（第3〜4節）で、シングルリファレンスとマルチリファレンスのスコア差や、言い換え・否定語挿入（`"not"`）に対する BLEU の挙動を確認する。続いて品質推定の演習で、開発データの Kendall と Spearman で選んだ XLM-R チェックポイントおよび COMET-QE の WMT22 テスト順位相関と、過大評価された翻訳事例を比べる。

### 4

（回答例）

- 分類問題: 入力にクラス（離散値）を割り当てる問題。多クラス分類では複数の候補から一つを選ぶ。
- 回帰問題: 入力に対し実数値を出力する問題。出力間の順序関係を用いてランキング問題に変換することができる。
- ランキング問題: 入力に対しランキングを出力する問題。順位だけではスコアの差や絶対値は決まらず、間隔尺度や比例尺度を仮定する必要がない。

- 関連ノートブック:
  - [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)
  - [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)

**ノートブックで確認**（CPU） — 順序尺度の演習（第3〜4節）で、多クラス分類、Ridge 回帰の四捨五入、訓練データ内の交差検証と累積割合から 5 段階の境界を決めた Ridge 回帰を比べ、QWK と Strict 正解率の違いを確認する。あわせてランキング演習（第3節）で、スコアを `{1: 1, 2: 2, 3: 10, 4: 40, 5: 100}` に変換した前後での Pointwise 回帰と Pairwise ランキングの順位一致率（τ）を確かめる。

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

**ノートブックで確認**（CPU / GPU） — 固有表現認識の基礎の演習（第2節）で BIO タグ単位 Macro-F1 とエンティティスパン完全一致の Precision / Recall / F1 を比べ、BERT による NER 演習（第4〜5節）で「すべて `O`」ベースラインのトークン正解率とエンティティ F1 の差や未知固有表現 (OOV) への汎化性能を確認する。あわせて形態素解析・サブワード分割の演習（第4節）で Subword Regularization の温度 `alpha` (`0.5` → `0.05`) による分割パターン数の増加（`4` → `19` 通り）を確かめ、Viterbi・仮名漢字変換・Pointwise 予測の演習（第2・4節）でバイグラム言語モデルによる同音異義語解消（「貴社の記者が汽車で帰社した」）および部分的アノテーション 10 文追加による専門複合語一致率の改善（`0.000` → `1.000`、境界 F1 `0.879` → `0.988`）と文脈依存の分割ゆれを確認する。

### 2

（回答例）

SVM や CRF などの機械学習手法で系列ラベリング問題を解く際に、モデル実行時にデータから動的に素性を展開するための仕組みである。すべての素性を人手で一つひとつ書き下すことなく、前後のトークンの表層形や品詞などを参照するユニグラム素性や、複数の素性を組み合わせたバイグラム（組合せ）素性などを簡潔に定義・抽出することができる。

- 関連ノートブック:
  - [固有表現認識の基礎（ガゼッティア・BIO タグ・素性テンプレートと CRF・サブワード整合）](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - [単語ラティス・仮名漢字変換・CRF vs MEMM・Pointwise 予測](notebooks/ch3_viterbi_crf.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)

**ノートブックで確認**（CPU） — 固有表現認識の基礎の演習（第2節）で、素性テンプレートを「表層形のみ」から「+品詞・文字種」「+前後文脈・バイグラム素性」へ段階的に増やしたときの未知固有表現の抽出精度と学習された遷移重みを比べる。あわせて Viterbi・CRF の演習（第3節）で、同一素性でも MEMM が `("新", "橋")` を誤り CRF が正しく識別できる理由を局所遷移確率と大域スコアから説明する。

### 3

（回答例）

入力の各単語に対して「保持」「削除」「追加」「置換」といった編集タグを出力する問題として定式化し、訓練データに一定回数以上出現した訂正候補に出力を絞ることで、適合率の高い訂正システムを構築できる（また、自己回帰モデルのように 1 単語ずつ生成する必要がないため高速に動作する）という利点がある。
一方、訓練データに出現しない未知の誤りや、大幅な語順の入れ替え・書き換えを伴う誤りを訂正しにくいため、再現率に課題があるという欠点がある。

- 関連ノートブック:
  - [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
  - [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)

**ノートブックで確認**（CPU / GPU） — 編集距離・言語モデルの演習（第4節）で、編集距離（通信路モデル）と単語バイグラム言語モデルを組み合わせたノイジーチャネルモデルにより、同距離候補の曖昧性解消や実単語誤り（`a` / `an`、`form` / `from`）がどう訂正されるか確認する。続いて Fast GECToR の演習で、開発データの ERRANT F0.5 に基づいて選んだチェックポイントと `--min_error_probability` 閾値が、従来設定（閾値 `0.3`）と比べてテストの Precision・Recall・F0.5 や見逃し・過剰訂正事例をどう変えるか確かめる。

## 4章

### 1

（回答例）

- テキスト平易化・言い換え（パラフレーズ生成）・文体変換: 言語は「同じ」、意味は「同じ」、長さは「固定しない」。
- 見出し生成（タイトル生成）: 言語は「同じ」、意味は「要点を保つ」、長さは「違う（短くなる）」。
- 質問応答・質問生成: 言語は「同じ」、意味は「違う」、長さは「違う（または同じ）」。
- クロスリンガル要約（異言語間要約）: 言語は「違う」、意味は「要点を保つ」、長さは「違う（短くなる）」。

- 関連ノートブック:
  - [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)

**ノートブックで確認**（CPU） — 文書要約の演習（第2〜4・6節）で、書籍 図 4.5 の ROUGE-1 (`0.500`)・ROUGE-L (`0.333`) 手計算検証と、ニュース型・後半結論型記事に対するリード法・TextRank・LexRank のスコア、さらに複数文抽出 (k=2) の重複を抑える MMR ($\lambda=0.6$) の効果を確認する。あわせて第6節で、忠実な言い換え抽象要約 (ROUGE-L `0.466`) より数値・極性を誤ったハルシネーション要約 (ROUGE-L `0.917`) のほうが高得点になる逆転現象と事実整合性検査の必要性を確かめる。

### 2

（回答例）

偽。系列変換タスクとはテキスト（単語列）を入力として別のテキスト（単語列）を出力するタスクのことであり、機械翻訳はその代表例である。統計的機械翻訳は機械翻訳を統計ベースのアプローチ（翻訳モデルと言語モデルの組み合わせ）で解く手法であり、系列変換タスクであることに変わりはない。

- 関連ノートブック:
  - [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)

**ノートブックで確認**（CPU / GPU） — 統計的機械翻訳の演習（第1節）で、IBM Model 1 が語順の異なる英日対訳から語彙翻訳確率 $t(f \mid e)$ を獲得する様子と、翻訳モデルと言語モデルの積で語順を決める仕組みを確認する。あわせて Eole 演習で開発データの BLEU に基づくチェックポイント選択（`step` 別の Dev BLEU 推移）と、テスト訳文の `<unk>` 出現率やワースト 10 文を確かめる。

### 3

（回答例）

深層学習による系列変換タスクの成功を支えた主な技術革新は以下の 3 つである。

1. エンコーダ・デコーダモデル：入力を処理するエンコーダと出力を 1 トークンずつ生成する自己回帰型のデコーダをニューラルネットワークで結合し、条件付き確率を直接推定することで、従来手法のようなつなぎ目の違和感がなく流暢なテキスト生成が可能になった。
2. アテンション機構と Transformer：出力生成時に入力のどの部分を参照するかを動的に重み付けするアテンション機構（クロスアテンション）により、長文でも妥当性の高い生成が可能になった。さらに自己アテンションを用いた Transformer により、長距離の文脈を考慮しつつ並列計算による大規模な学習が可能になった。
3. 自己教師あり学習と事前学習モデル：大規模な生テキストから自己教師あり学習によって構築された事前学習モデル（大規模言語モデル）により、対象タスクの大規模な教師データがなくても流暢で高精度なテキスト生成が可能になった。

- 関連ノートブック:
  - [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)

**ノートブックで確認**（CPU / GPU） — 要約演習（第5〜6節）で Pointer-Generator のコピー機構が OOV 固有表現・数値（`A社`・`栃木工場`・`5000万円` 等、コピー率 `0.868`〜`0.892`）を `<unk>` にせず補完する仕組みとカバレージ機構による反復抑制を確認し、あわせて第6節でハルシネーション検出の必要性を確かめる。続いて LLM プロンプト演習で、`phrase-annotation.csv` の残り 97 件に対するゼロショットと 3-shot のフォーマット遵守率・精度の違い、および根拠文書なしのハルシネーションと RAG 風プロンプトによる回答拒否・抑制を比べ、第4節でデコード戦略（Greedy Search・Beam Search `num_beams=4`・温度付き Top-p サンプリング）の違いを確認する。

## 5章

### 1

（回答例）

偽。日本の著作権法第30条の4では、情報解析などの非享受目的に必要な範囲で、著作権者の許諾なく利用できる場合がある。この規定は、著作権者の利益を不当に害する場合には適用されない。それ以外にも配慮すべき点がある。具体的には、言語資源やサービスのライセンス・利用規約（教育・研究目的限定で商用利用が不可である場合や、利用可能な組織の範囲が限定されている場合など）、個人情報やセンシティブなデータの保護、Web クローリング時の `robots.txt` によるアクセス制限やサーバ負荷といった技術的・道義的な問題、組織のコンプライアンスなどに配慮する必要がある。

- 関連ノートブック:
  - [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)

**ノートブックで確認**（CPU） — クレンジング演習（第3〜4節）で、近似重複を除去せずに分割した場合（条件 A）と除去後（条件 B）のテスト正解率の差からデータリークの影響を確認する。あわせて PII マスキングで `[CARD_OR_ID]`・`[PHONE]`・`[POSTAL]`・`[EMAIL]` を処理する順序や境界条件、および日本語比率・記号比率によるスパム除外の挙動を確かめる。

### 2

（回答例）

偽。複数の作業者が同じデータに対して独立にタグ付け（アノテーション）を行い、作業者間の一致率を測定することで、ラベル付けの一貫性を定量的に測ることができる。代表的な指標として、偶然に一致する割合を考慮して補正した Kappa 係数（2 人の場合は Cohen の Kappa、各項目に同じ人数が名義ラベルを付ける場合は Fleiss の Kappa）が広く用いられている。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - [機械学習によるコーパス品質管理と能動学習](notebooks/ch5_corpus_quality.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_corpus_quality.ipynb)

**ノートブックで確認**（CPU） — アノテーション演習（第2〜3節）で仕様書改訂前後の第1・第2ラウンドにおける Cohen の $\kappa$ を比べ、続いてコーパス品質管理と能動学習の演習（第1節・第3〜4節）で改訂前後のラベルで学習した分類器の未知データ精度、第3節の予測確率を用いたラベル誤り候補の絞り込み、第4節の能動学習（Least Confidence による不確実性サンプリング vs ランダムサンプリング）で同じ目標精度に要するラベル付け件数の違いを確認する。

### 3

（回答例）

クラウドソーシングを用いるときに気をつけるべき点は以下の 3 つである。

1. 作業者は自然言語処理の専門家ではなく個別の綿密なやりとりも難しいため、迷わず作業できるようタスク仕様や指示をわかりやすく設計すること。
2. 高度なアノテーションや試行錯誤が必要な実験的タスクには向かないため、作業内容をある程度定型的に切り出せるタスクに適用すること。
3. 真面目に作業しないスパマーが混じる可能性があるため、あらかじめ答えがわかっている問題を混ぜてチェックしたり、承認率が高い作業者に限定して依頼したりするなどの品質管理を行うこと。

- 関連ノートブック:
  - [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)

**ノートブックで確認**（CPU） — アノテーション演習（第4〜5節）で、チェック問題の正答率と他作業者との平均 $\kappa$ からスパマー（作業者 5）を除外した前後の Fleiss の $\kappa$ と多数決ラベル正解率の変化を確認する。あわせて欠損を含む疎な評価行列でも Krippendorff の $\alpha$ でスパマー除外の効果が定量評価できることを確かめる。

## 謝辞

練習問題の検討については東京都立大学システムデザイン学部情報科学科（当時）の長谷川諒さん、増子凱斗さん、江渡友美華さん、田中日加吏さん、そして自然言語処理研究室の皆さんにご協力いただきました。ありがとうございました。
