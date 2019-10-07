# LEFT

**LEFT(s,n) allows you to extract n characters from the start of the string s.**
1
```
LEFT('Hello world', 4) -> 'Hell'   
```
2
```
SELECT name,
       LEFT(name, 3)
  FROM bbc
```

Result:
```
name	  LEFT(name, 3)
Angola	 Ang
Benin	  Ben
```
