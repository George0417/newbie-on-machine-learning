# Removing punction
**Ex1**
'''
import string
string.punctuation
'!"#$%&()'+-/.;:'
'''

**Ex2** 
'''
def remove_punct(text):
   text_nopunct="".join([char for char in text if char not in string.punctuation])
   return text_nopunct

data["body_text_clean"]=data["body_text"].apply(lambda x: remove_punct(x))

data.head()

'''
'''
label              body_text                            body_text_clean
 ham      I've been searching for % the right words     Ive beensearching for the right words
 
'''
 
 # Tokenization
 > Symbolization ---splitted by symbol
 
 **Ex3**
 '''
 import re
 
 def tokenize(text):
     tokens =re.split("\W+",text)
     return tokens
 
 data["body_text_tokenized"]=data["body_text_clean"].apply(lambda x:tokenize(x.lower()))
 
 data.head()
'''     
'''
 label              body_text                            body_text_clean                                   body_text_tokenized
 ham      I've been searching for % the right words     Ive been searching for the right words  [Ive,been,searching,for,the,right,words]
 
 '''
 # Remove stopwords
 
 **Ex4**
 
 import nltk
 stopword=nltk.corpus.stopwords.words("english") #like words "I" "the" "a"
 
 '''
 def remove_stopwords(tokenized_list):
   text=[word for word in tokenized_list if word not in stopword])
   return text

data["body_text_nostop"]=data["body_text_tokenized"].apply(lambda x: remove_stopwords(x))

data.head()
 '''
''' 
label              body_text                            body_text_clean                                                     
 ham      I've been searching for % the right words     Ive been searching for the right words  
 
               body_text_tokenized                       body_text_nostop
 [Ive,been,searching,for,the,right,words]        [Ive,searching,right,words]
 
 '''
 
