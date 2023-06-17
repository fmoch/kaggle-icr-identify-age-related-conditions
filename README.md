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


ここで、`(N_{c})`はクラス(c)のオブザベーション数、((\log))は自然対数、(y_{c i})はオブザベーション(i)がクラス(c)に属していれば1、それ以外は0、(p_{c i})はオブザベーション(i)がクラス(c)に属しているという予想確率です。
与えられた行の提出された確率は、スコアリングされる前に再スケーリングされるため、合計が1になる必要はありません（各行は行の合計で割られます）。対数関数の極値を避けるため、各予測確率は、max(min(σ))は max(min(ᵅ,1-10-15),10-15) に置き換えられる。
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
- 2023年5月11日 - 開始日
- 2023年8月3日 -エントリー締切。出場するには、この日までに競技規則に同意する必要があります。
- 2023年8月3日 - チーム合併の締切日。この日が、参加者がチームに参加したり合併したりできる最後の日です
- 2023年8月10日 - 最終提出締切日。

## Data
競技データは、3つの年齢関連疾患に関連する50以上の匿名化された健康特性で構成されています。目標は、被験者がこれらの疾患のいずれかに罹っているかいないかを予測することである（二値分類問題）。

なお、これはコードコンペティションであり、実際のテストセットは隠されている。このバージョンでは、解答を作成するのに役立つように、正しい形式のサンプルデータをいくつか提供します。あなたの提出物が採点されるとき、このサンプルテストデータはフルテストセットに置き換えられます。完全なテストセットには、約400行があります。

- **train.csv** - The training set.
- **test.csv** - The test set. 
- **greeks.csv** - 補足的なメタデータ。トレーニングセットでのみ利用可能。
- **sample_submission.csv**

### train.csv 
|カラム名|説明|
|----|---- |
|id| 各オブザベーションの一意な識別子|
|AB-GL|56個の匿名化された健康特性。EJはカテゴリーであるが、それ以外はすべて数値である。|
|class|バイナリターゲット：1は、被験者が3つの条件のうちの1つと診断されたことを示し、0は、診断されていないことを示す|


### greek.csv
|カラム名|説明|
|----|---- |
|Alpha|年齢に関連する状態がある場合、その種類を特定する。|
|A|年齢に関連した状態はない。クラス0に対応する。|
|B, D, G|3つの加齢に関連した状態。クラス 1 に対応する。|
|Beta, Gamma, Delta|3つの実験特性を示す。|
|Epsilon|この被験者のデータが収集された日付。なお、テストセットのデータはすべてトレーニングセットが収集された後に収集されたものである。|



