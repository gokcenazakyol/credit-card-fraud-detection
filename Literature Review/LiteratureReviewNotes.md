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
## [AdaBoost and Majority Voting for Credit Card Fraud Detection](https://github.com/gokcenazakyol/credit-card-fraud-detection/blob/main/Literature%20Review/Credit_Card_Fraud_Detection_Using_AdaBoost_and_Majority_Voting.pdf)
### Abstract
- Credit card fraud is a serious problem in financial services. There is a lack of research studies on analyzing real-world credit card data owing to confidentiality issues. In this paper, machine learning algorithms are used to detect credit card fraud. Standard models are first used. Then, hybrid methods which use AdaBoost and majority voting methods are applied. The experimental results positively indicate that the majority voting method achieves good accuracy rates in detecting fraud cases in credit cards.
  
### Introduction
- Fraud is a wrongful or criminal deception aimed to bring financial or personal gain. Fraud detection is needed when a fraudulent transaction is attempted by a fraudster.
### Machine Learning Methods
- Sayfa 4'ün başında güzel bir tablo var, onu kullanabiliriz.
#### Majority Voting
- Majority voting is frequently used in data classification, which involves a combined model with at least two algorithms. Each algorithm makes its own prediction for every test sample. The final output is for the one that receives the majority of the votes.
#### AdaBoost
- Adaptive Boosting or AdaBoost is used in conjunction with different types of algorithms to improve their performance. The outputs are combined by using a weighted sum, which represents the combined output of the boosted classifier.
- AdaBoost tweaks weak learners in favor of misclassified data samples. It is, however, sensitive to noise and outliers. As long as the classifier performance is not random, AdaBoost is able to improve the individual results from different algorithms.

### Experiments
#### Experimental Setup
- In the credit card data set, the number of fraudulent transactions is usually a very small as compared with the total number of transactions. With a skewed data set, the resulting accuracy does not present an accurate representation of the system performance. As such, under-sampling is used in this paper to handle the skewed data set.
- While there is no best way of describing the true and falsepositives and negatives using one indicator, the best general measure is the Matthews Correlation Coefficient (MCC). It is a balanced measure, even when the classes are from different sizes.
#### Benchmark Data
- A publicly available data set containing a total of 284,807 transactions made in September 2013 by European cardholders. The data set contains 492 fraud transactions, which is highly imbalanced.
- Accuracy rates are high, generallya round 99%. This however is not the real outcome, as the rate of fraud detection varies from 32.5% for RT up to 83% for NB. The rate of non-fraud detection is similar to the accuracy rates, i.e., the non-fraud results dominate the accuracy rates. SVM produces the highest MCC score of, while the lowest is from NB.
- In addition to the standard models, AdaBoost has been used with all 12 models. Accuracy and non-fraud detection rates
are similar to those without AdaBoost. However, the fraud detection rates increase from 79.8% to 82.3% for SVM. Some models suffer a minor reduction in the fraud detection rate up to 1%. The MCC rates show very minor changes.
- Based on the models that produce good rates, the majority voting method is applied to the models. The accuracy rates are all above 99%, with DS + GBT yields a perfect non-fraud rate. The best fraud detection rate is achieved by NN + NB at 78.8%. The highest MCC score at 0.823 is yielded by NN + NB, which is higher than those form individual models.
#### Real World Data
- A real credit card data set from a financial institution in Malaysia is used in the experiment. It is based on cardholders from the South-East Asia region from February to April 2017. A total of 287,224 transactions are recorded, with 102 of them classified as fraud cases.
- All accuracy rates are above 99%, with the exception of SVM at 95.5%. The non-fraud detection rates
of NB, DT, and LIR are at 100%, while the rest are close to perfect, with the exception of SVM. The best MCC rates are from NB, DT, RF, and DS, at 0.990. The fraud detection rates vary from 7.4% for LIR up to 100% for RF, GBT, DS, NN, MLP, and LOR.
- Similar to the benchmark experiment, AdaBoost has been used with all individual models. The accuracy and non-fraud detection rates are similar to those without AdaBoost. AdaBoost helps improve the fraud detection rates. This clearly indicates the usefulness of AdaBoost in improvement the performance of individual classifiers.
- The majority voting method is then applied to the same models used in the benchmark experiment. The results of majority voting are better than those of individual models.
- To further evaluate the robustness of the machine learning algorithms, all real-world data samples are corrupted noise, at 10%, 20% and 30%. Noise is added to all data features. With the addition ofnoise, the fraud detection rate and MCC rates deteriorate, as expected.

### Conclusions
- The MCC metric has been adopted as a performance measure, as it takes into account the true and false positive and negative predicted outcomes.
-  A perfect MCC score of 1 has been achieved using AdaBoost and majority voting methods.
-  To further evaluate the hybrid models, noise from 10% to 30% has been added into the data samples. The majority voting method has yielded the best MCC score. This shows that the majority voting method offers robust performance in the presence of noise.
- For future work, the methods studied in this paper will be extended to online learning models. In addition, other online
learning models will be investigated.
