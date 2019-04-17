# foundation
### enumerate
loop function

**ex**
```
python

list1 = ['a', 'b', 'c']
for (i, x) in enumerate(list1):
print i,x

0 a
1 b
2 c
```

### Zip function
loop function

**ex**
```
python

list1 = [1, 2, 3]
list2 = [4, 5, 6]
for (a, b) in zip(list1, list2):   
#loop list1,list2
print a,b
... 
1 4
2 5
3 6

*****************************
list3 = [7, 8]
for (a, b) in zip(list1, list3):   
#Matched  with fewer elements list3
print a,b
... 
1 7
2 8

******************************
#Column conversion
 list4 = [
...   [1, 2, 3],
...   [4, 5, 6],
...   [7, 8, 9]
... ]
 for (a, b, c) in zip(*list4):
print a,b,c
... 
1 4 7
2 5 8
3 6 9
```

### copy
```
#a shallow copy
-a=b
-a=b.view()

#a deep copy
a=np.copy(b)

```
