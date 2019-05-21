# Feature Engineering
### Creat new features of transforming existing features to get the  most out of  data

**EX**
### Create new Feature(spam detection problem)
1. length of text field
2.percentage of characters that are punctuation in the text
3.percentage of characters that are capitalized

### create feature for text message length
'''
data["body_len"]=data["body_text"].apply(lambda x: len(x)-x.count(" "))
data.head()
'''

### create feature for % of text that is punctuation
'''
import string
def count_punct(text):
    count=sum([1 for char in text if char in string.punctuation])
    return round(count/(len(text)-text.count(" ")),3)*100

data["punct%"]=data["body_text"].apply(lambda x: count_punct(x))

data.head()
'''

# 2. Feature evaluation
### used histogram to compare
```
from matplotlib import pyplot
import numpy as np
%matplotlib inline

bins=np.linspace(0,200,40) # (start point, maximun length,cut point )
1.the distrubution of body length for spam
pyplot.hist(data[data["label"]=="spam"]["body_len"],bins,alpha=0.5,normed=True,Label="spam")

2.the distrubution of body length for nonspam
pyplot.hist(data[data["label"]=="spam"]["body_len"],bins,alpha=0.5,normed=True,Label="ham")

pyplot.legend(loc="upper left")
pyplot.show()
```

# 3.Box-Cox power transformation
#process
#determin what range of exponents to test
#apply each transformation to each value of your chosen feature
#use some criteria to determine which of the transformations yield the best distribution
```
for i in [1,2,3,4,5]:
    pyplot.hist((data["punct%"])**(1/i),bins=40) # bins = cut point,depending on what exponent we apply to it. 
    pyplot.show()
```


