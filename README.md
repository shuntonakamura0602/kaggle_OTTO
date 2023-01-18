# 最終結果

# アイデア
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

# EDA
