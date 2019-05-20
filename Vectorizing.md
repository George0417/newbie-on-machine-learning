# Vectorize

# Count vectorization
Creates a document-term matrix where the entry of each cell will be a count of the number of times that word occurred in that document.


### read in text
```
import pandas as pd
import re
import string
import nltk
pd.set_option("display.max_colwidth",100)

stopwords=nltk.corpus.stopwords.word("english")
ps=nltk.PorterStemmer()

data=pd.read_csv("XXX.csv",sep="\t")
data.columns=["label","body_text"]
```

###Create function to remove punctuation,tokenize,remove stopwords, and stem
def clean_text(text):
    text="".join([word.lower()for word in text if  word not in  string.punctuation])
    tokens = re.split("\W+",text)
    text =[ps.stem(word)for word  in tokens if word not in  stopwords]
    return text
    
```
### Apply CountVectorizer
```
from sklearn.feature_extraction.text import CountVectorizer
count_vect=CountVectorizer(analyzer=clean_text)
X_counts=count_vect.fit_transform(data["body_text"])
print(X_counts.shape)
print(count_vect.get_feature_names())

```
result
```
(20,192)#20 rows,192 columns
["","008704","06"]
```

```
X_counts_df=pd.DataFrame(X_counts.toarray())
X_counts_df.columns=count_vect.get_feature_names()
X_counts_df
```
result
```
100 wet win winner word
0   1   0   0       1
```



# N-grams
>create a document-term matrix where represent all combinations of adjacent words of length n in your text.
```
"NLP is an interesting topic"
result
four-gram  ["NLP is an interesting","is an interesting topic"]
```

###Create function to remove punctuation,tokenize,remove stopwords, and stem
```
def clean_text(text):
    text="".join([word.lower()for word in text if  word not in  string.punctuation])
    tokens = re.split("\W+",text)
    text =" ".join([ps.stem(word)for word  in tokens if word not in  stopwords])
    return text

data["cleaned_text"]=data["body_text"].apply(lambda x:clean_text(x))
data.head()
```
### Apply CountVectorizer
```
from sklearn.feature_extraction.text import CountVectorizer
ngram_vect=CountVectorizer(ngram_range=(2,2))#(1,3) means unigrams,bigrams and trigrams
X_counts=ngram_vect.fit_transform(data["cleaned_text"])
print(X_counts.shape)
print(ngram_vect.get_feature_names())

---(20,220)#20 rows,220 columns ==220 unique two words combination words
```


# Term frequency-inverse document frequency(TF-IDF)
```
text"I like NLP"
tf(NLP)= #of occurance of NLP/ number of words in text message =1/3

N=20 #(number of texts is 20)
df(NLP)=1 #(frequency of NLP is one)

Wi,j=tf(NLP)*log(N/df(NLP))
     =1/3*log(20/1)
     =0.43
```

>how ever when the N get larger, df(NLP) doesn't change ,the Wi,j will get larger
 so the rarer the word is , the higher the value is going to be

###Create function to remove punctuation,tokenize,remove stopwords, and stem
the same with Count vectorization

### Apply CountVectorizer
```
from sklearn.feature_extraction.text import TfidfVectorizer
tfidf_vect=TfidfVectorizer(analyzer=clean_text)
X_tfidf=tfidf_vect.fit_transform(data["body_text"])

print("X_tfidf.shape")
```


