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
