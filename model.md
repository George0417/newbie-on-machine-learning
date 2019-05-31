# Bulid Model and Check Accuracy


# naive_bayes
** using data of customer behavior to do Propensity analysis, know the probability of purchase**
**data: demographics of customer like age,income,family,and way of recive recommend like mail ,go to shop, online**
```
from sklearn.naive_bayes import GaussianNB

classifier=GaussianNB()
classifier=classifier.fit(pred_train,tar_train)

predictions=classifier.predict(pred_test)

sklearn.metrics.confusion_matrix(tar_test,predictions)#analyze accuracy of predictions

sklearn.metrics.accuracy_score(tar_test,predictions)

### probability computation to show the probability for the prospect to buy the product
pred_prob=classifier.predict_proba(pred_test)
pred_prob[0,1]

### real time predictions
browsing_data=np.array([0,0,0,0,0]).reshape(1,-1)
print("New visitor: propensity :",classifier.predict_prob(browsing_data)[:,1])
#[0,0,0,0,0]means result of each feature amounts 
```

# Marked basket analysis
**using data sale transaction items to find items bought together**
**the goal is to create customer group preference to give a recommend**
**Data:  demographics of customer like age,income,family,and see transactions like record of bought goods**

>process is 1.using clusters(K-means/KNN)to create customer group ,through using sales transaction data to predict affinity score between the customer group and the product

# collaborative filter 
**Data: user,item,affinity score**
**for each item,build a list of other items to recommend based on user-item affinities**

```
#the more number of customers who buy both the products,the higher affinity score is 

#get list of unique items
itemlist=list(set(useritemdata["itemid"].tolist()))

#get count of users
usercount=len(set(useritemdata["itemid"].tolist()))

#create an empty data frame to store item affinity scores for items
itemaffinity=pd.DataFrame(columns=("item1","item2","score"))
rowcount=0

#for each item in the list, compare with other items
for ind1 in range(len(itemlist)):
    
    #get list of users who bought this item 1.
    item1users =useritemData[useritemData.itemid==itemlist[ind1]]["userid"].tolist()
    
    #get item2  - items are not item 1 or those are not analyzed already
    for ind2 in range(ind1,len(itemlist)):
      
       if(ind1==ind2):
          continue
          
       #get list of users who bought this item 2.
      item2users =useritemData[useritemData.itemid==itemlist[ind1]]["userid"].tolist()
      
      #Find score find the common list of users and dived it by the total users
      commonusers= len(set(item1users).intersection(set(item2users)))
      score=commmonusers/usercount
      
      #add  a score for item1,item2
      itemaffinity.loc[rowCount]=[itemlist[ind1],itemlist[ind2],score]
      rowCount +=1
      
      #add  a score for item2,item1
      itemaffinity.loc[rowCount]=[itemlist[ind2],itemlist[ind1],score]
      rowCount +=1
      
 itemaffinity.head()
 
 #recommend
 
 searchitem=5001#id of item
 recolist=itemaffinity[itemaffinity.item1==searchitem]\[["item2","score"]]\.sort_values("score",ascending=[0])
 
 print("recommendations for item 5001\n",recolist)
 
 ```
# CLV (customer life value)
**Data: purchase record of each months**
```
from sklearn.linear_model import LinearRegression
import sklearn.metrics

#Do correlation analysis
cleaned_data.corr()["CLV"]#show the correlationship beatween months with the target variable(CLV)

#Build model
model=LinearRegression()
model.fit(pred_train,tar_train)
print("coefficients:\n",model.coef_)
print("Intercept:",model.intercept_)

predictions=model.predict(pred_test)
predictions

sklearn.metrics.r2_score(tar_test,predictions)

#predict a new customer
**if a new customer who in his first three months spend 100,0,50,let us use the model to predict the clv **
new_data=np.array([100,0,50,0,0,0]).reshape(1,-1)
new_pred=model.predict(new_data)
print("The CLV for the new customer is :&",new_pred[0])

```
# clustering
```
from sklearn.cluster import KMeans
import sklearn.metrics

**we will use K-means clustering group
1.use knee test to see the optimal number of groups**

# finding optimal no of clusters
from scipy.spatial.distance import cdist
clusters=range(1,10)
meanDistortions=[]

for k in clusters:
    model=KMeans(n_clusters=k)
    model.fit(clust_data)
    prediction=model.predict(clust_data)
    meanDistortions.append(sum(np.min(cdist(clust_data,model.cluster_centers_,"euclidean"),axis=1)))
    
plt.plot(clusters,meanDistortions,"bx-")
plt.xlabel("k")
plt.ylabel("Average distortion")
plt.title("Selecting k with the Elbow Method")

#optimal cluster is 3
final_model=KMeans(3)
final_model.fit(clust_data)
prediction=final_model.predict(clust_data)

raw_data["Group"]=prediction
raw_data[["Group","Problem_type"]]

#Analyze the groups
**do a set of boxplots to see how the groups differ for various feature attributes**

plt.cla()
plt.boxplot([[raw_data["count"][raw_data.Group==0]],
             [raw_data["count"][raw_data.Group==1]]
             [raw_data["count"][raw_data.Group==2]]],
             labels=("Group 1,Group 2,Group 3"))
             
             

```


