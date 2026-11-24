# 自然言語処理の教科書
小町守「自然言語処理の教科書」（技術評論社）のサポートサイトです。

姉妹サイトとして、自然言語処理の「やりたいこと」に対して「こうやればいい」をまとめた Google Colab ノートブック集 [NLP クックブック](https://github.com/mamorlis/nlpcookbook) も公開しています。本書で扱っている前処理・形態素解析・テキスト分類・固有表現抽出・文法誤り訂正・機械翻訳・要約・対話などの実装レシピも多数収録していますので、あわせてご活用ください。

## 演習

書籍の第2章から第5章にある演習の節（2-4・3-4・4-4・5-6）のノートブックに加えて、第1章から第5章の内容を手を動かして確かめる補足の演習ノートブックを用意しています。各ノートブックの説明の先頭に対応する書籍の節を示し、書籍の演習の節に対応するものには「演習：…」と節の題名を添えています。

ノートブック名をクリックすると GitHub 上で閲覧でき、「Open in Colab」をクリックすると Google Colab で直接実行できます。GPU 演習を含む全 32 本のノートブックに整理済みの実行結果を埋め込んでいるため、GitHub 上でも出力結果までそのまま読めます。

- **CPU** — Colab の標準ランタイムで実行できます。初めての方は、第1章の [分類タスクの評価尺度と閾値調整](notebooks/ch1_evaluation.ipynb) から始められます。
- **GPU 推奨** — CPU でも動く設定がありますが、学習や推論に時間がかかります。
- **GPU 必須** — ノートブックの設定で GPU を使用します。

GPU を使う場合は、Colab の「ランタイム」→「ランタイムのタイプを変更」で、ハードウェア アクセラレータに GPU（T4 など）を選んでください。

### 第1章

- **CPU** · [分類タスクの評価尺度と閾値調整（Fβ・特異度・不均衡データ・統計的有意差検定）](notebooks/ch1_evaluation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)
  - 最終確認 2026/11/23
  - （書籍 1-4）正解率・適合率・再現率・特異度・F 値を定義式から実装し、閾値の調整、不均衡データでの「正解率の罠」、多クラス分類の Macro / Micro 平均を確かめます。McNemar 検定と対応のあるブートストラップ法で、2 つのシステムの差が有意かどうかとサンプルサイズの影響も調べます。
- **CPU** · [自然言語処理システムの開発サイクル（文分割・データ分割・計算量）](notebooks/ch1_design_cycle.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_design_cycle.ipynb)
  - 最終確認 2026/11/24
  - （書籍 1-4・1-5）[サンプルデータ](misc/covid-annotation.csv)を使い、句点だけで文を分割すると失敗する例、ハイパーパラメータの選択に使ったデータで成績を報告したときの過大評価、計算量 O(1)・O(n)・O(n^2) による実行時間の違いを確かめます。
- **CPU** · [半教師あり学習と遠距離教師あり学習（Yarowsky・共訓練・マルチインスタンス集約）](notebooks/ch1_semisupervised.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_semisupervised.ipynb)
  - 最終確認 2026/11/24
  - （書籍 1-2・1-3）少数のシードから始める共訓練と Yarowsky の one sense per discourse 制約による半教師あり学習と、確信度の閾値を下げたときのセマンティックドリフトを確かめます。知識ベースを使う遠距離教師あり学習で、偶然の共起によるノイズとマルチインスタンス集約の効果も調べます。
- **CPU** · [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)
  - 最終確認 2026/11/24
  - （書籍 1-5・2-2）[サンプルデータ](misc/covid-annotation.csv)を第2章の SVM・BERT の演習と同じ分割で使い、TF-IDF とロジスティック回帰のベースライン、特徴量の重み、誤分類のエラー分析を確かめます。テストデータを見ずに訓練データの交差検証と開発データだけで素性を設計し直すアブレーションもします。
- **GPU 推奨** · [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)
  - 最終確認 2026/11/21
  - （書籍 2-4「演習：品質推定」）WMT21 の英日品質推定データで XLM-R をファインチューニングし、WMT22 のデータで人手評価との相関を COMET-QE と比べます。大きく外した翻訳の事例も確かめます。
  - 書籍からの変更：データを WMT21・WMT22 の品質推定タスクの英日翻訳のデータ（人手評価のスコア付き、それぞれ 1,000 文）に変え、2021 年以降更新されていない TransQuest の代わりに Transformers の `Trainer` で同じ構成のモデルを訓練します。
- **NLP クックブックの関連章**:
  - [1. データの収集と入出力](https://github.com/mamorlis/nlpcookbook#1-データの収集と入出力)：[データ分割 01-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/01_data_io/data_split.ipynb)
  - [3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)：[文分割 03-27](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sentence_split_ja.ipynb)
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[不均衡データ・しきい値調整 12-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/imbalanced.ipynb)
  - [14. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#14-評価指標と統計的検定)：[適合率・再現率・F1 14-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/prf_manual.ipynb)・[ブートストラップ信頼区間 14-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/bootstrap_ci.ipynb)・[統計的検定 14-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/significance_test.ipynb)
  - [17. 意味解析](https://github.com/mamorlis/nlpcookbook#17-意味解析)：[関係抽出 17-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/17_semantics/relation_extraction.ipynb)・[関係分類 17-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/17_semantics/relation_classification.ipynb)
  - [18. 語の意味と意味の変化](https://github.com/mamorlis/nlpcookbook#18-語の意味と意味の変化)：[ブートストラッピング 18-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/18_lexical_semantics/bootstrapping.ipynb)・[意味ドリフト 18-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/18_lexical_semantics/semantic_drift.ipynb)
  - [27. 機械翻訳](https://github.com/mamorlis/nlpcookbook#27-機械翻訳)：[品質推定 27-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_quality_estimation.ipynb)・[品質推定の学習 27-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_qe_train.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[適合率・再現率・F1 B-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/prf_scratch.ipynb)

### 第2章

書籍 2-4「演習：品質推定」は、[第1章に掲載している英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb)に対応します。

- **CPU** · [評価極性辞書と文単位・文書単位の極性分析](notebooks/ch2_sentiment_lexicon.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)
  - 最終確認 2026/11/22
  - （書籍 2-1）[サンプルデータ](misc/phrase-annotation.csv)（100 件）で、極性辞書だけ・否定と逆接を考慮したルール・教師あり学習を比べ、複数文のレビューで文書単位と文単位の分析を比べます。語彙ネットワークとスピンモデル（高村ら 2006）で、少数のシード語から極性辞書を自動で広げることも試します。
- **CPU** · [SVM カーネル（線形 vs RBF）・k 近傍法・ナイーブベイズによる文書分類と根拠分析](notebooks/ch2_svm_knn.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_svm_knn.ipynb)
  - 最終確認 2026/11/21
  - （書籍 2-1・2-2）[サンプルデータ](misc/covid-annotation.csv)の TF-IDF 表現で線形・多項式・RBF カーネルの SVM を比べ、k 近傍法で予測の根拠になる事例を示します。ナイーブベイズのラプラス平滑化と、クラスの不均衡に強い Complement ナイーブベイズも確かめます。
- **CPU** · [単語埋め込み（分散表現）と文脈付き埋め込みの比較](notebooks/ch2_word_embeddings.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_word_embeddings.ipynb)
  - 最終確認 2026/11/21
  - （書籍 第2章）共起行列の PPMI と SVD で静的な単語埋め込みを作って類似語の検索と可視化をし、多義語が 1 つのベクトルに潰れる限界を確かめます。文脈付き埋め込み（簡易な自己注意と日本語 BERT）で、多義語が文脈ごとに分かれる様子も見ます。
- **GPU 推奨** · [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)
  - 最終確認 2026/11/21
  - （書籍 2-2）日本語 BERT を[サンプルデータ](misc/covid-annotation.csv)（1,000 件）でファインチューニングして文書分類し、誤り分析と、同じテスト分割での TF-IDF とロジスティック回帰との比較をします。
  - 書籍からの変更：Transformers 5 で動くように更新し、東北大の BERT のモデル名を `cl-tohoku` から現在の `tohoku-nlp/bert-base-japanese-v3` に変えました。
- **CPU** · [多クラス分類と多ラベル分類（評価指標と訓練 CV による閾値選択）](notebooks/ch2_multilabel.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)
  - 最終確認 2026/11/24
  - （書籍 2-2）ニュース見出しで多クラス分類と多ラベル分類を比べ、Subset Accuracy・Hamming Loss・Micro-F1 などの評価尺度の違いと、訓練データの交差検証による閾値の選び方を確かめます。ラベル別の閾値と、ラベルの共起を使う Classifier Chains も試します。
- **CPU** · [文章の品質推定と解釈可能なシステム設計（接続表現ハイライト・線形モデルの根拠提示・特徴量ベース vs 微調整）](notebooks/ch2_writing_quality.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_writing_quality.ipynb)
  - 最終確認 2026/11/21
  - （書籍 2-3）1〜5 段階のスコア付きの作文サンプル（30 件）から接続表現や文字種の比率などの特徴量を取り出し、分類モデルの信頼度と線形モデルの素性の寄与で予測の根拠を示します。少ないデータでの特徴量ベースとファインチューニング（過学習と破壊的忘却）も比べます。
- **CPU** · [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)
  - 最終確認 2026/11/21
  - （書籍 2-3）書籍の表 2.1 の混同行列から Strict / Lenient 正解率と重みつきカッパ係数 (QWK) を実装します。[サンプルデータ](misc/phrase-annotation.csv)の 5 段階スコアで、回帰の予測が平均に寄る「MSE の罠」と、その補正方法を比べます。
- **CPU** · [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)
  - 最終確認 2026/11/18
  - （書籍 2-3）Kendall の τ・Spearman の ρ・nDCG を定義式から実装し、[サンプルデータ](misc/phrase-annotation.csv)で Pairwise ランキングと Pointwise 回帰を比べます。スコアを単調に変換しても、ランキングの予測順位が変わらないことも確かめます。
- **NLP クックブックの関連章**:
  - [6. 単語ベクトル](https://github.com/mamorlis/nlpcookbook#6-単語ベクトル)：[word2vec の学習 06-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/word2vec_train.ipynb)・[学習済みの日本語単語ベクトル 06-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/pretrained_vectors_ja.ipynb)・[単語ベクトルの可視化 06-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/word_vectors_viz.ipynb)・[単語類似度による評価 06-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/06_word_vectors/wordsim_eval.ipynb)
  - [8. Transformers の基本操作](https://github.com/mamorlis/nlpcookbook#8-transformers-の基本操作)：[文脈付き単語ベクトル 08-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/08_transformers/contextual_word_vectors.ipynb)
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[TF-IDF 12-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/tfidf_logreg_ja.ipynb)・[特徴量の重み 12-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/feature_importance.ipynb)・[エラー分析 12-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/error_analysis.ipynb)・[マルチラベル 12-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/multilabel.ipynb)・[BERT 12-21](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/bert_finetune.ipynb)
  - [13. 感情分析と意見・有害表現の分析](https://github.com/mamorlis/nlpcookbook#13-感情分析と意見有害表現の分析)：[極性辞書 13-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/13_sentiment/sentiment_lexicon.ipynb)・[二重否定・婉曲・皮肉の極性判定 13-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/13_sentiment/implicit_sentiment_ja.ipynb)・[スタンス検出 13-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/13_sentiment/stance_detection_ja.ipynb)
  - [19. 検索](https://github.com/mamorlis/nlpcookbook#19-検索)：[ランキング評価 19-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/19_search/ranking_metrics.ipynb)
  - [23. LLM の評価と分析](https://github.com/mamorlis/nlpcookbook#23-llm-の評価と分析)：[一対比較・Elo 23-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/23_llm_analysis/pairwise_judge_elo.ipynb)
  - [27. 機械翻訳](https://github.com/mamorlis/nlpcookbook#27-機械翻訳)：[品質推定 27-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_quality_estimation.ipynb)・[品質推定の学習 27-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_qe_train.ipynb)
  - [30. 言語教育・リーダビリティ・自動採点](https://github.com/mamorlis/nlpcookbook#30-言語教育リーダビリティ自動採点)：[自動採点・QWK 30-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/30_language_education/essay_scoring.ipynb)・[ルーブリック採点 30-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/30_language_education/rubric_scoring.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[PPMI+SVD B-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/ppmi_svd.ipynb)

### 第3章

- **CPU** · [固有表現認識の基礎（ガゼッティア・BIO タグ・素性テンプレートと CRF・サブワード整合）](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - 最終確認 2026/11/21
  - （書籍 3-1）ガゼッティアの最長一致と多義語の誤マッチの対策、BIO タグと `sklearn-crfsuite` による素性テンプレートの比較、`SentencePiece` のサブワードと BIO ラベルの整合を確かめます。
- **GPU 推奨** · [BERT による固有表現認識（Token Classification）](notebooks/ch3_bert_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_bert_ner.ipynb)
  - 最終確認 2026/11/21
  - （書籍 3-1）日本語 BERT を Token Classification としてファインチューニングし、`seqeval` でエンティティ単位の F1 を測ります。訓練データにない固有表現への汎化をガゼッティアと比べ、エラー分析をします。
- **CPU** · [形態素解析とサブワード分割（分割単位・正規化・未知語処理・Subword Regularization）](notebooks/ch3_morphology_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)
  - 最終確認 2026/11/21
  - （書籍 3-2）`SudachiPy` の分割単位（Mode A・B・C）、品詞・辞書形・正規化形、未知語の扱いを確かめ、`SentencePiece` のサブワード分割と比べます。ユニグラム言語モデルによる複数の分割候補と Subword Regularization も試します。
- **CPU** · [単語ラティス・仮名漢字変換・CRF vs MEMM・Pointwise 予測](notebooks/ch3_viterbi_crf.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)
  - 最終確認 2026/11/21
  - （書籍 3-1・3-2）単語ラティスと Viterbi アルゴリズムによる単語分割、バイグラム言語モデルによる仮名漢字変換、同じ素性で学習した MEMM と CRF の比較（ラベルバイアス問題）を確かめます。点推定による単語分割と、部分的アノテーションによる分野適応も試します。
- **CPU** · [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
  - 最終確認 2026/11/24
  - （書籍 3-3）編集距離によるスペル訂正、n-gram 言語モデルによる誤り検出、両者を組み合わせた雑音のある通信路モデルを実装し、文法誤り訂正の編集単位の F0.5 評価を確かめます。発展として、外来語の逆音訳 (Knight & Graehl 1997) も試します。
- **GPU 必須** · [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)
  - 最終確認 2026/11/25
  - （書籍 3-4「演習：文法誤り検出・訂正」）Fast GECToR を W&I+LOCNESS で訓練し、開発データの ERRANT の F0.5 でチェックポイントと誤り検出の閾値を選んで、英語の誤り訂正を評価します。後半では、ERRANT の誤りタイプ別の評価で語順やつづり・内容語の置換の再現率が低いことと、編集タグ 1 回で表せない訂正はほとんど直せないことを確かめます（練習問題 3-3）。
  - 書籍からの変更：データを cLang-8 から、申請なしで使える W&I+LOCNESS v2.1 に変え、1 つのノートブックで最後まで実行できるようにしました。Fast GECToR は 2023 年以降更新されていないので、`uv` で Python 3.10 の環境を作ります。
- **NLP クックブックの関連章**:
  - [2. 文字列処理と正規化](https://github.com/mamorlis/nlpcookbook#2-文字列処理と正規化)：[編集距離 02-24](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/02_string/edit_distance.ipynb)
  - [3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)：[Sudachi の分割単位 03-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_split.ipynb)・[Sudachi ユーザー辞書 03-18](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_userdic.ipynb)・[KyTea 分野適応 03-24](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/kytea_train.ipynb)・[MeCab ユーザー辞書 03-30](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/mecab_userdic.ipynb)
  - [7. サブワードとトークナイザ](https://github.com/mamorlis/nlpcookbook#7-サブワードとトークナイザ)：[Subword Regularization 07-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/07_subword/subword_regularization.ipynb)・[word_ids 07-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/07_subword/word_ids.ipynb)
  - [16. 固有表現抽出](https://github.com/mamorlis/nlpcookbook#16-固有表現抽出)：[BIO タグへの変換 16-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/spans_to_bio.ipynb)・[CRF 16-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/crf_tagger.ipynb)・[BERT 16-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/bert_ner_finetune.ipynb)
  - [29. 文法誤り訂正と文章校正](https://github.com/mamorlis/nlpcookbook#29-文法誤り訂正と文章校正)：[編集抽出 29-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/edit_extraction.ipynb)・[ERRANT 29-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/errant.ipynb)・[M2 形式 29-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/m2_format.ipynb)・[GEC F0.5 評価 29-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/gec_f05.ipynb)・[LLM による日本語の誤り訂正 29-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/gec_ja_llm.ipynb)・[マスク言語モデルによる誤り検出 29-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/ged_mlm.ipynb)・[日本語の校正 29-13](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/proofreading_ja.ipynb)・[スペル訂正 29-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/spelling_correction.ipynb)・[擬似誤りデータによる日本語 GEC の学習 29-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/29_gec/gec_synthetic_train.ipynb)
  - [31. 日本語入力（かな漢字変換）](https://github.com/mamorlis/nlpcookbook#31-日本語入力かな漢字変換)：[ユニグラム変換 31-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/31_japanese_input/kkc_unigram.ipynb)・[バイグラム変換 31-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/31_japanese_input/kkc_bigram.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[HMM 品詞タガー B-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/hmm_tagger.ipynb)・[Viterbi B-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/viterbi.ipynb)・[MEMM vs CRF B-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/memm_vs_crf_scratch.ipynb)・[n-gram 言語モデル B-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/ngram_lm_scratch.ipynb)・[編集距離スペル訂正 B-25](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/spelling_correction_scratch.ipynb)

### 第4章

- **CPU** · [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - 最終確認 2026/11/21
  - （書籍 4-1）ROUGE を定義式から実装して書籍の図 4.5 の計算例を確かめ、リード法・TextRank・LexRank と MMR を比べます。Pointer-Generator のコピー機構とカバレージ機構や、ハルシネーションを含む要約が ROUGE で高く出る逆転現象も確かめます。
- **CPU** · [翻訳メモリと統計的機械翻訳の基礎（IBM Model 1・フレーズベース SMT）](notebooks/ch4_smt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt.ipynb)
  - 最終確認 2026/11/24
  - （書籍 4-2-1・4-2-2）翻訳メモリのあいまい一致検索、EM アルゴリズムによる IBM Model 1 の単語アライメント、双方向アライメントの対称化とフレーズ抽出、フレーズベース SMT のデコーディングを、小さな対訳で一通り実装します。
- **CPU** · [機械翻訳の自動評価（BLEU）と対訳コーパスのノイズフィルタリング](notebooks/ch4_bleu_corpus.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_bleu_corpus.ipynb)
  - 最終確認 2026/11/24
  - （書籍 4-2-4・4-2-5）BLEU を定義式から実装し、書籍の図 4.11（参照訳の数と BLEU）の再現と、言い換えや否定に対する BLEU の限界を確かめます。ノイズを含む対訳コーパスを長さの比や IBM Model 1 の信頼度でふるいにかけ、単語アライメントが改善することも確かめます。
- **GPU 推奨** · [機械翻訳の自動評価と人手評価の相関（BLEU・chrF・BERTScore・COMET・品質推定）](notebooks/ch4_mt_eval.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_mt_eval.ipynb)
  - 最終確認 2026/11/25
  - （書籍 2-3・2-4・4-2-4）WMT22 の英日翻訳 13 システムの訳文と人手評価を使い、参照訳を使う評価（BLEU・chrF・BERTScore・COMET）と参照訳を使わない品質推定 (COMET-QE) の人手評価との相関を、文単位とシステム単位で比べます。参照訳が 1 つしかないために正しい言い換えが低く出る例と、参照訳を増やすと相関が上がる様子も確認できます。
- **GPU 必須** · [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - 最終確認 2026/11/21
  - （書籍 4-4「演習：機械翻訳」）田中コーパスで英日のニューラル機械翻訳を訓練し、開発データの BLEU でチェックポイントを選んで、テストデータの訳文を評価します。
  - 書籍からの変更：書籍の OpenNMT-py は 2024 年の v3.5.1 で開発が止まっているので、後継の [Eole](https://github.com/eole-nlp/eole) を使います（Colab の Python 3.13 では依存ライブラリが入らないので、`uv` で Python 3.12 の環境を作ります）。コマンドと設定ファイルの対応表はノートブックの末尾にあり、旧 OpenNMT-py 版のノートブックは[アーカイブ](misc/ch4_opennmt.ipynb)にあります。`fairseq` は 2022 年で開発が止まっていて、Colab では動かせません。
- **CPU** · [対話システムの基礎（ルールベース・検索型・タスク指向対話・検索拡張生成 RAG・評価・生成ベース）](notebooks/ch4_dialogue.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_dialogue.ipynb)
  - 最終確認 2026/11/25
  - （書籍 4-3）ルールベース対話、TF-IDF による用例検索型対話、意図分類とスロット抽出による複数ターンのタスク指向対話、宿泊規約を使った RAG 対話を実装し、BLEU の限界や Joint Goal Accuracy などの対話の評価を確かめます。第 7 節では軽量のオープン LLM (Qwen2.5-1.5B-Instruct) で同じ質問に生成で応答させ、用例検索型・テンプレート型 RAG と流暢さ・多様性・ハルシネーション・応答速度を比べます（第 7 節のみ GPU）。
- **GPU 推奨** · [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)
  - 最終確認 2026/11/21
  - （書籍 第1章 練習問題 4・5、4-2・4-3）API キーのいらない軽量のオープン LLM (`Qwen/Qwen2.5-1.5B-Instruct`) で分類・要約・翻訳をプロンプトで実行し、ゼロショットと 3-shot の比較、根拠文書を与えたときのハルシネーションの抑制、デコード戦略（貪欲法・ビームサーチ・サンプリング）の違いを確かめます。
- **NLP クックブックの関連章**:
  - [8. Transformers の基本操作](https://github.com/mamorlis/nlpcookbook#8-transformers-の基本操作)：[デコード比較 08-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/08_transformers/generation_decoding.ipynb)
  - [9. 言語モデルの確率と内部を調べる](https://github.com/mamorlis/nlpcookbook#9-言語モデルの確率と内部を調べる)：[アテンションの可視化 09-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/09_lm_analysis/attention_viz.ipynb)
  - [14. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#14-評価指標と統計的検定)：[BERTScore 14-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/bertscore.ipynb)・[自動評価と人手評価の相関 14-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/metric_correlation.ipynb)
  - [19. 検索](https://github.com/mamorlis/nlpcookbook#19-検索)：[MMR 19-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/19_search/mmr_diversify.ipynb)
  - [20. 質問応答](https://github.com/mamorlis/nlpcookbook#20-質問応答)：[質問生成 20-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/20_qa/question_generation.ipynb)
  - [21. 大規模言語モデル (LLM)](https://github.com/mamorlis/nlpcookbook#21-大規模言語モデル-llm)：[Few-shot プロンプト 21-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/21_llm/llm_few_shot.ipynb)・[ツール呼び出し 21-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/21_llm/llm_tool_calling.ipynb)
  - [23. LLM の評価と分析](https://github.com/mamorlis/nlpcookbook#23-llm-の評価と分析)：[一対比較・Elo 23-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/23_llm_analysis/pairwise_judge_elo.ipynb)
  - [24. LLM の学習と調整](https://github.com/mamorlis/nlpcookbook#24-llm-の学習と調整)：[タスク算術とモデルマージ 24-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/24_llm_training/task_arithmetic_merge.ipynb)
  - [25. RAG（検索拡張生成）](https://github.com/mamorlis/nlpcookbook#25-rag検索拡張生成)：[最小の RAG 25-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_minimal.ipynb)・[質問書き換え 25-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_query_rewrite.ipynb)・[出典検証 25-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_citation.ipynb)・[回答拒否 25-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/25_rag/rag_refusal.ipynb)
  - [26. 対話システム](https://github.com/mamorlis/nlpcookbook#26-対話システム)：[スロットフィリング 26-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/slot_filling.ipynb)・[対話履歴の管理 26-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/chat_history.ipynb)・[ペルソナ 26-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/persona_prompt.ipynb)・[複数ターンの RAG 26-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/chat_rag.ipynb)・[ガードレール 26-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/dialogue_guardrail.ipynb)・[対話評価 26-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/dialogue_eval.ipynb)・[音声対話 26-13](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/voice_dialogue.ipynb)・[対話状態追跡の評価 26-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_dialogue/dst_eval.ipynb)
  - [27. 機械翻訳](https://github.com/mamorlis/nlpcookbook#27-機械翻訳)：[対訳コーパス 27-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/parallel_corpus.ipynb)・[BLEU 27-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/bleu.ipynb)・[chrF・TER 27-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/chrf_ter.ipynb)・[COMET 27-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/comet.ipynb)・[品質推定 27-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/mt_quality_estimation.ipynb)・[Moses SMT 27-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/moses_smt.ipynb)・[NMT 27-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/nmt_from_scratch.ipynb)・[擬似対訳フィルタ 27-13](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/pseudo_parallel_filter.ipynb)・[用語集制約翻訳 27-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/terminology_constrained_translation.ipynb)・[LLM による翻訳 27-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_machine_translation/llm_translation.ipynb)
  - [28. 要約と平易化](https://github.com/mamorlis/nlpcookbook#28-要約と平易化)：[LexRank 28-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/extractive_summary.ipynb)・[ROUGE 28-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/rouge_ja.ipynb)・[Lead-3 28-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/lead3_baseline.ipynb)・[事実整合性検査 28-06](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/summary_faithfulness.ipynb)・[見出し生成 28-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/headline_generation.ipynb)・[T5 による見出し生成 28-13](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/t5_finetune.ipynb)・[テキスト平易化 28-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/text_simplification.ipynb)・[語彙平易化 28-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/lexical_simplification.ipynb)・[文体変換 28-16](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_summarization/style_transfer_ja.ipynb)
  - [付録 B. 仕組みを理解するための実装](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)：[ELIZA 方式 B-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/eliza_rule.ipynb)・[IBM Model 1 B-21](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/ibm_model1_scratch.ipynb)・[BLEU・ROUGE B-23](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/bleu_rouge_scratch.ipynb)・[TextRank・LexRank B-24](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/textrank_lexrank_scratch.ipynb)

### 第5章

- **CPU** · [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)
  - 最終確認 2026/11/18
  - （書籍 5-1・5-4）HTML タグや URL の除去と NFKC 正規化、文字 n-gram の Jaccard 係数による近似重複の検出とデータリークの実験、個人情報 (PII) のマスキングとスパムの除外を確かめます。
- **CPU** · [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - 最終確認 2026/11/21
  - （書籍 5-2、5-6「演習：フレーズ分類ラベルアノテーション」）2 人の作業者の評価極性アノテーションから Cohen の κ を計算し、不一致の分析と仕様書の改訂を経て一致率を測り直します。3 人以上での Fleiss の κ とスパマーの検出、欠損や順序尺度を扱える Krippendorff の α も確かめます。
  - 書籍の演習例は楽天データセットによるもので配布できないので、配布できる宿泊レビュー風のサンプルデータ（100 件）を作り、スプレッドシート用の [Excel ファイル](misc/phrase-annotation.xlsx)と Colab 演習用の [CSV ファイル](misc/phrase-annotation.csv)を公開しています。
- **CPU** · [形態素解析のユーザ辞書作成と単体テスト](notebooks/ch5_dictionary.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_dictionary.ipynb)
  - 最終確認 2026/11/24
  - （書籍 5-3）システム辞書ではうまく分割できない専門用語を `SudachiPy` のユーザ辞書に登録してビルドし、単体テストで確かめます。分野コーパスと背景コーパスを比べて（PMI と対数尤度比）専門用語の候補を自動で抽出し、辞書に追加するサイクルも試します。
- **CPU** · [機械学習によるコーパス品質管理と能動学習](notebooks/ch5_corpus_quality.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_corpus_quality.ipynb)
  - 最終確認 2026/11/21
  - （書籍 5-4-3）[サンプルデータ](misc/phrase-annotation.csv)で、仕様の改訂前後のラベルで学習した分類器の比較、学習曲線、予測確率によるアノテーションミスの候補の抽出、能動学習（不確実性サンプリング）を確かめます。
- **CPU** · [パイプライン処理のモジュール分割と前後処理・デバッグ](notebooks/ch5_toolkit_pipeline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_pipeline.ipynb)
  - 最終確認 2026/11/22
  - （書籍 5-5-1・5-5-3）1 つの関数にまとめた処理を JSON Lines でつなぐ 4 段のパイプラインに分け、モジュールの差し替え、前処理・後処理のアブレーション、中間出力の差分による原因の特定、回帰テストを確かめます。
- **CPU** · [パイプラインの高速化・スケーラビリティとボトルネック計測](notebooks/ch5_toolkit_benchmark.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_benchmark.ipynb)
  - 最終確認 2026/11/22
  - （書籍 5-5-1・5-5-2）1 文ごとのプロセス起動・常駐ワーカー・バッチ処理の速さと、Python のループ・NumPy・疎行列による行列積の速さを比べます。`cProfile` とアムダールの法則でボトルネックを見つけ、段階的に高速化します。
- **NLP クックブックの関連章**:
  - [1. データの収集と入出力](https://github.com/mamorlis/nlpcookbook#1-データの収集と入出力)：[重複除去 01-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/01_data_io/dedup_clean.ipynb)
  - [2. 文字列処理と正規化](https://github.com/mamorlis/nlpcookbook#2-文字列処理と正規化)：[NFKC 02-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/02_string/nfkc.ipynb)
  - [3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)：[Sudachi 正規化 03-17](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_normalize.ipynb)・[Sudachi ユーザー辞書 03-18](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sudachi_userdic.ipynb)・[Janome ユーザー辞書 03-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/janome_userdic.ipynb)・[MeCab ユーザー辞書 03-30](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/mecab_userdic.ipynb)・[専門用語抽出 03-31](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/term_extraction.ipynb)
  - [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)：[学習曲線 12-08](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/learning_curve.ipynb)・[能動学習 12-17](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/active_learning.ipynb)・[ラベル誤り検出 12-19](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/label_noise.ipynb)
  - [14. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#14-評価指標と統計的検定)：[一致度 14-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/14_evaluation/agreement.ipynb)
  - [16. 固有表現抽出](https://github.com/mamorlis/nlpcookbook#16-固有表現抽出)：[PII マスク 16-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/16_ner/pii_mask.ipynb)
  - [付録 A. Colab と Python の小技](https://github.com/mamorlis/nlpcookbook#付録-a-colab-と-python-の小技)：[処理時間計測 A-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/A_colab_python_tips/timing.ipynb)・[JSON Lines 入出力 A-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/A_colab_python_tips/jsonl_io.ipynb)・[巨大ファイルのストリーム処理 A-14](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/A_colab_python_tips/large_file_stream.ipynb)

## 練習問題

第1章から第5章までは章末に練習問題があります。それぞれの章の練習問題の[回答例](exercise.md)を掲載します。

## 正誤表

[正誤表](errata.md)を掲載します。本に関する誤りを見つけた場合は教えていただけると嬉しいです。

## リンク

[Amazon のページ](https://amzn.to/3K0j914) で購入できます（書籍版、Kindle 版ともにあります）。
EPUB/PDF 版は[技術評論社のページ](https://gihyo.jp/dp/ebook/2024/978-4-297-13864-6)から購入できます。
