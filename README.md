# 自然言語処理の教科書
小町守「自然言語処理の教科書」（技術評論社）のサポートサイトです。

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
  - 最終確認 2026/11/25
  - （書籍 1-4・1-5）[サンプルデータ](misc/covid-annotation.csv)を使い、句点だけで文を分割すると失敗する例、ハイパーパラメータの選択に使ったデータで成績を報告したときの過大評価、計算量 O(1)・O(n)・O(n^2) による実行時間の違いを確かめます。
- **CPU** · [半教師あり学習と遠距離教師あり学習（Yarowsky・共訓練・マルチインスタンス集約）](notebooks/ch1_semisupervised.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_semisupervised.ipynb)
  - 最終確認 2026/11/24
  - （書籍 1-2・1-3）少数のシードから始める共訓練と Yarowsky の one sense per discourse 制約による半教師あり学習と、確信度の閾値を下げたときのセマンティックドリフトを確かめます。知識ベースを使う遠距離教師あり学習で、偶然の共起によるノイズとマルチインスタンス集約の効果も調べます。
- **CPU** · [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)
  - 最終確認 2026/11/25
  - （書籍 1-5・2-2）[サンプルデータ](misc/covid-annotation.csv)を第2章の SVM・BERT の演習と同じ分割で使い、TF-IDF とロジスティック回帰のベースライン、特徴量の重み、誤分類のエラー分析を確かめます。テストデータを見ずに訓練データの交差検証と開発データだけで素性を設計し直すアブレーションもします。
- **GPU 推奨** · [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)
  - 最終確認 2026/11/21
  - （書籍 2-4「演習：品質推定」）WMT21 の英日品質推定データで XLM-R をファインチューニングし、WMT22 のデータで人手評価との相関を COMET-QE と比べます。大きく外した翻訳の事例も確かめます。
  - 書籍からの変更：データを WMT21・WMT22 の品質推定タスクの英日翻訳のデータ（人手評価のスコア付き、それぞれ 1,000 文）に変え、2021 年以降更新されていない TransQuest の代わりに Transformers の `Trainer` で同じ構成のモデルを訓練します。

### 第2章

書籍 2-4「演習：品質推定」は、[第1章に掲載している英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb)に対応します。

- **CPU** · [評価極性辞書と文単位・文書単位の極性分析](notebooks/ch2_sentiment_lexicon.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)
  - 最終確認 2026/11/25
  - （書籍 2-1）[サンプルデータ](misc/phrase-annotation.csv)（100 件）で、極性辞書だけ・否定と逆接を考慮したルール・教師あり学習を比べ、複数文のレビューで文書単位と文単位の分析を比べます。語彙ネットワークとスピンモデル（高村ら 2006）で、少数のシード語から極性辞書を自動で広げることも試します。
- **CPU** · [SVM カーネル（線形 vs RBF）・k 近傍法・ナイーブベイズによる文書分類と根拠分析](notebooks/ch2_svm_knn.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_svm_knn.ipynb)
  - 最終確認 2026/11/25
  - （書籍 2-1・2-2）[サンプルデータ](misc/covid-annotation.csv)の TF-IDF 表現で線形・多項式・RBF カーネルの SVM を比べ、k 近傍法で予測の根拠になる事例を示します。ナイーブベイズのラプラス平滑化と、クラスの不均衡に強い Complement ナイーブベイズも確かめます。
- **CPU** · [単語埋め込み（分散表現）と文脈付き埋め込みの比較](notebooks/ch2_word_embeddings.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_word_embeddings.ipynb)
  - 最終確認 2026/11/25
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
  - 最終確認 2026/11/25
  - （書籍 2-3）書籍の表 2.1 の混同行列から Strict / Lenient 正解率と重みつきカッパ係数 (QWK) を実装します。[サンプルデータ](misc/phrase-annotation.csv)の 5 段階スコアで、回帰の予測が平均に寄る「MSE の罠」と、その補正方法を比べます。
- **CPU** · [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)
  - 最終確認 2026/11/25
  - （書籍 2-3）Kendall の τ・Spearman の ρ・nDCG を定義式から実装し、[サンプルデータ](misc/phrase-annotation.csv)で Pairwise ランキングと Pointwise 回帰を比べます。スコアを単調に変換しても、ランキングの予測順位が変わらないことも確かめます。

### 第3章

