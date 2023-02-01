# 最終結果
<img width="1092" alt="スクリーンショット 2023-02-01 10 40 37" src="https://user-images.githubusercontent.com/63344524/215924069-793f64d2-aa99-49cb-a389-a7d3ac7f6750.png">


GBT rankerでの実装をしたが、colabで実装していることもあってメモリ不足となり、ヒューリスティック手法に変更した。

しかし公開noteのスコアを越えることができなかった。

<img width="457" alt="スクリーンショット 2023-02-01 10 44 23" src="https://user-images.githubusercontent.com/63344524/215924561-c3ef430a-2ebe-4466-a19a-21ae7fa27c09.png">

# アイデア
・item groupbyでts間隔の平均が短い順(clicks)

・item groupbyでts間隔の平均が短い順(carts)

・item groupbyでts間隔の平均が短い順(orders)

・item groupbyでclicksされた回数順

・item groupbyでcartsに入れた回数順

・item groupbyでordersされた回数順

・session groupbyで直前にclicksされたunique itemの数が多い順

・session groupbyで直前にcartsされたunique itemの数が多い順

・session groupbyで直前にordersされたunique itemの数が多い順

・月曜日にclicksされた回数順

・日曜日にclicksされた回数順

・月曜日にcartsされた回数順

・日曜日にcartsされた回数順

・月曜日にordersされた回数順

・日曜日にordersされた回数順

## do

## done

# discussion

* [A top-down perspective on the current metric values](https://www.kaggle.com/competitions/otto-recommender-system/discussion/363874)
1. testセットのsessionはランダムに切り捨てられる
2. sessionの最後が切り捨てられた場合、それをpredictするのは簡単
3. sessionの最初で切り捨てられた場合、very hard
4. 優勝するのはsessionの最初で切り捨てられたものをうまくpredictできたモデル

* [Yes, We Can Use Test Data Leakage.](https://www.kaggle.com/competitions/otto-recommender-system/discussion/363939)
1. 直近のテストデータの傾向を使うことで、特定のユーザーの以前の行動を予測することができる

* [Top Solutions of Last Recommender Systems Competition](https://www.kaggle.com/competitions/otto-recommender-system/discussion/363950)

* [The order of appearance of type in each aid](https://www.kaggle.com/competitions/otto-recommender-system/discussion/364064)
1. 必ずしもcklicks > carts > ordersの順番であるわけではなく、clicksしていなくてもcartsやordersが可能である
2. co-visitation matrix だけでは予測漏れするaidが存在する

* [Great Resource about Session-based Recommender Systems](https://www.kaggle.com/competitions/otto-recommender-system/discussion/364099)

* [Do not disregard longer sessions -- they contribute disproportionately to the competition metric!](https://www.kaggle.com/competitions/otto-recommender-system/discussion/364375)
1. 長いsessionを切り捨てるのは必ずしも得策ではない

* [Recommendation Systems for Large Datasets](https://www.kaggle.com/competitions/otto-recommender-system/discussion/364721)
1. データセットが膨大であるため、sessionごとにcandidateを作成しそれらをランクづけする方法を取る
2. candidateは過去に購入した商品・再購入した商品・最も人気のある商品・クラスタリングに基づく類似アイテム・co-visitation matrixによる類似アイテムなどで作成することができる
3. rankerにはlgbm・xgb・sklearn・NNを使うことができる

* [30x Faster Co-Visitation Matrices using RAPIDS cuDF!](https://www.kaggle.com/competitions/otto-recommender-system/discussion/365369)
1. 改善する方法はより多くのcandidateをとより良いrerankのロジックを見つけること
2. より多くのcandidateを見つけるには新しいco-visitation matrixを作るのが簡単

* [Locate Real Users and Real Sessions EDA](https://www.kaggle.com/competitions/otto-recommender-system/discussion/366138)
1. 朝に注文するユーザーと夜に注文するユーザーに分かれることがわかった

* [Can you beat static rules with a ranker model without additional features?](https://www.kaggle.com/competitions/otto-recommender-system/discussion/366474)

* [Graph Neural Netwok , is complex to model but efficient for this task](https://www.kaggle.com/competitions/otto-recommender-system/discussion/368355)
1. GNNのモデル化は複雑だが、このタスクには有効かもしれない
2. GNNは商品の複雑な遷移を捉えることができる

* [3 dimensions Co-visitation matrix](https://www.kaggle.com/competitions/otto-recommender-system/discussion/368538)
1. これまではAが起きた時のBのco-visitation matrixを作成していたが、AかつBが起きた時のCというco-visitation matrixを作成することができる

* [What are we predicting?](https://www.kaggle.com/competitions/otto-recommender-system/discussion/368541)
1. ユーザーはOTTOのレコメンドシステムをみて商品を選んでいる
2. 実際にOTTOのサイトを見てみることが大切

* [Surprising LB 0.587 !!!Share some experimental results](https://www.kaggle.com/competitions/otto-recommender-system/discussion/370116)
1. 1ユーザーあたり200candidateで精度が向上した

# EDA
