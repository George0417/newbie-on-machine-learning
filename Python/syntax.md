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

Right
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
