# kaggle-icr-identify-age-related-conditions
icr-identify-age-related-conditionsコンペのリポジトリ

  
- result
	- public: ●● 
		- rank: ●●/●●
	- private: ●●
		- rank: ●●/●●

## Overview
### 競技の目的
このコンペティションの目的は、ある人が3つの病状のいずれかを持っているかどうかを予測することです。あなたは、その人が3つの医学的状態のいずれか1つ以上を持っているか（クラス1）、または3つの医学的状態のいずれも持っていないか（クラス0）を予測するように求められています。あなたは、健康特性の測定値に基づいて訓練されたモデルを作成することになります。
ある人がこれらの病状にあるかどうかを判断するには、患者から情報を収集するための長くて侵入的なプロセスが必要です。予測モデルを使えば、病状に関連する主要な特徴を収集し、その特徴を符号化することで、このプロセスを短縮し、患者の情報を非公開にすることができます。
あなたの研究は、研究者が特定の特性の測定値と潜在的な患者の状態との間の関係を発見するのに役立ちます。

### コンテキスト
年齢は単なる数字に過ぎないと言われますが、加齢に伴う健康上の問題は山ほどあります。心臓病や認知症、難聴や関節炎など、加齢は多くの病気や合併症の危険因子となります。バイオインフォマティクスの成長分野には、生物学的老化を遅らせたり逆転させたり、加齢に関連する主要な病気を予防するための介入策を研究するものがあります。データサイエンスは、たとえサンプル数が少なくても、多様なデータで問題を解決するための新しい手法を開発する役割を担うことができます。
現在、病状予測にはXGBoostやランダムフォレストなどのモデルが使われていますが、その性能は十分とは言えません。人命がかかった重大な問題を扱う場合、モデルは異なるケース間で確実かつ一貫して正しい予測を行う必要があります。
2015年に設立されたコンペティションホストのInVitro Cell Research, LLC（ICR）は、再生医療と予防的個別化医療に焦点を当てた民間企業である。ニューヨークの大地にある彼らのオフィスとラボは、最先端の研究スペースを提供しています。インビトロ・セル・リサーチのサイエンティストは、老化した人を早く修復する方法を研究するという彼らのミッションを導き、定義することで、彼らを際立たせています。
このコンペティションでは、バイオインフォマティクスにおける重要な問題を解決するために、健康状態の特徴的なデータの測定に取り組みます。最小限のトレーニングで、ある人が3つの病状のいずれかに該当するかどうかを予測するモデルを作成し、既存の方法を改善することを目指します。
成長著しいバイオインフォマティクス分野の発展に貢献し、多様なデータで複雑な問題を解決する新しい手法を探求することができます。


### Submit
提出された作品は、**バランスのとれた対数損失**を用いて評価されます。全体的な効果は、各クラスが最終的なスコアに対してほぼ等しく重要であるようなものである。
**各観測はクラス0かクラス1のいずれか**である。各観測について、各クラスの確率を提出する必要があります。その時の計算式は


$Log Loss= \frac{-\frac{1}{𝑁_0}\sum_{i=1}^{N_0}\log{𝑝_{0𝑖}}−\frac{1}{𝑁_1}\sum_{i=1}^{N_1}\log{𝑝_{1𝑖}}}{2}$


ここで、(N_{c})はクラス(c)のオブザベーション数、(˶‾‾)は自然対数、(y_{c i})はオブザベーション(i)がクラス(c)に属していれば1、それ以外は0、(p_{c i})はオブザベーション(i)がクラス(c)に属しているという予想確率です。
与えられた行の提出された確率は、スコアリングされる前に再スケーリングされるため、合計が1になる必要はありません（各行は行の合計で割られます）。対数関数の極値を避けるため、各予測確率ᑝは、max(min(σ))
 は max(min(ᵅ,1-10-15),10-15) に置き換えられる。
- 提出ファイル
テストセットの各IDについて、2つのクラスのそれぞれの確率を予測する必要があります。ファイルはヘッダを含み、以下の形式でなければならない：
```
ID,class_0,class_1
00eed32682bb,0.5,0.5
010ebe33f668,0.5,0.5
02fa521e1838,0.5,0.5
040e15f562a2,0.5,0.5
046e85c7cc7f,0.5,0.5
```

