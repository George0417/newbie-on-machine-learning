# Pipeline of NLP
### download NLTK
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

2.remove stop words# stop words mean "you" ,"the","and" frequency and not important words
  
[clean the text](/NLP/clean the text.md)
### 6. Vectorize--convert to numeric form
[Vectorize](/NLP/Vectorize.md)


### 7. Machine learning algorithm--fit/train model



### 8. implement it within whatever framework