- **CPU** · [固有表現認識の基礎（ガゼッティア・BIO タグ・素性テンプレートと CRF・サブワード整合）](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - 最終確認 2026/11/21
  - （書籍 3-1）ガゼッティアの最長一致と多義語の誤マッチの対策、BIO タグと `sklearn-crfsuite` による素性テンプレートの比較、`SentencePiece` のサブワードと BIO ラベルの整合を確かめます。
- **GPU 推奨** · [BERT による固有表現認識 (Token Classification)](notebooks/ch3_bert_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_bert_ner.ipynb)
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

### 第4章

- **CPU** · [文書要約のベースライン・抽象型要約・ROUGE とハルシネーション](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - 最終確認 2026/11/21
  - （書籍 4-1）ROUGE を定義式から実装して書籍の図 4.5 の計算例を確かめ、リード法・TextRank・LexRank と MMR を比べます。Pointer-Generator のコピー機構とカバレージ機構や、ハルシネーションを含む要約が ROUGE で高く出る逆転現象も確かめます。
- **CPU** · [翻訳メモリと統計的機械翻訳の基礎（IBM Model 1・フレーズベース SMT）](notebooks/ch4_smt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt.ipynb)
  - 最終確認 2026/11/24
  - （書籍 4-2-1・4-2-2）翻訳メモリのあいまい一致検索、EM アルゴリズムによる IBM Model 1 の単語アライメント、双方向アライメントの対称化とフレーズ抽出、フレーズベース SMT のデコーディングを、小さな対訳で一通り実装します。
- **CPU** · [機械翻訳の自動評価 (BLEU) と対訳コーパスのノイズフィルタリング](notebooks/ch4_bleu_corpus.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_bleu_corpus.ipynb)
  - 最終確認 2026/11/24
  - （書籍 4-2-4・4-2-5）BLEU を定義式から実装し、書籍の図 4.11（参照訳の数と BLEU）の再現と、言い換えや否定に対する BLEU の限界を確かめます。ノイズを含む対訳コーパスを長さの比や IBM Model 1 の信頼度でふるいにかけ、単語アライメントが改善することも確かめます。
- **GPU 推奨** · [機械翻訳の自動評価と人手評価の相関（BLEU・chrF・BERTScore・COMET・品質推定）](notebooks/ch4_mt_eval.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_mt_eval.ipynb)
  - 最終確認 2026/11/25
  - （書籍 2-3・2-4・4-2-4）WMT22 の英日翻訳 13 システムの訳文と人手評価を使い、参照訳を使う評価（BLEU・chrF・BERTScore・COMET）と参照訳を使わない品質推定 (COMET-QE) の人手評価との相関を、文単位とシステム単位で比べます。参照訳が 1 つしかないために正しい言い換えが低く出る例と、参照訳を増やすと相関が上がる様子も確認できます。
- **GPU 必須** · [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - 最終確認 2026/11/21
  - （書籍 4-4「演習：機械翻訳」）田中コーパスで英日のニューラル機械翻訳を訓練し、開発データの BLEU でチェックポイントを選んで、テストデータの訳文を評価します。
  - 書籍からの変更：書籍の OpenNMT-py は 2024 年の v3.5.1 で開発が止まっているので、後継の [Eole](https://github.com/eole-nlp/eole) を使います（Colab の Python 3.13 では依存ライブラリが入らないので、`uv` で Python 3.12 の環境を作ります）。コマンドと設定ファイルの対応表はノートブックの末尾にあり、旧 OpenNMT-py 版のノートブックは[アーカイブ](misc/ch4_opennmt.ipynb)にあります。`fairseq` は 2022 年で開発が止まっていて、Colab では動かせません。
- **GPU 推奨** · [対話システムの基礎（ルールベース・検索型・タスク指向対話・検索拡張生成 RAG・評価・生成ベース）](notebooks/ch4_dialogue.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_dialogue.ipynb)
  - 最終確認 2026/11/25
  - （書籍 4-3）ルールベース対話、TF-IDF による用例検索型対話、意図分類とスロット抽出による複数ターンのタスク指向対話、宿泊規約を使った RAG 対話を実装し、BLEU の限界や Joint Goal Accuracy などの対話の評価を確かめます。第 7 節では軽量のオープン LLM (Qwen2.5-1.5B-Instruct) で同じ質問に生成で応答させ、用例検索型・テンプレート型 RAG と流暢さ・多様性・ハルシネーション・応答速度を比べます（第 7 節のみ GPU）。
- **GPU 推奨** · [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)
  - 最終確認 2026/11/21
  - （書籍 第1章 練習問題 4・5、4-2・4-3）API キーのいらない軽量のオープン LLM (`Qwen/Qwen2.5-1.5B-Instruct`) で分類・要約・翻訳をプロンプトで実行し、ゼロショットと 3-shot の比較、根拠文書を与えたときのハルシネーションの抑制、デコード戦略（貪欲法・ビームサーチ・サンプリング）の違いを確かめます。

### 第5章

- **CPU** · [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)
  - 最終確認 2026/11/18
  - （書籍 5-1・5-4）HTML タグや URL の除去と NFKC 正規化、文字 n-gram の Jaccard 係数による近似重複の検出とデータリークの実験、個人情報 (PII) のマスキングとスパムの除外を確かめます。
- **CPU** · [フレーズ分類ラベルアノテーションと作業者間一致率](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - 最終確認 2026/11/25
  - （書籍 5-2、5-6「演習：フレーズ分類ラベルアノテーション」）2 人の作業者の評価極性アノテーションから Cohen の κ を計算し、不一致の分析と仕様書の改訂を経て一致率を測り直します。3 人以上での Fleiss の κ とスパマーの検出、欠損や順序尺度を扱える Krippendorff の α も確かめます。
  - 書籍の演習例は楽天データセットによるもので配布できないので、配布できる宿泊レビュー風のサンプルデータ（100 件）を作り、スプレッドシート用の [Excel ファイル](misc/phrase-annotation.xlsx)と Colab 演習用の [CSV ファイル](misc/phrase-annotation.csv)を公開しています。
- **CPU** · [形態素解析のユーザ辞書作成と単体テスト](notebooks/ch5_dictionary.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_dictionary.ipynb)
  - 最終確認 2026/11/24
  - （書籍 5-3）システム辞書ではうまく分割できない専門用語を `SudachiPy` のユーザ辞書に登録してビルドし、単体テストで確かめます。分野コーパスと背景コーパスを比べて（PMI と対数尤度比）専門用語の候補を自動で抽出し、辞書に追加するサイクルも試します。
- **CPU** · [機械学習によるコーパス品質管理と能動学習](notebooks/ch5_corpus_quality.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_corpus_quality.ipynb)
  - 最終確認 2026/11/25
  - （書籍 5-4-3）[サンプルデータ](misc/phrase-annotation.csv)で、仕様の改訂前後のラベルで学習した分類器の比較、学習曲線、予測確率によるアノテーションミスの候補の抽出、能動学習（不確実性サンプリング）を確かめます。
- **CPU** · [パイプライン処理のモジュール分割と前後処理・デバッグ](notebooks/ch5_toolkit_pipeline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_pipeline.ipynb)
  - 最終確認 2026/11/22
  - （書籍 5-5-1・5-5-3）1 つの関数にまとめた処理を JSON Lines でつなぐ 4 段のパイプラインに分け、モジュールの差し替え、前処理・後処理のアブレーション、中間出力の差分による原因の特定、回帰テストを確かめます。
- **CPU** · [パイプラインの高速化・スケーラビリティとボトルネック計測](notebooks/ch5_toolkit_benchmark.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_toolkit_benchmark.ipynb)
  - 最終確認 2026/11/22
  - （書籍 5-5-1・5-5-2）1 文ごとのプロセス起動・常駐ワーカー・バッチ処理の速さと、Python のループ・NumPy・疎行列による行列積の速さを比べます。`cProfile` とアムダールの法則でボトルネックを見つけ、段階的に高速化します。

## 練習問題

第1章から第5章までは章末に練習問題があります。それぞれの章の練習問題の[回答例](exercise.md)を掲載します。

## 正誤表

[正誤表](errata.md)を掲載します。本に関する誤りを見つけた場合は教えていただけると嬉しいです。

## リンク

[Amazon のページ](https://amzn.to/3K0j914) で購入できます（書籍版、Kindle 版ともにあります）。
EPUB/PDF 版は[技術評論社のページ](https://gihyo.jp/dp/ebook/2024/978-4-297-13864-6)から購入できます。

## ライセンス

本リポジトリのノートブック・コードは [MIT License](LICENSE) のもとで公開しています。
