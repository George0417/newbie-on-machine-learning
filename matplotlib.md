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

### show the figure with subplot

```
my_first_figure=plt.figure(`my first figure`)
subplot_1=my_first_figure.add_subplot(2,3,1)
subplot_6=my_first_figure.add_subplot(2,3,6)
plt.plot(np.random.rand(50).cumsum(),`K--`)#continue values
plt.show()

```

### show multiple lines
```
days=list(range(1,16))
low_mu,low_sigma=50,4.3
low_data_set=low_mu+low_sigma*np.random.randn(data_set_size)
high_mu,high_sigma=57,5.2
high_data_set=high_mu+high_sigma*np.random.randn(data_set_size)

plt.plot(days,low_data_set,
         days,low_data_set,"vm",#mark
         days,high_data_set,
         days,high_data_set,"^k")
       
plt.show()

```

### plot Annotations
```
subplot_1.text(1,0.5,r"an equation: $E=mc^2$",fontsize=18,color="red") # 1=x localation 1 ,0.5= y axis value

subplot_1.text(0.5,0.5,"we are centered,now",transform=subplot_1.transAxes)# in the middle of the scale

subplot_1.text.annotate("shoot arrow",xy=(2,1),xytext=(3,4),arrowprops=dict(facecolor="red",shrink=0.05))
# the arrow start from(3,4) to (2,1)

plt.show()

```

### plot label of  figure
```
fig = plt.figure()
for i, label in enumerate(("A","B","C","D")):
    ax=fig.add_subplot(2,2,i+1)
    ax.text(0.05,0.95,label,transform=ax.transAxes,
    fontsize=16,fontweight="bold",va="top")
    
plt.show()    
```

### pie charts
```
labels="Frogs","Hogs","Dogs","Logs"
sizes=[15,30,45,10]
colors=["yellowgreen","gold","lightskyblue","lightcoral"]
explode=(0,0.1,0,0)#only explode the 2nd slice (i.e Hogs)

plt.pie(x=sizes,explode=xeplode,labels=labels,colors=colors,autopct="%1.1f%%",shadow=True,startangle=90)
plt.axis("equal")

plt.show()

```

### Bar chart
```
N=5
menMean=(20,35,30,35,27)
menStd=(2,3,4,1,2)

ind=np.arrange(N) #the x locations for the groups
width=0.35 # the width of the bars

fig,ax=plt.subplots()
rects1=ax.bar(ind,menMeans,width,color="r",yerr=menStd)

#add some text fro labels , title and axes ticks
ax.set_ylabel("scores")
ax.set_title("scores bu group")

ax.set_xticks(ind+width)
ax.set_xticklabels(("G1","G2","G3","G4","G5"))
ax.legend((rects1[0],rects2[0]),("Men","Women"))

plt.show()


```
