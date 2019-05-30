# Pipeline of NLP
### download NLTK("natural language toolkit")
```
import nltk
from nltk.stem import PorterStemmer
from nltk.tokenize import WordPunctTokenizer

# Download stopwords
nltk.download("stopwords")
from nltk.corpus import stopwords


```
### 1. manipulate

```
parseData = rawData.replace("\t","\n").split("\n") # you can replace "\t" to "\n",and devide the sentance by "\n"
parseData[0:5] #the former 5 line of the phrass
```

### 2. devide the different types of phrase into different data
```
labellist = parseData [0::2] # from the beginning to the end every other two words will be devided into labellist

testlist = parseData [1::2]
```

### 3. compose
```
**the length of labellist and testlist should be same**

fullcorpus = pd.DataFrame({
"label":labellist,
"body":testlist
})
```
>dataset=pd.read_csv("XXXX.csv",sep="\t",header=None)  #read csv file and divide it by"\t",without column 

### 4. Expore the dataset
> how many words "spam"  in the text 
```
print("out of {} rows,{} are spam".format(len(fullcorpus),len(fullcorpus[fullcorpus["label"]=="spam"])))
```

> how many missing data is in the column "label"
```
print("Number of null in label: {} ".format(fullcorpus["label"].isnull().sum()))
# first calculcate the number of true if null is in label, then sum the number of True
```
### 5. clean text
1.regular expression (punctuation)  
 or
 ```
 word_pattern = re.compile("^\w+S")
 ```

2.remove stop words# stop words mean "you" ,"the","and" frequency and not important words
```
esw =stopwords.words("english")
esw.append("would")

```
  
[clean the text](/NLP/clean the text.md)

### 6. Vectorize--convert to numeric form
[Vectorize](/NLP/Vectorize.md)

```
1.create a token counter function
def get_text_counter(text)
    tokens = WordPunctTokenizer().tokenize(PorterStemmer().stem(text))
    tokens = list(map(lambda x:x.lower(),tokens))
    tokens = [token for token in tokens if re.match(word_pattern,token) and token not in esw]
    return collections.Counter(tokens),len(tokens)
    
2.Create a function to calculate the absolute frequency and relative 
def make_df(counter,size)
    abs_freq = np.array([el[1] for el in counter])
    rel_freq = abs_freq / size
    index = [el[0] for el in counter]
    df =pd.DataFrame(data=np.array([abs_freq,rel_freq]).T,index=index,columns=["Absolute frequceny","Relative frequecy"])
    df.index.name ="Most common words"
    return df
``` 

**Analysis**
  calculate the most commonwords of XXX
``` 
je_counter,je_size = get_text_counter(XXX)
je_df = make_df(je_counter.most_common(100),je_size) #save the 100 most common words of xxx to csv
je_df.to_csv("JE_100.csv")    
   
#you can do it the same way to the other file    
``` 
**Compare**
  find the most common words across the two documents
``` 
all_counter =Je_counter+wh_counter
all_df=make_df(wh_counter.most_common(1000),1)
most_common_words=all_df.index.values

#create a data frame with the word frequency differences

df_data=[]
for word  in most common_words:
    je_c = je_counter.get(word,0)/je_size
    wh_c = je_counter.get(word,0)/wh_size
    d=abs(je_c-wh_c)
    df_data.append([je_c,wh_c,d])
dist_df=pd.DataFrame(data=df_data,index=most_common_words,columns=["JE relative frequency","Wu relative frequency","Relative frequency difference"])
dist_df.index.name = "Most common words"
dist_df.sort_values("Relative frequency difference",ascending=False,inplace=True)
dist_df.head(10)
dist_df.to_csv("difference.csv")
```

### 7. Machine learning algorithm--fit/train model
[model of machine learning](/NLP/model of machine learning.md)


### 8. implement it within whatever framework
