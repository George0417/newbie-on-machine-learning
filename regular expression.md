###Takeaways  methods
---findall()
---split()

###Takeaways  regexes
---"\W"&"\w"--words
---"\S"&"\s"--whitespaces
---

**Ex**
re_test="this-is-a-made/up.string*to>>>>test-----2'''''different"

resolution1
'''
re.split("\W+",re_test)  #"\W=every element including space,*,.,-","\s only indicated white space","+means one or more white space here"
["this","is","a",",made",-------]
'''

resolution2
'''
re.findall("\S+",re_test) #"\S+ means one or more non white space here",#"\w+ means one or more non special characters==find string only,*
'''

###replace a specific string

**EX**
example="I want to follow PEP8"

'''
re.findall("[a-z]+",exapmle) # to find the lower alphabert from a to z in the example

["want","to","follow"] 

'''

'''
re.findall("[A-Z]+[0-9]+",exapmle) # to find the capital alphabert contains number from a to z in the example

["PEP8"]
'''

'''
re.sub("[A-Z]+[0-9]+","python",exapmle) # to find the capital alphabert contains number from a to z in the example and replace it into "python"

"I want to follow python"
'''
