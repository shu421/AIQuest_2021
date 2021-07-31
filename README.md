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