## 参考
|notebook|説明|
|---|---|
|[ICR IARC EDA Ensemble and Stacking baseline](https://www.kaggle.com/code/tetsutani/icr-iarc-eda-ensemble-and-stacking-baseline)|ベースライン（仮）|
|[ICR - EDA & Balanced Learning with LGBM & XGB](https://www.kaggle.com/code/mateuszk013/icr-eda-balanced-learning-with-lgbm-xgb)|EDA参考|
|[icr-identify-age](https://www.kaggle.com/code/vadimkamaev/icr-identify-age)|Tabpfnを用いたノート, LB上位 (0.11)はこのTabPFN使用している|

## NOTE
### nb
|notebook|CV|PV|説明|
|---|---|---|---|
|kg-nb_ICR_001|0.13968 ± 0.08848|0.28|[ICR IARC EDA_Ensemble and Stacking baseline](https://www.kaggle.com/code/tetsutani/icr-iarc-eda-ensemble-and-stacking-baseline) をコピーして作成|
|kg-nb_ICR_002|56.3||001ベース、中身の説明追加|

### EXP
|notebook|CV|PV|説明|
|---|---|---|---|
|kg-nb_ICR_exp_001||0.23|kg-nb_ICR_001をベースに、EDA用のノートブック作成|
|kg-nb_ICR_exp_002|-|-|飛び番号|
|kg-nb_ICR_exp_003|0.18385 ± 0.06902|0.40|001ベース、drop column変更, EDA削除|
|kg-nb_ICR_exp_004|||[icr-identify-age](https://www.kaggle.com/code/vadimkamaev/icr-identify-age) をコピーして作成, |
|kg-nb_ICR_exp_005_ver1|||003ベース, `drop_cols` =['BC', 'CL','BZ','DV']|
|kg-nb_ICR_exp_005_ver2||| `drop_cols` =['BC', 'CL','BZ','DV','AR]|
|kg-nb_ICR_exp_005_ver3|||ver2の設定のままearly_stopping_rounds = 1000 -> 10000,Early_stoppingに伴うオーバーフットを検証
|
early_stopping_rounds = 100000|

## LOG
### 20230527ß
- Join!
	- 題材としては健康状態を、いくつかの指標を用いて２値分類するテーブルコンペ。
	- データ自自体は多くない

### 20230529
- [ICR IARC EDA| Ensemble and Stacking baseline](https://www.kaggle.com/code/tetsutani/icr-iarc-eda-ensemble-and-stacking-baseline) を参考にkg-nb-ICR-001を作成
- 中身の確認、基本的には以下のような流れ
	- モデル作成
	- スタッキング

### 20230530
- kg-nbICR-001
	- 欠損値を可視化、基本的には欠損はなさそうだが、BQとELは60程度の欠損値がある

### 20230601
- kg-nbICR-001
	- ベースモデルまで写経
	- Opunutaを用いてパラメータ最適化を行っているが、一旦この部分は後回し
- 以下本モデルないで使用しているベースモデル
- XGBoost
    - CPUまたはGPUを引数で指定可能
- LightGBM
    - Modelとしては3つのパラメータ違いを設定している
- CatBoost
- HistGradientBoosting
> 	- GradientBoostingTreeはヒストグラムベースの勾配ブースティング分類ツリーアルゴリズムです。この実装はMicrosoftのLightGBMに基づいており、並列化にOpenMPを利用しています。
> 	- 大きなデータセット（n_samples> = 10000）の場合はGradientBoostingClassifierよりもはるかに高速です。
> 	- この推定器は、欠測値（NaN）でも学習できます。Scikit-Learnのv0.21.1以降では、HistGradientBoostingを利用できます。

### 20230605
- EDA用に`kg-nb_ICR_001`をベースに`kg-nb_ICR_exp_001`を作成
- DiscussにてCVとPBスコアの相関を集計していた
	-　
- 欠損値に関して以下Dで述べられている
	- [Do not worry about data points with missing values](https://www.kaggle.com/competitions/icr-identify-age-related-conditions/discussion/410843)
	- t-SNEを用いて1と0を次元削減して2次元上にプロットしクラスタリング、lgbでの予測結果をもとにした絶対誤差を色付け
	- 欠損値だけを抽出して絶対誤差を見ると、他の値と大差ない -> 欠損値そこまで影響なし
	- この人は平均値で欠損補完しているが、中央値のほうが良いかもしれない

### 20230606
- ローカルで”kg-nbICR-001”を実行したところHistGradientBoostingClassifierの引数でエラー
	- class_weight=balanced に対応していない -> sklearnアップデートで解消

### 20230607
- `kg-nb_ICR_exp_001`  -> `n_splits=4` `n_reapts=3`
	- 1st : 0.19868 ± 0.06894
	- 2nd : 0.19868 ± 0.06894
	- 3rd : 0.19868 ± 0.06894

### 20230609
- `kg-nb_ICR_exp_001` -> `kg-nb_ICR_exp_003`
- もともと`BC` と `CL` それぞれ有無でのCV確認
- そもそも各特徴量の相関を見た場合、となっており、BC及びCLは特徴量削減を行ったほうが良いという考え
	- **`BZ` vs `BC` (0.91)**
	- **`DV` vs `CL` (0.95)** 
	- **`EH` vs `FD` (0.97)**
- random_state_listsを7個にするとCL,BC除いたデータの優位性あり
|drop column|n_reapts=3_CV|n_reapts=7_CV|
|----|----|---|
|CL, BC|0.19868 ± 0.06894|**0.18587 ± 0.07086**|
|CL|0.18195 ± 0.07915 |0.19023 ± 0.07402|
|BC|0.18252 ± 0.07493|0.19101 ± 0.07822|
|None|0.19250 ± 0.07822|0.19023 ± 0.07402|

### 20230610
#### [ICR - EDA & Balanced Learning with LGBM & XGB](https://www.kaggle.com/code/mateuszk013/icr-eda-balanced-learning-with-lgbm-xgb) を参考にEDA
- 上記でも書いているがまずは王道に各特徴量の相関を確認
- KDE（カーネル密度分布）では正規分布的な広がりを見せているか、裾が長いか（LongTail)かを確認　-> 特徴量ごとで異なる
	- 上記の分布に対してスケーリング方法を検討するに当たって以下、スケーラーごとに正規分布度を比較している（直線的な右上がりになればなるほどｍ正規分布に従っている
		-  **Log Transformation** - generally works fine with right-skewed data. Requires non-negative numbers.
		-   **Square Root Transformation** - similarly to log-level transformation. Requires non-negative numbers.
		-   **Square Transformation** - helps to reduce left-skewed data.
		-   **Reciprocal Transformation** - used sometimes, when data is skewed, or there are obvious outliers. Not defined at zero.
		-   **Box-Cox Transformation** - used when data is skewed or has outliers. Requires strictly positive numbers.
		-   **Yeo-Johnson Transformation** -variation of Box-Cox transformation, but without restrictions concerning numbers.
	 - 結果としては  **Yeo-Johnson Transformation** が最も適している特徴量が多い
~~~
Tree Based modelを使用する場合はスケーリングを気にする必要はすくないが、
SVMなどを用いる場合は必要、今後Tree model以外を使用する場合は参考にする
~~~

- 特徴量の中でうまいことスケーリングできないやつの中身を確認
	-  `AR`, `BZ`, `DV` 
		- ほとんど同じ値かつ、大きな外れ値がある
		- 他のいくつかの特徴量と相関がある -> 削除することもあり？
	 - `AY`, `DF`　に関しても同様だけど他の特徴量との相関が薄い -> 削除は微妙
	 - `AR`, `BZ`, `DV` 削除した上でCVを比較すると`BZ`, `DV`それぞれ単体で削除するとCVの向上が見られた

|drop column|n_reapts=7_CV|n_reapts=10_CV|
|----|----|----|
|CL, BC, AR, BZ, DV|0.18666 ± 0.07729||
|CL, BC, BZ, DV|0.18137 ± 0.07311|0.18625 ± 0.06379|
|CL, BC, AR|0.18292 ± 0.07210||
|CL, BC, BZ|0.17243 ± 0.07241|0.18326 ± 0.06861|
|CL, BC, DV|0.17438 ± 0.07019||

- 以下、特徴量とClassのピアソン相関係数
~~~
これらはCassとの相関が小さいためBinalizationするのも有効
~~~

|drop column|n_reapts=3_CV|
|----|----|
|AH|	 +0.045|
|AR|	 +0.064|
|AY|	 +0.082|
|BC|	 +0.156|
|BZ|	 +0.112|
|CL|	 +0.017|
|DF|	 +0.064|
|DV|	 +0.015|
|EP|	 -0.068|
|GE|     -0.071|
|Class|	 +1.000|

- t-SNEを用いたクラスタリングも実施している
	- `Class=1`は2D及び3Dでみてもそれぞれクラスターを形成している
	  -> 何かしらストーリはあるはず
- Dropする列でFor回す関数を作成すれば捗りそう…

####  [icr-identify-age](https://www.kaggle.com/code/vadimkamaev/icr-identify-age)を読み解く
- Tabpfnを用いたノートブック_コード自体はシンプル
	- 現時点上位陣はほとんど用いている
> - `SimpleImputer()` 
> - missing_values：置き換える値
> - strategy：統計値の種類：デフォルトは平均値
-   fill_value：strategyがconstantになっている場合に、整数や文字列を指定して置き換えるまずは平均値を設定して欠損値の置き換えを行っていきます。

### 20230612
- `kg-nb_ICR_exp_003` サブ
	- CV：0.18385 ± 0.06902
	- LB：0.40
		- `drop_cols` =['BC', 'CL','BZ']
		- `kfold` = 'skf'
		- `n_splits` = 4
		- `n_reapts` = 20
		- `random_state` = 71
		- `n_estimators` = 99999
		- `early_stopping_rounds` = 1000
		- `verbose` = False
		- `device` = 'cpu'
	 - LBは悪化しているが、より汎化したと考えるべき？？
	 - 少量データ過ぎて逆に難しい

### 20230613
-  `kg-nb_ICR_exp_003`  -> `kg-nb_ICR_exp_005`
	- `drop_cols` =['BC', 'CL','BZ','DV']

-　[Binary classification VS multi label(using Alpha in greeks)](https://www.kaggle.com/competitions/icr-identify-age-related-conditions/discussion/413287)
	- マルチラベル分類か二項分類どちらが優れているか->二項分類
	- Greeksを用いると概ねスコアアップが期待できるが、Alphaがオーバーフィットを催すかも

- [lightgbmで二値分類の一連の流れをしたメモ](https://qiita.com/d_desuyon/items/807e01311ad08570ee78)
	- 参考にLightgbmでのbinary classifier実装把握

### 20230614
-  `kg-nb_ICR_exp_005` ver2
	- `drop_cols` =['BC', 'CL','BZ','DV','AR]
- Versionで管理することにしました

-  Robust Validationに関する内容のNote
	- https://www.kaggle.com/competitions/icr-identify-age-related-conditions/discussion/412911

### 202030617
- `kg-nb_ICR_exp_005_ver3`
	- 以下ノート参考にモデル変更
		- https://www.kaggle.com/competitions/icr-identify-age-related-conditions/discussion/417838
	- ver2の設定のままearly_stopping_rounds = 1000 -> 10000,
	- Early_stoppingに伴うオーバーフットを検証

