# Model
# 1.Random forest(Bagging,randomly,harder to overfit,easier to tune)
> creates multiple decision tree models and then combines them into strong model to produce better results than any of the single models individually


### conbine the feature
```
X_feature=pd.concat([data["body_len"],data["punct%"],pd.DataFrame(X_tfidf.toarray())],axis=1)
```
### build Grid-search
```
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import precision_recall_fscore_support as score
from sklearn.model_selection import train_test_split

X_train,X_test,Y_train,Y_test=train_test_split(X_feature,data["label"],test_size=0.2)

def train_RF(n_est,depth):
    rf=RandomForestClassifier(n_estimators=n_est,max_depth=depth,n_job=-1)
    rf_model=rf.fit(X_train,Y_train)
    y_pred=rf.model.predict(X_test)
    precision,recall,fscore,support=score(Y_test,Y_pred,pos_label="spam",average="binary")
    print("EST:{}/Depth:{}-----Precision:{}/Recall:{}/Accurary:{}".format(n_est,depth,round(precision,3),round(recall,3),round((y_pred==Y_test).sum()/len(y_pred),3)))
      
      
for n_est in [10,50,100]:
    for depth in [10,20,30,None]:
        train_RF(n_est,depth)
```
### Exploring parameter setting using GridSearchCV
```
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import GridSearchCV

rf=RandomForestClassifier()
param={"n_estimators":[10,150,300],"max_depth":[30,60,90,None]}

gs=GridSearchCV(rf,param,cv=5,n_jobs=-1)
gs_fit=gs.fit(X_tfidf,data["label"])# X_train,Y_train
pd.DataFrame(gs_fit.cv_results_).sort_values("mean_test_score",ascending=False)[0:5]# the former 5

```
# 2.Gradient boosting(Boosting,iterative,easier to overfit,harder to tune)
>ensemble learning method that takes an iterative approach to combining weak learners to create a strong  learner by focusing on mistakes of prior iterations

### Bulid Grid Search
```
from sklearn.ensemble import  GradientBoostingClassifier
from sklearn.metrics import precision_recall_fscore_support as score
from sklearn.model_selection import train_test_split

X_train,X_test,Y_train,Y_test=train_test_split(X_feature,data["label"],test_size=0.2)

def train_GB(est,depth,Ir):
    gb=GradientBoostingClassifier(n_estimators=est,max_depth=max_depth,learning_rate=Ir)
    gb_model=gb.fit(X_train,Y_train)
    y_pred=gb.model.predict(X_test)
    precision,recall,fscore,support=score(Y_test,Y_pred,pos_label="spam",average="binary")
    print("EST:{}/Depth:{}-----Precision:{}/Recall:{}/Accurary:{}".format(n_est,depth,round(precision,3),round(recall,3),round((y_pred==Y_test).sum()/len(y_pred),3)))
      
      
for est in [50,100,150]:
    for max_depth in [3,7,11,15]:
       for Ir in [0.01,0.1,1]:
          train_GB(est,max_depth,Ir)
```
### Exploring parameter setting using GridSearchCV
```
from sklearn.ensemble import  GradientBoostingClassifier
from sklearn.model_selection import GridSearchCV

gb=GradientBoostingClassifier()
param={"n_estimators":[100,150],"max_depth":[7,11,15],"learning_rate":[0.1]}

gs=GridSearchCV(gb,param,cv=5,n_jobs=-1)
cv_fit=gs.fit(X_tfidf,data["label"])# X_train,Y_train
pd.DataFrame(cv_fit.cv_results_).sort_values("mean_test_score",ascending=False)[0:5]# the former 5

```
