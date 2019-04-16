# numpy
```
diff
+・np.c_ np.r_
  
 np.c_is to connect two matrices by column like concat() in pandas
 np.r_is to connect two matrices by row like merge() in pandas
  
### ex:
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
c = np.c_[a,b]

```
python
print(np.r_[a,b])
[1 2 3 4 5 6]
----------------------------------------------
print(c)
[[1 4]
 [2 5]
 [3 6]]
 ----------------------------------------------
print(np.c_[c,a])
[[1 4 1]
 [2 5 2]
 [3 6 3]]
```  
```
