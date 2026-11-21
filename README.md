# 自然言語処理の教科書
小町守「自然言語処理の教科書」（技術評論社）のサポートサイトです。

姉妹サイトとして、自然言語処理の「やりたいこと」に対して「こうやればいい」をまとめた Google Colab ノートブック集 [NLP クックブック](https://github.com/mamorlis/nlpcookbook) も公開しています。本書で扱っている前処理・形態素解析・テキスト分類・固有表現抽出・文法誤り訂正・機械翻訳・要約・対話などの実装レシピも多数収録していますので、あわせてご活用ください。

## 演習

第1章から5章までは演習があります。ノートブック名をクリックすると GitHub 上で閲覧でき、「Open in Colab」をクリックすると Google Colab で直接実行できます。GPU 演習を含む全 26 本のノートブックに整理済みの実行結果を埋め込んでいるため、GitHub 上でも出力結果までそのまま読めます。

- **CPU** — Colab の標準ランタイムで実行できます。初めての方は、第1章の [分類タスクの評価尺度と閾値調整](notebooks/ch1_evaluation.ipynb) から始められます。
- **GPU 推奨** — CPU でも動く設定がありますが、学習や推論に時間がかかります。
- **GPU 必須** — ノートブックの設定で GPU を使用します。

GPU を使う場合は、Colab の「ランタイム」→「ランタイムのタイプを変更」で、ハードウェア アクセラレータに GPU（T4 など）を選んでください。

### 第1章

- **CPU** · [自然言語処理システムの開発サイクル（文分割・データ分割・計算量）](notebooks/ch1_design_cycle.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_design_cycle.ipynb)
  - 最終確認 2026/11/18
  - [サンプルデータ](misc/covid-annotation.csv)を使い、素朴な句点文分割が破綻するケース（「モーニング娘。」や括弧内句点）への対処、小さな評価データでハイパーパラメータを選び続けることによる過大評価の実験、および $O(1)$・$O(n)$・$O(n^2)$（ハッシュ探索・線形探索・全対計算）の計算量スケーリング実測を CPU のみ・数秒で体験できます。
- **CPU** · [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)
  - 最終確認 2026/11/21
  - [サンプルデータ](misc/covid-annotation.csv)を使い、[SVM・k-NN・ナイーブベイズ演習](notebooks/ch2_svm_knn.ipynb)および[日本語 BERT 演習](notebooks/ch2_bert.ipynb)と `文書ID` が一致する同一の層化分割（訓練 810 件・開発 90 件・テスト 100 件）上で TF-IDF + ロジスティック回帰の軽量ベースラインを構築します。予測に寄与している特徴量（重み）の可視化や、誤分類事例と `コメント` 列を照らし合わせたエラー分析を CPU のみ・数秒で体験できます。
- **CPU** · [分類タスクの評価尺度と閾値調整（Fβ・特異度・不均衡データ）](notebooks/ch1_evaluation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)
  - 最終確認 2026/11/18
  - 正解率・適合率・再現率・特異度・偽陽性率・F値（$F_{0.5}$ / $F_1$ / $F_2$）を定義式から実装して `scikit-learn` と比較し、再現率 0.90 制約を満たす閾値調整、不均衡データでの「正解率の罠」、多クラス分類の Macro / Micro 平均を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)
  - 最終確認 2026/11/21
  - データを WMT21・WMT22 の品質推定タスクで公開された英日翻訳のデータ（人手評価のスコア付き、それぞれ1,000文）に変更しました。WMT21 のデータで訓練し、WMT22 のデータでテストします。
  - 2021年以降更新されていない TransQuest の代わりに、Transformers の `Trainer` で XLM-R をファインチューニングするようにしました（TransQuest の MonoTransQuest と同じ構成です）。開発データの Kendall と、[WMT22 の英日文単位品質推定の主指標](https://aclanthology.org/2022.wmt-1.3/)である Spearman の両方でチェックポイントを選び、同じ WMT22 のテストデータ上で両者を比較します。
  - 既存の品質推定モデル（COMET-QE）との同じテストデータでの比較に加え、人手評価スコアとの散布図や大きく外した翻訳事例（流暢だが誤訳している例など）を確認できます（実行結果埋め込み済み）。
- **NLP クックブックの関連章**: [1. データの収集と入出力](https://github.com/mamorlis/nlpcookbook#1-データの収集と入出力)（[データ分割 01-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/01_data_io/data_split.ipynb)）・[3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)（[文分割 03-26](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/03_japanese_tokenization/sentence_split_ja.ipynb)）・[13. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#13-評価指標と統計的検定)・[26. 機械翻訳](https://github.com/mamorlis/nlpcookbook#26-機械翻訳)（[品質推定 26-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_machine_translation/mt_quality_estimation.ipynb)）

### 第2章

書籍 2-4「演習：品質推定」は、[第1章に掲載している英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb)に対応します。

- **CPU** · [評価極性辞書と文単位・文書単位の極性分析](notebooks/ch2_sentiment_lexicon.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)
  - 最終確認 2026/11/21
  - [サンプルデータ](misc/phrase-annotation.csv)（100件）を使い、極性辞書のみ・否定反転と逆接を考慮したヒューリスティクス（全体データへの適合度評価）と教師あり機械学習（Bag-of-n-grams + ロジスティック回帰、5 分割交差検証による未知事例への汎化評価）を比較します。第 3 節では複数文からなる宿泊レビューを用い、文書一括（ML）、文単位の辞書＋ルールのみによる集約、ハイブリッド文平均、ハイブリッド重みづけ集約を比べながら不満根拠を特定できます（CPU のみ・数秒で実行できます）。
- **CPU** · [SVM カーネル（線形 vs RBF）・k 近傍法・ナイーブベイズによる文書分類と根拠分析](notebooks/ch2_svm_knn.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_svm_knn.ipynb)
  - 最終確認 2026/11/21
  - [サンプルデータ](misc/covid-annotation.csv)（[TF-IDF ベースライン](notebooks/ch1_tfidf_baseline.ipynb)・[BERT 演習](notebooks/ch2_bert.ipynb)と `文書ID` が一致する 810/90/100 層化分割）の高次元スパースな TF-IDF 表現に対し、線形カーネル（`LinearSVC`）と多項式・RBF カーネルの精度・過学習・計算時間を比較します。あわせて TF-IDF コサイン類似度を用いた k 近傍法（k-NN）による根拠事例の提示、および第 3 節で追加したナイーブベイズ分類器（`MultinomialNB`）のラプラス平滑化（`alpha` の違いによる Log-Loss とゼロ頻度問題）・対数尤度比による特徴語比較を確認できます（CPU のみ・十数秒で実行できます）。
- **CPU** · [単語埋め込み（分散表現）と文脈付き埋め込みの比較](notebooks/ch2_word_embeddings.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_word_embeddings.ipynb)
  - 最終確認 2026/11/18
  - 共起行列と PPMI + SVD による静的単語埋め込み（分散表現）の学習・コサイン類似度探索・2 次元可視化を通じ、多義語が単一ベクトルに潰れてしまう限界を確認したうえで、文脈付き埋め込み（文脈加重表現・日本語 BERT）によって多義語が文脈ごとに分離される仕組みを体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)
  - 最終確認 2026/11/21
  - Transformers 5 で動くように更新し、東北大の BERT ベースモデルも `tohoku-nlp/bert-base-japanese-v3` に更新しました（以前は `cl-tohoku` として公開されていましたが、現在は `tohoku-nlp` に変更されています）。
  - [サンプルデータ](misc/covid-annotation.csv)1,000件（TRUE と FALSE が500件ずつ）を[TF-IDF ベースライン](notebooks/ch1_tfidf_baseline.ipynb)・[SVM・k-NN・ナイーブベイズ演習](notebooks/ch2_svm_knn.ipynb)と `文書ID` が一致する 810/90/100 層化分割で訓練・開発・テストし、正解率・F1・混同行列・`コメント` 列との照合による誤り分析に加え、同一テスト分割上での TF-IDF + ロジスティック回帰との直接比較を確認できます（実行結果埋め込み済み）。
- **CPU** · [多クラス分類と多ラベル分類（評価指標と訓練 CV による閾値選択）](notebooks/ch2_multilabel.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)
  - 最終確認 2026/11/21
  - 重複のない 24 件の訓練見出しと 8 件のテスト見出しを用い、`MultiLabelBinarizer` と `OneVsRestClassifier` による多ラベル分類を実装します。テストデータを見ずに訓練データの 4 分割交差検証（CV）で出力閾値を選び、Top-1 多クラス分類・標準閾値（`0.50`）・CV 選択閾値の多ラベル分類を Subset Accuracy（完全一致率）・Hamming Loss・Micro-F1・Macro-F1・Samples-F1 で比較できます（CPU のみ・数秒で実行できます）。
- **CPU** · [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)
  - 最終確認 2026/11/21
  - 書籍 表 2.1（6 段階評価の混同行列）をヒートマップで可視化し、Strict / Lenient（±1）正解率および重みつきカッパ係数（QWK）を定義式から実装して `scikit-learn` と比較します。[サンプルデータ](misc/phrase-annotation.csv) の 5 段階スコアを用いた第 3 節では MSE 最小化の回帰モデルが平均値付近に予測を集中させてしまう「MSE の罠」を確認でき、続く第 4 節では訓練データ内での交差検証予測と累積割合の分位点から 5 段階の境界を決め、回帰の収縮を補正する手法を比較できます（CPU のみ・数秒で実行できます）。
- **CPU** · [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)
  - 最終確認 2026/11/18
  - Kendall の順位相関係数 $\tau_b$・Spearman の順位相関係数 $\rho$・nDCG@k を定義式から実装して `scipy.stats` / `scikit-learn` と比較します。さらに [サンプルデータ](misc/phrase-annotation.csv) の 5 段階スコアを用い、Pairwise ランキング（特徴量差分のロジスティック回帰）と Pointwise 回帰（Ridge）を 5 分割交差検証で比較するとともに、評価ラベルの大小関係を保つ非線形変換の前後で、Pairwise ランキングの予測順位が一致することを確認します（CPU のみ・数秒で実行できます）。
- **NLP クックブックの関連章**: [12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)（[TF-IDF 12-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/tfidf_logreg_ja.ipynb)・[マルチラベル 12-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/multilabel.ipynb)・[BERT 12-22](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/bert_finetune.ipynb)・[極性辞書 12-26](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/sentiment_lexicon.ipynb)）・[6. 単語ベクトル](https://github.com/mamorlis/nlpcookbook#6-単語ベクトル)・[8. Transformers の基本操作](https://github.com/mamorlis/nlpcookbook#8-transformers-の基本操作)・[22. 検索](https://github.com/mamorlis/nlpcookbook#22-検索)（[ランキング評価 22-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/22_search/ranking_metrics.ipynb)）

### 第3章

- **CPU** · [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)
  - 最終確認 2026/11/21
  - `SudachiPy` の分割単位（短単位・中単位・長単位）の違い、`SentencePiece` によるサブワード分割と未知語への振る舞い、BIO タグと CRF による固有表現認識（素性テンプレートによる精度変化と遷移重みの確認）を体験できます。評価では BIO トークン単位の Macro-F1 に加え、エンティティスパン完全一致の Precision / Recall / F1 もあわせて確認できます（CPU のみ・十数秒で実行できます）。
- **CPU** · [単語ラティス・Viterbi アルゴリズムと CRF vs MEMM](notebooks/ch3_viterbi_crf.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)
  - 最終確認 2026/11/18
  - 単語ラティスと Viterbi アルゴリズムによる日本語単語分割のコスト最小化（前方最長一致の失敗例と DP テーブルの追跡）に加え、同一の素性空間で学習した MEMM（局所正規化）と線形鎖 CRF（大域正規化）の比較実験を通じて「ラベルバイアス問題」を実際に確かめられます（CPU のみ・数秒で実行できます）。
- **CPU** · [ガゼッティア（辞書）による固有表現認識とサブワード・BIO ラベル整合](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - 最終確認 2026/11/18
  - 最長一致ガゼッティアでの多義語誤マッチを文脈分類器とのハイブリッド判定で抑える手法と、`SentencePiece` によるサブワード分割結果へ BIO タグ（`-100` マスク含む）を整合させる前処理・不正 `I-XXX` 遷移を補正する後処理を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [BERT による固有表現認識（Token Classification）](notebooks/ch3_bert_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_bert_ner.ipynb)
  - 最終確認 2026/11/21
  - Colab の T4 GPU で数分が目安です（実行結果埋め込み済み）。
  - 日本語 BERT（`tohoku-nlp/bert-base-japanese-v3`）と `AutoModelForTokenClassification` を用い、サブワードに対する `-100` ラベルマスク整合、ファインチューニング、`seqeval` によるエンティティ単位の F1 評価（トークン単位正解率との違い）、第 5 節の未知固有表現（OOV）に対する訓練語彙ガゼッティア vs BERT の汎化性能比較、およびエラー分析を体験できます。
- **CPU** · [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
  - 最終確認 2026/11/21
  - Levenshtein 距離と隣接文字入れ替え（swap）を考慮した制約付き Damerau–Levenshtein 距離（OSA）の動的計画法実装、スペル訂正の候補ランキング、単語バイグラム言語モデル（パープレキシティ）による誤り検出に加え、第 4 節では編集距離（通信路モデル）とバイグラム言語モデルを組み合わせた雑音のある通信路モデル（Noisy Channel Model）による文脈スペル・冠詞訂正を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 必須** · [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)
  - 最終確認 2026/11/21
  - データを cLang-8 から、BEA-2019 共有タスクで公開された W&I+LOCNESS v2.1 に変更しました。W&I は非営利の研究・教育目的なら申請なしでダウンロードできるので、Lang-8 のデータの申請や cLang-8 の作成が不要になり、1つのノートブックで最後まで実行できます。
  - W&I の訓練データ（約3.4万文）で10エポック訓練し、T4 GPU で40分ほどで終わります（短時間で動作確認したい方向けに `QUICK_RUN = True` の軽量モードも用意しています）。テストデータの正解は公開されていないので、開発データを半分に分けて開発データとテストデータにしています。
  - 学習率とエポック数を探索し、[GECToR の訓練ガイド](https://github.com/grammarly/gector/blob/master/docs/training_parameters.md)にならって最初の2エポックはエンコーダを固定して訓練する（`--cold_step_count 2`）ようにしました。Fast GECToR のこの機能にはバグがあるので、ノートブックの中でソースコードを1行修正しています。公開開発データを分けた演習内テストでの ERRANT の $F_{0.5}$ は0.41程度です（最初の設定では0.26程度でした）。開発データの ERRANT $F_{0.5}$ に基づいてチェックポイントと `--min_error_probability` 閾値の両方を選択して同じテストデータで従来設定と比較する実験や、原文・予測・正解の3列テーブルによるエラー分析も確認できます（実行結果埋め込み済み）。
  - Fast GECToR は2023年以降更新されていないため、ノートブックの中で `uv` を使って Python 3.10 の環境を作っています。
- **NLP クックブックの関連章**: [3. 日本語の形態素解析と文分割](https://github.com/mamorlis/nlpcookbook#3-日本語の形態素解析と文分割)・[7. サブワードとトークナイザ](https://github.com/mamorlis/nlpcookbook#7-サブワードとトークナイザ)（[word_ids 07-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/07_subword/word_ids.ipynb)）・[19. 固有表現抽出](https://github.com/mamorlis/nlpcookbook#19-固有表現抽出)（[CRF 19-10](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/19_ner/crf_tagger.ipynb)・[BERT 19-11](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/19_ner/bert_ner_finetune.ipynb)）・[28. 文法誤り訂正と言語教育](https://github.com/mamorlis/nlpcookbook#28-文法誤り訂正と言語教育)（[ERRANT 28-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_gec_education/errant.ipynb)・[スペル訂正 28-15](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/28_gec_education/spelling_correction.ipynb)）・[付録 B](https://github.com/mamorlis/nlpcookbook#付録-b-仕組みを理解するための実装)（[Viterbi B-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/B_implementations/viterbi.ipynb)）

### 第4章

- **CPU** · [文書要約のベースラインと ROUGE 評価](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - 最終確認 2026/11/21
  - ROUGE-1 / ROUGE-2 / ROUGE-L を定義式から実装し、抽出型要約の 3 手法（リード法・TextRank（共有文字バイグラムに基づく）・LexRank（TF-IDF コサイン類似度ベース））を比較します。ニュース型（冒頭結論）と後半結論型での手法ごとの得意・不得意や抽出型要約の限界に加え、第 4 節では複数文抽出（$k=2$）における冗長性問題と MMR（Maximal Marginal Relevance）による冗長性抑制の効果を確認できます（CPU のみ・数秒で実行できます）。
- **CPU** · [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)
  - 最終確認 2026/11/18
  - EM アルゴリズムによる IBM Model 1 の単語アライメント学習・可視化と、第 1 章から移設した BLEU の定義式実装（クリッピング・簡潔性ペナルティ・`sacrebleu` 検証・書籍 図 4.11 の再現・言い換えや否定反転での限界）を CPU のみ・数秒で体験できます。
- **GPU 必須** · [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - 最終確認 2026/11/21
  - 書籍で紹介している OpenNMT-py は2024年の v3.5.1 で開発が止まっているので、後継の [Eole](https://github.com/eole-nlp/eole) を使う演習に変更しました。コマンド名（`onmt_train` → `eole train` など）と設定ファイルの書き方が少し違いますが、演習の内容は同じです（実行結果埋め込み済み）。
  - Google Colab の Python 3.13 では Eole の依存ライブラリがインストールできないため、ノートブックの中で `uv` を使って Python 3.12 の環境を作っています。
- **GPU 必須** · 旧版：[OpenNMT-py によるニューラル機械翻訳演習](notebooks/ch4_opennmt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_opennmt.ipynb)
  - 最終確認 2026/11/21
  - 書籍に載せている OpenNMT-py（v3.5.1）のコマンドで演習したい場合はこちらを使ってください（新規の方は後継の Eole 版を推奨します。実行結果埋め込み済み）。Eole 版と同じく、`uv` で Python 3.12 の環境を作っています。
  - `fairseq` は2022年で開発が止まっていて、Google Colab では動かせません。
- **CPU** · [対話システムの基礎（ルールベース・検索型・タスク指向対話）](notebooks/ch4_dialogue.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_dialogue.ipynb)
  - 最終確認 2026/11/18
  - ELIZA 風の正規表現・テンプレートによるルールベース対話、TF-IDF コサイン類似度を用いた用例検索型対話に加え、意図分類・スロット抽出・対話状態管理を組み合わせた複数ターンのタスク指向対話（宿泊条件の確認）を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)
  - 最終確認 2026/11/21
  - Google Colab T4 GPU 向け（API キー不要・オープンウェイトの `Qwen/Qwen2.5-1.5B-Instruct` を使用、`dtype=` 指定に対応・実行結果埋め込み済み）
  - 第 1 章（深層学習の利点と課題）および第 4 章（大規模事前学習モデル・デコード戦略）に対応し、単一の LLM による分類・要約・翻訳のプロンプト実行、[サンプルデータ](misc/phrase-annotation.csv)の残り全 97 件に対するゼロショット vs 3-shot の比較、ハルシネーション発生例と根拠文書付与（RAG 風プロンプト）による抑制、および第 4 節でのデコード戦略比較（Greedy Search vs Beam Search vs Sampling）を体験できます。
- **NLP クックブックの関連章**: [27. 要約と平易化](https://github.com/mamorlis/nlpcookbook#27-要約と平易化)（[LexRank 27-01](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_summarization/extractive_summary.ipynb)・[ROUGE 27-02](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/27_summarization/rouge_ja.ipynb)）・[26. 機械翻訳](https://github.com/mamorlis/nlpcookbook#26-機械翻訳)（[BLEU 26-04](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_machine_translation/bleu.ipynb)・[NMT 26-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/26_machine_translation/nmt_from_scratch.ipynb)）・[25. 対話システム](https://github.com/mamorlis/nlpcookbook#25-対話システム)・[8. Transformers の基本操作](https://github.com/mamorlis/nlpcookbook#8-transformers-の基本操作)（[デコード比較 08-05](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/08_transformers/generation_decoding.ipynb)）・[14. 大規模言語モデル (LLM)](https://github.com/mamorlis/nlpcookbook#14-大規模言語モデル-llm)・[24. RAG（検索拡張生成）](https://github.com/mamorlis/nlpcookbook#24-rag検索拡張生成)

### 第5章

- **CPU** · [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)
  - 最終確認 2026/11/18
  - HTML タグ・URL 除去や Unicode 正規化（NFKC）、文字 n-gram の Jaccard 係数による近似重複検出とデータリーク実験に加え、メールアドレス・電話番号・郵便番号等の個人情報（PII）マスキングおよび日本語比率・記号比率によるスパム除外を体験できます（CPU のみ・数秒で実行できます）。
- **CPU** · [形態素解析のユーザ辞書作成と単体テスト](notebooks/ch5_dictionary.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_dictionary.ipynb)
  - 最終確認 2026/11/18
  - 書籍 5-3（辞書作成）に対応し、システム辞書だけでは分割・正規化がうまくいかない専門用語を `SudachiPy` のユーザ辞書 CSV（表層形・品詞・読み・正規化形）へ登録して `sudachipy ubuild` でコンパイルし、エラー記録と単体テストで動作を検証します（CPU のみ・十数秒で実行できます）。
- **CPU** · [フレーズ分類ラベルアノテーションと品質管理](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - 最終確認 2026/11/21
  - 書籍に載せている演習例は楽天データセットによるものなので配布はできませんが、配布可能な宿泊レビュー風のサンプルデータ（100件）を作成し、スプレッドシート用の [Excel ファイル](misc/phrase-annotation.xlsx)と Colab 演習用の [CSV ファイル](misc/phrase-annotation.csv)を公開しました。
  - 2人の作業者による評価極性アノテーションから混同行列と Cohen の κ を計算し、不一致事例の分析・仕様書を改訂して未知データで一致度を測り直す手順を体験できます。あわせて、3人以上の作業者に対する Fleiss の κ とスパマー検出、欠損あり行列や 5 段階順序尺度に対応する Krippendorff の α、学習曲線や分類器の予測確率を用いたアノテーションミス候補の抽出、および第 5-4 節の能動学習シミュレーション（不確実性サンプリング vs ランダムサンプリング）も扱っています。
- **NLP クックブックの関連章**: [1. データの収集と入出力](https://github.com/mamorlis/nlpcookbook#1-データの収集と入出力)（[重複除去 01-07](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/01_data_io/dedup_clean.ipynb)）・[2. 文字列処理と正規化](https://github.com/mamorlis/nlpcookbook#2-文字列処理と正規化)（[NFKC 02-03](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/02_string/nfkc.ipynb)）・[12. テキスト分類](https://github.com/mamorlis/nlpcookbook#12-テキスト分類)（[能動学習 12-18](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/active_learning.ipynb)・[ラベル誤り検出 12-20](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/12_classification/label_noise.ipynb)）・[13. 評価指標と統計的検定](https://github.com/mamorlis/nlpcookbook#13-評価指標と統計的検定)（[一致度 13-09](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/13_evaluation/agreement.ipynb)）・[19. 固有表現抽出](https://github.com/mamorlis/nlpcookbook#19-固有表現抽出)（[PII マスク 19-12](https://github.com/mamorlis/nlpcookbook/blob/main/notebooks/19_ner/pii_mask.ipynb)）

## 練習問題

第1章から第5章までは章末に練習問題があります。それぞれの章の練習問題の[回答例](exercise.md)を掲載します。

## 正誤表

[正誤表](errata.md)を掲載します。本に関する誤りを見つけた場合は教えていただけると嬉しいです。

## リンク

[Amazon のページ](https://amzn.to/3K0j914) で購入できます（書籍版、Kindle 版ともにあります）。
EPUB/PDF 版は[技術評論社のページ](https://gihyo.jp/dp/ebook/2024/978-4-297-13864-6)から購入できます。
