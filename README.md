# 自然言語処理の教科書
小町守「自然言語処理の教科書」（技術評論社）のサポートサイトです。

姉妹サイトとして、自然言語処理の「やりたいこと」に対して「こうやればいい」をまとめた Google Colab ノートブック集 [NLP クックブック](https://github.com/mamorlis/nlpcookbook) も公開しています。本書で扱っている前処理・形態素解析・テキスト分類・固有表現抽出・文法誤り訂正・機械翻訳・要約・対話などの実装レシピも多数収録していますので、あわせてご活用ください。

## 演習

第1章から5章までは演習があります。ノートブック名をクリックすると GitHub 上で閲覧でき、「Open in Colab」をクリックすると Google Colab で直接実行できます。

- **CPU** — Colab の標準ランタイムで実行できます。初めての方は、第1章の [分類タスクの評価尺度と閾値調整](notebooks/ch1_evaluation.ipynb) から始められます。
- **GPU 推奨** — CPU でも動く設定がありますが、学習や推論に時間がかかります。
- **GPU 必須** — ノートブックの設定で GPU を使用します。

GPU を使う場合は、Colab の「ランタイム」→「ランタイムのタイプを変更」で、ハードウェア アクセラレータに GPU（T4 など）を選んでください。

### 第1章

- **CPU** · [自然言語処理システムの開発サイクル（文分割・データ分割・計算量）](notebooks/ch1_design_cycle.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_design_cycle.ipynb)
  - 最終確認 2026/11/18
  - [サンプルデータ](misc/covid-annotation.csv)を使い、素朴な句点文分割が破綻するケース（「モーニング娘。」や括弧内句点）への対処、小さな評価データでハイパーパラメータを選び続けることによる過大評価の実験、および $O(1)$・$O(n)$・$O(n^2)$（ハッシュ探索・線形探索・全対計算）の計算量スケーリング実測を CPU のみ・数秒で体験できます。
- **CPU** · [TF-IDF と線形モデルによる文書分類ベースライン・エラー分析](notebooks/ch1_tfidf_baseline.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_tfidf_baseline.ipynb)
  - 最終確認 2026/11/18
  - [サンプルデータ](misc/covid-annotation.csv)を使い、TF-IDF + ロジスティック回帰で軽量ベースラインを構築します。予測に寄与している特徴量（重み）の可視化や、誤分類事例と `コメント` 列を照らし合わせたエラー分析を CPU のみ・数秒で体験できます。
- **CPU** · [分類タスクの評価尺度と閾値調整（Fβ・特異度・不均衡データ）](notebooks/ch1_evaluation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_evaluation.ipynb)
  - 最終確認 2026/11/18
  - 正解率・適合率・再現率・特異度・偽陽性率・F値（$F_{0.5}$ / $F_1$ / $F_2$）を定義式から実装して `scikit-learn` と比較し、再現率 0.90 制約を満たす閾値調整、不均衡データでの「正解率の罠」、多クラス分類の Macro / Micro 平均を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [英日機械翻訳の品質推定](notebooks/ch1_qe.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch1_qe.ipynb)
  - 最終確認 2026/11/19
  - データを WMT21・WMT22 の品質推定タスクで公開された英日翻訳のデータ（人手評価のスコア付き、それぞれ1,000文）に変更しました。WMT21 のデータで訓練し、WMT22 のデータでテストします。
  - 2021年以降更新されていない TransQuest の代わりに、Transformers の `Trainer` で XLM-R をファインチューニングするようにしました（TransQuest の MonoTransQuest と同じ構成です）。WMT22 の公式の評価尺度である Kendall's tau でも評価します。
  - 既存の品質推定モデル（COMET-QE）との比較に加え、人手評価スコアとの散布図や大きく外した翻訳事例（流暢だが誤訳している例など）を確認できます。

### 第2章

- **CPU** · [評価極性辞書と文単位・文書単位の極性分析](notebooks/ch2_sentiment_lexicon.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_sentiment_lexicon.ipynb)
  - 最終確認 2026/11/18
  - [サンプルデータ](misc/phrase-annotation.csv)（100件）を使い、極性辞書のみ・否定反転と逆接を考慮したヒューリスティクス・教師あり機械学習（Bag-of-n-grams + ロジスティック回帰）を比較します。後半では複数文からなる宿泊レビューを用い、文書全体を一括判定する手法と文単位に分解して不満根拠を特定・重みづけ集約する手法の違いを確認できます（CPU のみ・数秒で実行できます）。
- **CPU** · [SVM カーネル（線形 vs RBF）と k 近傍法による根拠分析](notebooks/ch2_svm_knn.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_svm_knn.ipynb)
  - 最終確認 2026/11/18
  - [サンプルデータ](misc/covid-annotation.csv)の高次元スパースな TF-IDF 表現に対し、線形カーネル（`LinearSVC`）と多項式・RBF カーネルの精度・過学習・計算時間を比較します。あわせて TF-IDF コサイン類似度を用いた k 近傍法（k-NN）で、予測の根拠や誤分類の原因となった類似訓練事例を確認できます（CPU のみ・十数秒で実行できます）。
- **CPU** · [単語埋め込み（分散表現）と文脈付き埋め込みの比較](notebooks/ch2_word_embeddings.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_word_embeddings.ipynb)
  - 最終確認 2026/11/18
  - 共起行列と PPMI + SVD による静的単語埋め込み（分散表現）の学習・コサイン類似度探索・2 次元可視化を通じ、多義語が単一ベクトルに潰れてしまう限界を確認したうえで、文脈付き埋め込み（文脈加重表現・日本語 BERT）によって多義語が文脈ごとに分離される仕組みを体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [日本語 BERT モデルによる文書分類](notebooks/ch2_bert.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_bert.ipynb)
  - 最終確認 2026/11/19
  - Transformers 5 で動くように更新しました。東北大の BERT モデルの名前が `cl-tohoku` から `tohoku-nlp` に変わったので、合わせて変更しています。
  - [サンプルデータ](misc/covid-annotation.csv)1,000件（TRUE と FALSE が500件ずつ）を層化分割して訓練・開発・テストし、正解率・F1・混同行列に加えて誤分類事例を `コメント` 列と照らし合わせて分析できます。テストデータでの正解率・F1 は0.95〜0.97程度です。
- **CPU** · [多クラス分類と多ラベル分類（評価指標と共起）](notebooks/ch2_multilabel.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_multilabel.ipynb)
  - 最終確認 2026/11/18
  - 1 つの文書に複数カテゴリが同時に付きうる多ラベル分類を `MultiLabelBinarizer` と `OneVsRestClassifier` で実装し、Subset Accuracy（完全一致率）と Hamming Loss / Micro-F1 / Macro-F1 / Samples-F1 の違いや閾値調整を体験できます（CPU のみ・数秒で実行できます）。
- **CPU** · [順序尺度の評価（QWK・Strict/Lenient・分類 vs 回帰）](notebooks/ch2_ordinal_qwk.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ordinal_qwk.ipynb)
  - 最終確認 2026/11/18
  - 書籍 表 2.1（6 段階評価の混同行列）をヒートマップで可視化し、Strict / Lenient（±1）正解率および重みつきカッパ係数（QWK）を定義式から実装して `scikit-learn` と比較します。あわせて [サンプルデータ](misc/phrase-annotation.csv) の 5 段階スコアを用い、MSE 最小化の回帰モデルが平均値付近に予測を集中させてしまう「MSE の罠」を確認できます（CPU のみ・数秒で実行できます）。
- **CPU** · [ランキング問題と順位評価指標（Kendall's τ・Spearman's ρ・nDCG）](notebooks/ch2_ranking.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch2_ranking.ipynb)
  - 最終確認 2026/11/18
  - Kendall の順位相関係数 $\tau_b$・Spearman の順位相関係数 $\rho$・nDCG@k を定義式から実装して `scipy.stats` / `scikit-learn` と比較します。さらに [サンプルデータ](misc/phrase-annotation.csv) の 5 段階スコアを用い、Pairwise ランキング（特徴量差分のロジスティック回帰）と Pointwise 回帰（Ridge）を 5 分割交差検証で比較するとともに、評価尺度の単調非線形変換に対して Pairwise ランキングの順位が 100% 不変であることを実証します（CPU のみ・数秒で実行できます）。

### 第3章

- **CPU** · [形態素解析・サブワード分割と固有表現認識（系列ラベリング）](notebooks/ch3_morphology_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_morphology_ner.ipynb)
  - 最終確認 2026/11/18
  - `SudachiPy` の分割単位（短単位・中単位・長単位）の違い、`SentencePiece` によるサブワード分割と未知語への振る舞い、BIO タグと CRF による固有表現認識（素性テンプレートによる精度変化と遷移重みの確認）を体験できます（CPU のみ・十数秒で実行できます）。
- **CPU** · [単語ラティス・Viterbi アルゴリズムと CRF vs MEMM](notebooks/ch3_viterbi_crf.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_viterbi_crf.ipynb)
  - 最終確認 2026/11/18
  - 単語ラティスと Viterbi アルゴリズムによる日本語単語分割のコスト最小化（前方最長一致の失敗例と DP テーブルの追跡）に加え、同一の素性空間で学習した MEMM（局所正規化）と線形鎖 CRF（大域正規化）の比較実験を通じて「ラベルバイアス問題」を実際に確かめられます（CPU のみ・数秒で実行できます）。
- **CPU** · [ガゼッティア（辞書）による固有表現認識とサブワード・BIO ラベル整合](notebooks/ch3_ner_gazetteer_subword.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_ner_gazetteer_subword.ipynb)
  - 最終確認 2026/11/18
  - 最長一致ガゼッティアでの多義語誤マッチを文脈分類器とのハイブリッド判定で抑える手法と、`SentencePiece` によるサブワード分割結果へ BIO タグ（`-100` マスク含む）を整合させる前処理・不正 `I-XXX` 遷移を補正する後処理を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [BERT による固有表現認識（Token Classification）](notebooks/ch3_bert_ner.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_bert_ner.ipynb)
  - 最終確認 2026/11/19
  - Colab の T4 GPU で数分が目安です。
  - 日本語 BERT（`tohoku-nlp/bert-base-japanese-v3`）と `AutoModelForTokenClassification` を用い、サブワードに対する `-100` ラベルマスク整合、ファインチューニング、および `seqeval` によるエンティティ単位の F1 評価（トークン単位正解率との違い）とエラー分析を体験できます。
- **CPU** · [編集距離と n-gram 言語モデルによる誤り検出・訂正](notebooks/ch3_edit_distance_lm.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_edit_distance_lm.ipynb)
  - 最終確認 2026/11/18
  - Levenshtein 距離と隣接文字入れ替え（swap）を考慮した Damerau-Levenshtein 距離を動的計画法で実装し、スペル訂正の候補ランキングや n-gram 言語モデル（パープレキシティ）による誤り検出を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 必須** · [Fast GECToR と W&I による英語誤り検出・訂正](notebooks/ch3_gector.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch3_gector.ipynb)
  - 最終確認 2026/11/19
  - データを cLang-8 から、BEA-2019 共有タスクで公開された W&I+LOCNESS v2.1 に変更しました。W&I は非営利の研究・教育目的なら申請なしでダウンロードできるので、Lang-8 のデータの申請や cLang-8 の作成が不要になり、1つのノートブックで最後まで実行できます。
  - W&I の訓練データ（約3.4万文）で10エポック訓練し、T4 GPU で40分ほどで終わります（短時間で動作確認したい方向けに `QUICK_RUN = True` の軽量モードも用意しています）。テストデータの正解は公開されていないので、開発データを半分に分けて開発データとテストデータにしています。
  - 学習率とエポック数を探索し、[GECToR の訓練ガイド](https://github.com/grammarly/gector/blob/master/docs/training_parameters.md)にならって最初の2エポックはエンコーダを固定して訓練する（`--cold_step_count 2`）ようにしました。Fast GECToR のこの機能にはバグがあるので、ノートブックの中でソースコードを1行修正しています。ERRANT で評価すると F0.5 は0.41程度です（最初の設定では0.26程度でした）。開発データ上での `--min_error_probability` 閾値トレードオフ比較や、原文・予測・正解の3列テーブルによるエラー分析も確認できます。
  - Fast GECToR は2023年以降更新されていないため、ノートブックの中で `uv` を使って Python 3.10 の環境を作っています。

### 第4章

- **CPU** · [文書要約のベースラインと ROUGE 評価](notebooks/ch4_summarization.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_summarization.ipynb)
  - 最終確認 2026/11/18
  - ROUGE-1 / ROUGE-2 / ROUGE-L を定義式から実装し、抽出型要約の 3 手法（リード法・TextRank（単語共起ベース）・LexRank（TF-IDF コサイン類似度ベース））を比較します。ニュース型（冒頭結論）と後半結論型での手法ごとの得意・不得意や、抽出型要約の限界を確認できます（CPU のみ・数秒で実行できます）。
- **CPU** · [統計的機械翻訳の基礎（IBM Model 1）と BLEU 評価](notebooks/ch4_smt_bleu.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_smt_bleu.ipynb)
  - 最終確認 2026/11/18
  - EM アルゴリズムによる IBM Model 1 の単語アライメント学習・可視化と、第 1 章から移設した BLEU の定義式実装（クリッピング・簡潔性ペナルティ・`sacrebleu` 検証・書籍 図 4.11 の再現・言い換えや否定反転での限界）を CPU のみ・数秒で体験できます。
- **GPU 必須** · [Eole による英日ニューラル機械翻訳演習](notebooks/ch4_eole.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_eole.ipynb)
  - 最終確認 2026/11/19
  - 書籍で紹介している OpenNMT-py は2024年の v3.5.1 で開発が止まっているので、後継の [Eole](https://github.com/eole-nlp/eole) を使う演習に変更しました。コマンド名（`onmt_train` → `eole train` など）と設定ファイルの書き方が少し違いますが、演習の内容は同じです。
  - Google Colab の Python 3.13 では Eole の依存ライブラリがインストールできないため、ノートブックの中で `uv` を使って Python 3.12 の環境を作っています。
- **GPU 必須** · 旧版：[OpenNMT-py によるニューラル機械翻訳演習](notebooks/ch4_opennmt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_opennmt.ipynb)
  - 最終確認 2026/11/19
  - 書籍に載せている OpenNMT-py（v3.5.1）のコマンドで演習したい場合はこちらを使ってください（新規の方は後継の Eole 版を推奨します）。Eole 版と同じく、`uv` で Python 3.12 の環境を作っています。
  - `fairseq` は2022年で開発が止まっていて、Google Colab では動かせません。
- **CPU** · [対話システムの基礎（ルールベース・検索型・タスク指向対話）](notebooks/ch4_dialogue.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_dialogue.ipynb)
  - 最終確認 2026/11/18
  - ELIZA 風の正規表現・テンプレートによるルールベース対話、TF-IDF コサイン類似度を用いた用例検索型対話に加え、意図分類・スロット抽出・対話状態管理を組み合わせた複数ターンのタスク指向対話（宿泊予約）を体験できます（CPU のみ・数秒で実行できます）。
- **GPU 推奨** · [軽量オープン LLM によるプロンプト演習とハルシネーション抑制](notebooks/ch4_llm_prompt.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch4_llm_prompt.ipynb)
  - 最終確認 2026/11/19
  - Google Colab T4 GPU 向け（API キー不要・オープンウェイトの `Qwen/Qwen2.5-1.5B-Instruct` を使用）
  - 第 1 章（深層学習の利点と課題）および第 4 章（大規模事前学習モデル）に対応し、単一の LLM による分類・要約・翻訳のプロンプト実行、[サンプルデータ](misc/phrase-annotation.csv)でのゼロショット vs フューショット比較、およびハルシネーション発生例と根拠文書付与（RAG 風プロンプト）による抑制を体験できます。

### 第5章

- **CPU** · [言語資源のクレンジング・重複排除と PII マスキング](notebooks/ch5_data_cleaning.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_data_cleaning.ipynb)
  - 最終確認 2026/11/18
  - HTML タグ・URL 除去や Unicode 正規化（NFKC）、文字 n-gram の Jaccard 係数による近似重複検出とデータリーク実験に加え、メールアドレス・電話番号・郵便番号等の個人情報（PII）マスキングおよび日本語比率・記号比率によるスパム除外を体験できます（CPU のみ・数秒で実行できます）。
- **CPU** · [形態素解析のユーザ辞書作成と単体テスト](notebooks/ch5_dictionary.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_dictionary.ipynb)
  - 最終確認 2026/11/18
  - 書籍 5-3（辞書作成）に対応し、システム辞書だけでは分割・正規化がうまくいかない専門用語を `SudachiPy` のユーザ辞書 CSV（表層形・品詞・読み・正規化形）へ登録して `sudachipy ubuild` でコンパイルし、エラー記録と単体テストで動作を検証します（CPU のみ・十数秒で実行できます）。
- **CPU** · [フレーズ分類ラベルアノテーションと品質管理](notebooks/ch5_annotation.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mamorlis/nlpbook/blob/main/notebooks/ch5_annotation.ipynb)
  - 最終確認 2026/11/18
  - 書籍に載せている演習例は楽天データセットによるものなので配布はできませんが、配布可能な宿泊レビュー風のサンプルデータ（100件）を作成し、スプレッドシート用の [Excel ファイル](misc/phrase-annotation.xlsx)と Colab 演習用の [CSV ファイル](misc/phrase-annotation.csv)を公開しました。
  - 2人の作業者による評価極性アノテーションから混同行列と Cohen の κ を計算し、不一致事例の分析・仕様書の改訂によって未知データでの一致率が向上するプロセスを体験できます。あわせて、3人以上の作業者に対する Fleiss の κ とスパマー検出、欠損あり行列や 5 段階順序尺度に対応する Krippendorff の α、学習曲線や分類器の予測確率を用いたアノテーションミス検出も扱っています。

## 練習問題

第1章から第5章までは章末に練習問題があります。それぞれの章の練習問題の[回答例](exercise.md)を掲載します。

## 正誤表

[正誤表](errata.md)を掲載します。本に関する誤りを見つけた場合は教えていただけると嬉しいです。

## リンク

[Amazon のページ](https://amzn.to/3K0j914) で購入できます（書籍版、Kindle 版ともにあります）。
EPUB/PDF 版は[技術評論社のページ](https://gihyo.jp/dp/ebook/2024/978-4-297-13864-6)から購入できます。
