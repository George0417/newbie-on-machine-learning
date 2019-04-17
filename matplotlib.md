# matplotlib
>is a python 2D plotting library that produces plublication quality figures in hard copy formats

-Before import matplotlib you must input %matplotlib inline 
### the histogram of the data
```

mu,sigma=100,15
data_set=mu+sigma+np.random.randon(10000)

n,bins,patches=plt.his(data_set,50,normed=1,facecolor=`g`,alpha=0.75)
plt.axis（[40，160，0，0.03]）
plt.show()
```

