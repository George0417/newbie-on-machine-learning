# 1. Removing punction

### punctuation---example of punctuation
```
import string
string.punctuation
'!"#$%&()'+-/.;:'
```

```
def remove_punct(text):
   text_nopunct="".join([char for char in text if char not in string.punctuation])
   return text_nopunct

data["body_text_clean"]=data["body_text"].apply(lambda x: remove_punct(x))

data.head()

```
Result
```
label              body_text                            body_text_clean
 ham      I've been searching for % the right words     Ive beensearching for the right words
 
```
 
 # 2.Tokenization
 ### Symbolization ---splitted by symbol
 

```
 import re
 
 def tokenize(text):
     tokens =re.split("\W+",text)
     return tokens
 
 data["body_text_tokenized"]=data["body_text_clean"].apply(lambda x:tokenize(x.lower()))
 
 data.head()
```   
result
```
 label              body_text                            body_text_clean                                   body_text_tokenized
 ham      I've been searching for % the right words     Ive been searching for the right words  [Ive,been,searching,for,the,right,words]
 
```
 # 3.Remove stopwords
 
 
 ### example of stopwords
 import nltk
 stopword=nltk.corpus.stopwords.words("english") #like words "I" "the" "a"
 
```
 def remove_stopwords(tokenized_list):
   text=[word for word in tokenized_list if word not in stopword])
   return text

data["body_text_nostop"]=data["body_text_tokenized"].apply(lambda x: remove_stopwords(x))

data.head()
```
result
```
label              body_text                                         body_text_clean                                                     
 ham      I've been searching for % the right words               Ive been searching for the right words  
               body_text_tokenized                                   body_text_nostop
           [Ive,been,searching,for,the,right,words]               [Ive,searching,right,words]
 
```
# 4.Stem (faster as it chops off the end of word using heuristics)
### crudely choppingoff the end of the word to leave only the  base

```
import nltk
ps=nltk.PorterStemmer()
**EX**

PS.stem("grows")
PS.stem("growing")
PS.stem("grow")

result
grow
```
```
def stemming(tokenized_text):
   text=[ps.stem(word) for word in tokenized_text)
   return text

data["body_text_stemmed"]=data["body_text_nostop"].apply(lambda x: stemming(x))

data.head()
```
result
```
           body_text_nostop                              body_text_stemmed
    [Ive,searching,right,words]                       [Ive,searching,right,words] 
```

# 5.Lemmatizing (more accurate than stem)

```
**Ex1**
import nltk
ps=nltk.PorterStemmer()
wn=nltk.WordNetLemmatizer()

print(ps.stem("goose"))
print(ps.stem("geese"))
```

result
```
gose
gese
```


```
**Ex2**
print(wn.lemmatize("goose"))
print(wn.lemmatize("geese"))
```

result
```
goose
goose
```

```
def lemmatizing (tokenized_text):
    text=[wn.lemmatize(word)for word in  tokenized_text]
    return text
data["body_text_lemmatized"]=data["body_text_nostop"].apply(lambda x: lemmatizing(x))

data.head()
```
