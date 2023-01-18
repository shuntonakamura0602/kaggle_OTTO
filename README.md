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
# EDA
