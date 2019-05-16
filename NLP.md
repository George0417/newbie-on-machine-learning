# Process of NLP
### download NLTK
### manipulate

"""

parseData = rawData.replace("\t","\n").split("\n")### you can replace "\t" to "\n",and devide the sentance by "\n"
parseData[0:5]#the former 5 line of the phrass

"""
### devide the different types of phrase into different data
"""
labellist = parseData [0::2]# from the beginning to the end every other two words will be devided into labellist

testlist = parseData [1::2]
"""

### compose
"""

*the length of labellist and testlist should be same

fullcorpus = pd.DataFrame({
"label":labellist,
"body":testlist
})

"""
>dataset=pd.read_csv("XXXX.csv",sep="\t",header=None)  #read csv file and divide it by"\t",without column 

### Expore the dataset
> how many words "spam"  in the text 

"""

print("out of {} rows,{} are spam".format(len(fullcorpus),len(fullcorpus[fullcorpus["label"]=="spam"])))

"""

> how many missing data is in the column "label"

"""

print("Number of null in label: {} ".format(fullcorpus["label"].isnull().sum()))
# first calculcate the number of true if null is in label, then sum the number of True

"""
