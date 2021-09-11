# AIQuest_2021
AI Quest2021アセスメントのリポジトリです。
最終結果は、
- cv:103.575077379
- lb: 144.0033488
- 964人中23位  

でした。[Twitter](https://twitter.com/shu421_)をやっていますので、ぜひフォローお願いします。アセスメントに関して質問があれば、slackのアセスメント_チュートリアルチャンネルで回答いたします。

# 解法
mainフォルダの中にある、nb001.ipynbが最終サブミッションです。内容を簡単にまとめておきます。
- 前処理
  - 型がobjectのカラムは、label encodingと、target encodingをしました。
  - レビュー日やアメニティなどは、one hot encodingをしています。
  - descriptionは、bag-of-wordsやTF-IDFを試しましたが精度が上がらなかったので、単純に文字数だけカウントしています。
  - cityをキーにした、z得点(zscore)、偏差(deviation)、標準偏差(std)の集約特徴量を使用しています。meanやsumも試しましたが、精度改善されませんでした。
    - cityごとに宿泊施設の値段は違うと予想しました
    - kmeansによるクラスタリング結果をキーにして集約特徴量を作成してみましたが、精度は悪化しました。
- モデル
  - LightGBMを使用しています。今回は1モデルの出力をそのまま提出しましたが、アンサンブルすればよかったなと思ってます。
  - 5 KFold
  - 学習率: 0.1
  - パラメータチューニングを試しましたが、過学習してしまったので、デフォルトのパラメータを使用しています。

# 効いたもの
- target encoding ### 20210911追記: 実装ミスしていて、target encodingが反映されていませんでした。
- 各種集約特徴量
- descriptionの長さ

# 効かなかったもの
- knn
- kmeans
- optuna hyperparameter tuning(やり方が間違ってたかも)
- count encoding


# Log
- 以下はメモです。
### 20210723
- nb000
  - rmse: 107.23996925306717
  - lb: 147.9472109
- nb000 add nun nan
  - rmse : 107.50887532119695
  - lb: 148.1268360
  - cvとlb相関取れてる
- description落としただけ
  - cv: 104.29192406749749
- add len description
  - cv: 104.24454861684883
  
- TF-IDF、features選択しても精度上がらなかった
- kmeansもあまり効かない
  - これに関しては、組み合わせによって0.02くらい精度上がった。怖いから採用しない
- bedroomsをキーにした集約特徴量効かんなぁ
- count encoding 効かない
- cityキーにするとcv0.1改善

- nb001
- target encoding かなりきく
  - sub_nb001
  - cv: 103.57507737973427
- bedroomあたりのbedの数だめだった

- nb003
  - kmeans実験用

### 20210724
- 効かないもの
  - log
  - n_amenities

- nb005
  - top50 importanceでkmeansしたら0.01上がった
  - 再現性なかった

  ### 20210731
  - nb007
    - knn
    - 少しスコア下がるっぽいからknnの特徴選択する

  ### 20210801
  - nb008
    - xgboost

  - nb009
    - tuning

- nb010
  - fold=5, cv: 103.57507737973427
  - fold=15, cv: 102.73201801142532
  - fold=20, cv: 102.40243881308743
  - fold=25, cv: 102.53350343999037

- sub_nb010
  - チューニング、fold5→20
  - cv: 100.67796832289454
  - lb: 144.3624826

  - fold=5
  - cv: 101.72109494522418
  - lb: 144.5972590