## Timeline
- 2023年2月16日 - 開始日。
- 2023年5月11日 エントリー締切。出場するためには、この日までに競技規則を承諾する必要があります。
- 2023年5月11日 - チーム合併の締切日です。この日が、参加者がチームに参加したり、合併したりできる最後の日です。
- 2023年5月18日 - 最終提出期限。
- すべての締め切りは、特に断りのない限り、該当日の午後11時59分（UTC）になります。主催者が必要と判断した場合、コンテストのタイムラインを更新する権利を有します。

## Data
### データセット説明
- このコンペティションの目的は、タンパク質の存在量データを用いてパーキンソン病（PD）の経過を予測することです。PDに関与するタンパク質の完全なセットは、まだ未解決の研究課題であり、予測価値を持つタンパク質は、さらに調査する価値があると思われます。このデータセットの中核は、数百人の患者から収集した脳脊髄液（CSF）サンプルの質量分析から得られたタンパク質存在量値です。各患者は、PDの重症度評価を行いながら、複数年にわたり複数のサンプルを提供しました。
- 時系列コードのコンペティションです。テストセットのデータを受け取り、Kaggleの時系列APIを使って予測を行っていただきます。
<br>

## ファイル
-  train_peptides.csv 
- train_proteins.csv
- train_clinical_data.csv
- supplemental_clinical_data.csv 

### train_peptides.csv 
- ペプチドレベルの質量分析データです。ペプチドはタンパク質の構成サブユニットである。

|カラム名|説明|
|----|---- |
|visit_id | 訪問のIDコード。|
|visit_month | 患者の最初の訪問から相対的に見た、訪問の月。|
|patient_id | 患者のIDコード。|
|UniProt | 関連するタンパク質のUniProt IDコード。1つのタンパク質に複数のペプチドが存在することが多い。|
|Peptide | ペプチドに含まれるアミノ酸の配列。関連するコードについては、この表を参照してください。稀なアノテーションは、この表に含まれない場合もある。テストセットには、トレーニングセットに含まれていないペプチドが含まれることがあります。|
|PeptideAbundance | サンプルに含まれるアミノ酸の頻度です。|

### train_proteins.csv
- ペプチドレベルのデータから集約したタンパク質発現頻度。

|カラム名|説明|
|----|---- |
|visit_id | 訪問のIDコード。|
|visit_month | 患者の最初の訪問から相対的に見た、訪問の月。|
|patient_id | 患者のIDコード。|
|UniProt | 関連するタンパク質のUniProt IDコード。1つのタンパク質につき数個のペプチドが存在することが多い。テストセットには、トレーニングセットに含まれていないタンパク質が含まれる場合がある。|
|NPX | Normalized protein expression（正規化タンパク質発現量）。サンプルに含まれるタンパク質の出現頻度。ペプチドを繰り返し含むタンパク質もあるため、構成ペプチドと1対1の関係にはない可能性があります。|

### train_clinical_data.csv
|カラム名|説明|
|----|----| 
|visit_id | 訪問のIDコード。|
|visit_month | 患者の最初の訪問から相対的に見た、訪問の月。|
|patient_id | 患者のIDコード。|
|updrs_[1-4] | 統一パーキンソン病評価尺度のパートNに対する患者のスコア。数値が高いほど症状が重いことを示す。パート1では気分や行動、パート3では運動機能など、各サブセクションは症状の異なるカテゴリーをカバーしています。|
|upd23b_clinical_state_on_medication | UPDRS評価時にレボドパなどの薬物を服用していたかどうか。主にパート3（運動機能）のスコアに影響を及ぼすと予想される。これらの薬はかなり早く（1日単位で）切れるので、患者は1ヶ月に2回、薬の服用と未服用の両方で運動機能検査を受けることが一般的です。|

### supplemental_clinical_data.csv 
- CSF サンプルが添付されていない臨床記録。このデータは、パーキンソン病の典型的な進行に関する追加的な文脈を提供することを意図している。train_clinical_data.csvと同じカラムを使用する。

