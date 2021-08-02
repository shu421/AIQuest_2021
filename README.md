# AIQuest_2021

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