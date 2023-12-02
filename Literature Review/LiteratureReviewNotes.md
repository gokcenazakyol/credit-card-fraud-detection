# Literature Review Notes

## [Random Forest for Credit Card Fraud Detection](https://github.com/gokcenazakyol/credit-card-fraud-detection/blob/main/Literature%20Review/Random_forest_for_credit_card_fraud_detection.pdf)
### Abstract
- Effictive fraud detection method is important since it can identify a fraud in time when a criminal uses a stolen card to consume. One method is to make full use of the historical transaction data including normal transactions and fraud ones to obtain normal/fraud behavior features based on machine learning techniques, and then utilize these features to check if a transaction is fraud or not. In this paper, two kinds of random forests (They are Random-tree-based random forest and CART-based one, respectively.) are used to train the behavior features of normal and abnormal transactions. We make a comparison of the two random forests which are different in their base classifiers, and analyze their performance on credit fraud detection. The data used in our experiments come from an e-commerce company in China.
### Introduction
- Fraud detection is a process of monitoring the transaction behavior of a cardholder in order to detect whether an in- coming transaction is done by the cardholder or others.
### Random Forest
- Ensemble methods can solve these problems by combine a group of individual decisions in some way and are more accurate than single classifiers [21]. Random forest, one of ensemble methods, is a combination of multiple tree predictors such that each tree depends on a random independent dataset and all trees in the forest are of the same distribution [20]. The capacity of random forest not only depends on the strength of individual tree but also the correlation between different trees.
#### Random-tree-based random forest
- The training set of each tree is a collection of bootstrapped samples selected randomly from the standard training set with replacement. At each internal node, it randomly selects a subset of attributes and computes the centers of different classes of the data in current node.
<img width="460" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/8adc9833-4b43-4cc1-a322-56ed1e34ca23">
<img width="502" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/4a9520a2-85a3-4d37-8545-00405de01f26">

#### CART-based random forest
- The base classifier of random forest II is CART (Classifica- tion and Regression Trees) [24] whose training set also comes from bootstrapped samples.
- At each node, it splits dataset by choosing the best attribute in a subset of attributes according to Gini impurity which measures uncertainty of dataset. The subset of attributes are randomly selected from all attributes of dataset. According to the advice from Breiman, the size of the subset is set to the square root of the number of all attributes [20].

<img width="507" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/1653376e-cd0a-45a2-982a-0940448dc5c3">
<img width="554" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/4200e81b-6245-4ae4-a792-4552730696a9">

- The main difference between the two algorithms is the way of splitting of nodes. In type-I random forest, the data are distributed by comparing distances between records and two centers; In type-II random forest, the data are distributed according to the attribute which has minimum gini impurity. They all have their own advantages and drawbacks. In Algo- rithm I, it could be faster in computing centers but slower in distributed records, because it has to compute distances between centers and all records. In algorithm II, although it could be slower in computing gini impurity for attributes, it would be faster in the process of distributing data.

### Experiment
#### Performance measures
- Accuracy rate is not enough to measure the performance of a random forest model when the data is significantly imbalanced.For instance, a default prediction of all instances into the majority class will also have a high value of accuracy.
- Precision rate is a measure of the result of prediction and recall rate measures the detection rate of all fraud cases. F-measure is the harmonic mean of recall and precision. Intervention rate is a measure of degree of intercept of normal instances.
<img width="485" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/06507dae-7010-4511-9a49-f5c3d4e6fb25">
#### Experimental dataset
- The dataset used in the paper comes from an e-commerce company of China, and consists of fraudulent and legitimate B2C transactions from November 2016 to January 2017.
- The total original dataset contains more than 30,000,000 individual transactions.
- In the dataset only about 82,000 transactions were labeled as fraud, meaning the fraud ratio of 0.27% and dataset imbalance problem should be taken into consideration.
#### Experiment I
- The subset used in this experiment consists of all the fraud transactions in January 2017 and 150,000 legal transactions randomly selected from all the legal transactions in January 2017 in order to balance the positive and negative samples of the training set.
- Then 70% transactions of the above data are as the training dataset, and the rest as the testing dataset.
- The comprehensive performance of random forest II is much more suitable for application on this experiment subset.
<img width="489" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/d0c7fce1-1442-4cd6-8506-d0d23af7cb64">
#### Experiment II
- The original dataset has a fraud ratio of 0.27%, denoting that there is a seriously data imbalance problem. This experiment explores the relation between a model’s performance and the ratio of legal and fraud transactions.
<img width="520" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/0585c399-643b-43a5-8a57-efd9c0139eac">

- As fraud transactions of the dataset are limited, this experiment adopts the random under-sampling method [6] on legal transactions. Thus, all transactions labeled by fraud are preserved as the base for regulating the under-sampling ratio. As shown in Table IV, ten subsets are extracted with the ratio of legal and fraud transactions from 1:1 to 10:1.
- Considering random forest II is more practical, this experi- ment uses it to explore the influence of different ratio of legal and fraud transactions on fraud transactions detection. For any one of the above ten datasets.
<img width="468" alt="image" src="https://github.com/gokcenazakyol/credit-card-fraud-detection/assets/74296174/59219094-6fe3-4f7b-b8f5-4b9ee5733f72">

- As shown in Fig. 3, the accuracy of fraud detection is increasing with the growth of legal transactions, while the re- call is decreasing. However, the F-measure gets the maximum value when the ratio of legal and fraud transaction is 5:1. A perspective can be get that random forest II is suitable for the balance class problem and under-sampling method is effective to deal with class unbalance problem. The performance of fraud detection models is related to the ratio of legal and fraud transactions, and the best results should be obtained by practical testing.

#### Experiment III
- We also apply other algorithms in our experiments, such as support vector machine, naive bayes an nerual network. But the results of them are worse than random forest.
### Conclusions
- The algorithm of random forest itself should be improved. For example, the voting mechanism
assumes that each of base classifiers has equal weight, but some of them may be more important than others. Therefore, we also try to make some improvement for this algorithm.
-------------------------------------------------------------------