### example_test_files/ 
APIがどのように機能するかを説明するためのデータ。APIが提供するカラムと同じカラムが含まれます（つまり、更新カラムはありません）。

### amp_pd_peptide/ 
APIを有効にするためのファイルです。APIは、5分以内にすべてのデータ（1,000人未満の追加患者）を配信し、0.5GB未満のメモリを確保することを期待します。APIが提供する簡単なデモは、こちらでご覧いただけます。

### public_timeseries_testing_util.py 
カスタムオフラインAPIテストの実行を容易にすることを目的としたオプションファイルです。詳細はスクリプトのdocstringを参照してください。


## 参考
|notebook|説明|
|---|---|
|[AMP® - PDPP - Baseline](https://www.kaggle.com/code/fmotch/amp-pdpp-baseline)|ベースライン（仮）|
|[AMP - EDA + Models](https://www.kaggle.com/code/craigmthomas/amp-eda-models)|EDA一番Vote多い|
|[AMP - EDA + Models 日本語訳&コード解説](https://www.kaggle.com/code/ihorin/amp-eda-models)|上記の日本語翻訳版|
|[AMP® - PDPP - EDA](https://www.kaggle.com/code/gunesevitan/amp-pdpp-eda)|EDA それぞれのタンパク質ごとに分析実施
|[Explain Dataset, Test API, Cross-Validation Tips](https://www.kaggle.com/code/vitalykudelya/explain-dataset-test-api-cross-validation-tips)|参考情報多数
|[How many Patients are in the Test Part? We have an answer...](https://www.kaggle.com/competitions/amp-parkinsons-disease-progression-prediction/discussion/398758)|PLでのテスト方法記載。PLでのスコアは実際には50人程度の人数。なのであまり当てにならない。いいモデルを作ればShakeupするだろうとのこと
|[Parkinson's Disease MDS-UPDRS End-to-End Baseline](https://www.kaggle.com/code/gokifujiya/parkinson-s-disease-mds-updrs-end-to-end-baseline#Import-Libraries)|TrainデータとテストデータとしてClinicとProteinデータをPivotで作成（UPDRS1~4をそれぞれ別ファイルで扱う）。タンパク質の特徴量選択はSelectKSelectKBestで、最適なものを5つ抽出し、線形回帰している。|
|[Parkinson's Disease MDS-UPDRS Features Selection](https://www.kaggle.com/code/gokifujiya/parkinson-s-disease-mds-updrs-features-selection#Random-Forest-Regressor-Model-with-Univariate-Feature-Selection-and-PCA)|上記参考に複数のモデル作成。特徴量選択に焦点を当てている。|

## NOTE
|notebook|score|説明|
|---|---|---|
|kg-nb_PDPP_001|56.3|[AMP® - PDPP - Baseline]そのまま|
|kg-nb_PDPP_002|56.3|001ベース、中身の説明追加|
|kg-nb_PDPP_003| |[Parkinson's Disease MDS-UPDRS Features Selection]ベースで作成|
|kg-nb_PDPP_004| 57.2|[[Update: 57.4] Train + Inference RandomForest](https://www.kaggle.com/code/bibanh/update-57-4-train-inference-randomforest)ベースで作成。TrainセットはFirst Visitのみ。（０Visit)
|kg-nb_PDPP_005| 57.2|[[Update: 57.4] Train + Inference RandomForest](https://www.kaggle.com/code/bibanh/update-57-4-train-inference-randomforest)NB004と同じだが説明を追記している（０Visit)
|kg-nb_PDPP_006| 57.2|[[Update: 57.4] Train + Inference RandomForest](https://www.kaggle.com/code/bibanh/update-57-4-train-inference-randomforest)NB0041|
|kg-nb_PDPP_007| 57.9|005ベースにXGboostを追加|



## LOG
### 20230409
- 初サブ
  - ベースライン（仮）として以下ノートブックをそのまま提出
  - [AMP® - PDPP - Baseline](https://www.kaggle.com/code/fmotch/amp-pdpp-baseline)


