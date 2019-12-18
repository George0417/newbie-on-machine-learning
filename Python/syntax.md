>> https://www.w3schools.com/python/python_lists.asp

# String Format
### 1. we cannot combine strings and numbers,but we can combine strings and numbers by using the format() method! 
```
age = 36
txt = "My name is John, and I am {}"
print(txt.format(age))
```

### 2. format {0}

```
quantity = 3
itemno = 567
price = 49.95
myorder = "I want to pay {2} dollars for {0} pieces of item {1}."
print(myorder.format(quantity, itemno, price))

```

# Escape Character

### 1.To insert characters that are illegal in a string, use an escape character

>>illegal character is a double quote inside a string that is surrounded by double quotes
```
"We are the so-called "Vikings" from the north."
```

### Right
```
"We are the so-called \"Vikings\" from the north."
```

### Example
```
\'	Single Quote
\\	Backslash
\n	New Line
\r	Carriage Return
```

### insert
```
thislist = ["apple", "banana", "cherry"]
thislist.insert(1, "orange")
print(thislist)
```

### PoP
**The pop() method removes the specified index, (or the last item if index is not specified)**
```
thislist = ["apple", "banana", "cherry"]
thislist.pop()
print(thislist)
```

### del
**The del keyword removes the specified index:**
```
thislist = ["apple", "banana", "cherry"]
del thislist[0]
print(thislist)
```

### extend
```
list1 = ["a", "b" , "c"]
list2 = [1, 2, 3]

list1.extend(list2)
print(list1)
```

### list
**Using the list() constructor to make a List:**
>>tuple,set would also need to use the double brackets
```
thislist = list(("apple", "banana", "cherry")) # note the double round-brackets
print(thislist)

['apple', 'banana', 'cherry']
```

### tuple
**Once a tuple is created, you cannot change its values. Tuples are unchangeable, or immutable as it also is called.
But there is a workaround. You can convert the tuple into a list, change the list, and convert the list back into a tuple.**

```
x = ("apple", "banana", "cherry")
y = list(x)
y[1] = "kiwi"
x = tuple(y)

print(x)
("apple", "kiwi", "cherry")
```

### Create Tuple With One Item
```
thistuple = ("apple",)
print(type(thistuple))

<class 'tuple'>

#NOT a tuple
thistuple = ("apple")
print(type(thistuple))

<class 'str'>
```

### SET
**You cannot access items in a set by referring to an index, since sets are unordered the items has no index.**
```
thisset = {"apple", "banana", "cherry"}

for x in thisset:
  print(x)
  
banana
apple
cherry
```

### update
**Add multiple items to a set, using the update() method:**
```
thisset = {"apple", "banana", "cherry"}
thisset.update(["orange", "mango", "grapes"])
print(thisset)

{'mango', 'orange', 'banana', 'cherry', 'grapes', 'apple'}
```

### remove,discard
**If the item to remove does not exist, remove() will raise an error.**
**If the item to remove does not exist, discard() will NOT raise an error.**

### union
```
set1 = {"a", "b" , "c"}
set2 = {1, 2, 3}
set3 = set1.union(set2)
print(set3)

{1, 'c', 3, 'b', 2, 'a'}
```

### items
**Loop through both keys and values, by using the items() function**
```
for x, y in thisdict.items():
  print(x, y)
```

### copy
**Make a copy of a dictionary with the dict() method**
```
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
mydict = dict(thisdict)
print(mydict)

{'brand': 'Ford', 'model': 'Mustang', 'year': 1964}
```

### Nested Dictionaries
```
child1 = {
  "name" : "Emil",
  "year" : 2004
}
child2 = {
  "name" : "Tobias",
  "year" : 2007
}
child3 = {
  "name" : "Linus",
  "year" : 2011
}

myfamily = {
  "child1" : child1,
  "child2" : child2,
  "child3" : child3
}

{'child1': {'name': 'Emil', 'year': 2004}, 'child2': {'name': 'Tobias', 'year': 2007}, 'child3': {'name': 'Linus', 'year': 2011}}
```
>> Note that range(6) is not the values of 0 to 6, but the values 0 to 5


