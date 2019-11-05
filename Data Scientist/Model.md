# MODEL
### LSTM
LSTM(long short term memory)LSTMを使うべきときは遠い過去の情報まで参考にしないと予測できない

### 决策树
决策树是一组通常用于分类的机器学习算法。因为它们简单有效

### XGBoost
XGBoost 用在分类上（分类树1，0）
下一棵决策树输入样本会与前面决策树的训练和预测相关。

### random foreast
random foreast（随机森林）算法，各个决策树是独立的、每个决策树在样本堆里随机选一批样本，
随机选一批特征进行独立训练，各个决策树之间没有啥毛线关系

### QUEST
QUEST quick unbiased and efficient statistic tree,use statistic tests to examines
fewer cut points by performing calculations.
use deffer test appropriate for different variable types and rank the p-Value

### Chaid
Chaid chi-square Automatic interaction biased toward branches with a large number of child nodes
tree are wider than other technoque

### cart
cart classfication and regression trees
slow--check all possible split technoque
cart has some missing value method with quest

>F-test in continous and ordinal variables
chi-square in categorical values

>chi-square is small,close to 0,means there is a statistically signaficant relationship between gender and survial.if 
it near 1.0 it would not be significant

>p-Value=probability value.indicating any other values below 0.05 are significant at 95% confidence.

>F-test is comparaing signal to noise
the larger F-score is the more significant the difference between the two groups are

### bagging
bagging ---build mutiple models and compare all of those results.

resampling --- repeat take sample
10different models with 10 differe t resamples

shortage:you can see the data from regression tree,however , bagging is a black box.
sometimes you also can use it to do the feature selection.ex:use 100models to figure out what feature used less


### random Forest
random forest cart +bagging   black box 

boosting----to find out where it is mistakes,build the model to see what it got correct and in correct then adjust the weights and give the mistake added weight. the one got correct will get less weight then repeat.

### chaid
use different values to compare chi-square,the less the better, the less value of P can be used to root.

### cart 
gini coefficient is commonly used measure of inequality and represent the income distribution of a nation's residents.

set minimum change in imparity 0.001--0.0001 to grow the tree bigger

### confusion matrix
      predict value
         0  1
true 0  TN FP
Value 1 FN TP
N=Negative P=Positive

accuracy=(TP+TN)/all
Precision=TP/(TP+TN)
recall=TP/(TP+FN)
F1 the larger the better 2/F1=1/Precision+1/Recall
AUC(the area inside ROC 0.5-1 the larger the better)

