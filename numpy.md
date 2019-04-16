# numpy

### np.c_ np.r_
  
 np.c_is to connect two matrices by column like concat() in pandas
 np.r_is to connect two matrices by row like merge() in pandas
  
**ex:**
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

### np.linspace
numpy.linspace(start, stop, num = 50, endpoint = True, retstep = False, dtype = None)

Generation of Equivariance Sequence

**ex:**
```
python

np.linspace(0, 2, num = 3) # if you don't set the dtype、it would be float
array([ 0.,  1.,  2.])

 ----------------------------------------------
 
np.linspace(0, 1, num = 4, dtype = 'float32')  # if you set the dtype、it would be float32 or int or float64
array([ 0.        ,  0.33333334,  0.66666669,  1.        ]
```


### np.meshgrid
Return coordinate matrices from coordinate vectors

![](https://chaopei.github.io/images/posts/python/meshgrid.png)

```
 x = np.linspace(0, 1, 3)
 # x = array([0, 0.5, 1])
 
 y = np.linspace(0, 1, 2) 
 # y = array([0, 1])
 
>>> xv, yv = np.meshgrid(x, y)
>>> xv
array([[ 0. ,  0.5,  1. ],
       [ 0. ,  0.5,  1. ]])
>>> yv
array([[ 0.,  0.,  0.],
       [ 1.,  1.,  1.]])
```


### np.flatten() 
convert the matrix to (1,X),but the return of flatten()is the copy of array

![](https://upload-images.jianshu.io/upload_images/6445182-684d925e66cdfffe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/331/format/webp)


### np.ravel()
convert the matrix to (1,X),but the return of flatten()is the inital of array

![](https://upload-images.jianshu.io/upload_images/6445182-cae7edd6227f9751.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/323/format/webp)


### np.random.randn()
Generate the random data with normal distribution 
which in ()should be int

**ex**
np.random.randn(3,2)
array([[1.25,2.55],
      [[1.25,2.55],
      [[1.25,2.55]])

### np.random.rand()
Generate the random data with normal distribution  [0,1)

**ex**
np.random.rand(3,2)
array([[0.25,0.55],
      [[0.25,0.55],
      [[0.25,0.55]])
      

### numpy.random.randint(low, high=None, size=None, dtype=’l’)  
low—–min 
high—-max
size—–(2,2)matrix 
dtype— format np.int

**ex**
numpy.random.randint(1, 20, size=(3,3), dtype=’unit8’) 
array([[19,2,5],
      [[1,2,8],
      [[10,2,4]], dtype=’unit8’)


