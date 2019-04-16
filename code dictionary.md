# numpy

**np.c_ np.r_**
  
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

**np.linspace**
numpy.linspace(start, stop, num = 50, endpoint = True, retstep = False, dtype = None)

Generation of Equivariance Sequence

### ex:
```
python

np.linspace(0, 2, num = 3) # if you don't set the dtype、it would be float
array([ 0.,  1.,  2.])

 ----------------------------------------------
 
np.linspace(0, 1, num = 4, dtype = 'float32')  # if you set the dtype、it would be float32 or int or float64
array([ 0.        ,  0.33333334,  0.66666669,  1.        ]
```
