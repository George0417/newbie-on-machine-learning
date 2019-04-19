# numpy

### np.c_ np.r_
  
 >np.c_is to connect two matrices by column like concat() in pandas  #c---cloumn
 
 >np.r_is to connect two matrices by row like merge() in pandas   #r----row
  
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
>Generation of Equivariance Sequence

**ex:**
```
python

np.linspace(0, 2, num = 3) # if you don't set the dtype、it would be float
array([ 0.,  1.,  2.])

 ----------------------------------------------
 
h=np.linspace(0, 1, num = 4, retstep_True,dtype = 'float32')  # if you set the dtype、it would be float32 or int or float64
(array([ 0.        ,  0.33333334,  0.66666669,  1.        ]),0.3333)
h[1]=0.3333
```


### np.meshgrid
>Return coordinate matrices from coordinate vectors

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
>convert the matrix to (1,X),but the return of flatten()is the copy of array

![](https://upload-images.jianshu.io/upload_images/6445182-684d925e66cdfffe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/331/format/webp)


### np.ravel()
>convert the matrix to (1,X),but the return of flatten()is the inital of array

![](https://upload-images.jianshu.io/upload_images/6445182-cae7edd6227f9751.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/323/format/webp)

a.shape
(4,0)

### np.random.randn()
>Generate the random data with normal distribution 
>which in ()should be int

**ex**
```
np.random.randn(3,2)
array([[1.25,2.55],
      [[1.25,2.55],
      [[1.25,2.55]])
```



### np.random.rand()
>Generate the random data with normal distribution  [0,1)

**ex**
```
np.random.rand(3,2)
array([[0.25,0.55],
      [[0.25,0.55],
      [[0.25,0.55]])
```      

### numpy.random.randint(low, high=None, size=None, dtype=’l’)  
low—–min 
high—-max
size—–(2,2)matrix 
dtype— format np.int

**ex**
```
numpy.random.randint(1, 20, size=(3,3), dtype=’unit8’) 
array([[19,2,5],
      [[1,2,8],
      [[10,2,4]], dtype=’unit8’)

```

###np.arange(start,stop,step,dtype)
>Values are generated within the half-open interval[start,stop)
   
**ex**
```
np.arange(7)

array([1,2,3,4,5,6])

np.arange(10，23，5)

array([0，15，20])

np.arange(26，step=5)

array([0，5,10,15,20,15])

```   

### np.zeros(),np.ones()

**ex**
```
np.zero(3,2)
array([[0.,0.],
       [0.,0.],
       [0.,0.]])

```
```
np.zero(2,3,2) 2 means two group,3 means three rows,2 means two columns 
array([[0.,0.],
       [0.,0.],
       [0.,0.]]
       
       [[0.,0.],
       [0.,0.],
       [0.,0.]])

```

### Two dimensional arrays

**ex**
```
my_array=np.arange(10)
my_array.shape=(2,5)
my_array

array([[0,1,2,3,4],
       [5,6,7,8,9]])

""""""""""""""""""""""""""""
my_array[1]
array([5,6,7,8,9])

my_array[row,column]
       
```       
### Three dimensional arrays

```
c=np.array(np.arange(24)).reshape(2,3,4)*10+3

array([[[3,13,23,33],
        [43,53,63,73],
        [83,93,103,113]],
        
       [[123,133,143,153],
        [163,173,183,193],
        [203,213,223,233]]])

a=c

np.append(a,c,axis=0).shape
(4,3,4)

np.append(a,c,axis=1).shape
(2,6,4)

np.append(a,c,axis=2).shape
(2,3,8)
```

### np.hstack((a,c))
>eaqul to np.append(a,c,axis=1).shape

### np.insert()
>np.insert(c,1,444,axis=0)
```
array([[[3,13,23,33],
        [43,53,63,73],
        [83,93,103,113]],
        
        [[444,444,444,444],
        [444,444,444,444],
        [444,444,444,444]]
        
       [[123,133,143,153],
        [163,173,183,193],
        [203,213,223,233]]])
        
```
>np.insert(c,1,444,axis=1)
```
array([[[3,13,23,33],
        [444,444,444,444],
        [43,53,63,73],
        [83,93,103,113]],
        
       [[123,133,143,153],
        [163,173,183,193],
        [203,213,223,233]]])
        
```


### Boolean Mask Arrays

**ex**
```
my_vector=np.array([-17,-4,0,2,21,37,105])
zero_mod_7_mask=0==(my_vector % 7)
zero_mod_7_mask

array([False,False,True,False,True,False,true]，dytype=bool)

sub_array=my_vector[zero_mod_7_mask]
arrray([0,21,105])

```

### np.logical_and()
**ex**
```
positive_test=my_vector > 0
combined_mask=np.logical_and(zero_mod_7_mask,positive_test)
array([False,False,False,False,True,False,True],dytype=bool)

```

### np.rec.array()

**ex**
```
person_record_array=np.rec.array([(`Delat`,73,205,34),(`Alpha`,65,112,23)],dtype=person_data_def)

rec.array([(b`Delta`,73,205,34),(b`alpha`,65,112,23)],
dtype=[(`name`,`s6`),（`height`,`f8`）,(`weight`,``f8),(`age`,`i8`)])

person_record_array[0].age
34

```

### np.concatenate()
**ex**
```
a=array([[1,2],[3,4]])
b=array([[5,6]])
c=np.concatenate((a,b),axis=0)

c=array([[1,2],[3,4],[5,6]])

```

### np.fliplr()& np.flipud() & np.roll() &np.rot90()
**ex**
```
a=array([[1,2,3,4],
         [5,6,7,8]],
         
         [[9,10,11,12],
         [13,14,15,16]])
         
        
np.fliplr(a)

array([[8,7,6,5],
       [4,3,2,1]]
       
       [[16,15,14,13],
        [12,11,10,9]])

np.flipud(a)

array([[16,15,14,13],
       [12,11,10,9]]
       
       [[8,7,6,5],
       [4,3,2,1]])
       
np.roll(a,2)  #n means put the n number of value infront,-n means put the fornt number to the end
a=array([[15,16,1,2],
         [3,4,5,6]],
         
         [[7,8,9,10],
         [11,12,13,14]])
         
 np.rot90(a)    
 a=array([[4,8,12,16],
         [3,7,11,15]],
         
         [[2,6,10,14],
         [1,5,9,13]])
         
 

```

### np.transpose()
**ex**
```
a=array([[1,2,3,4],
         [5,6,7,8]])
         
np.transpose(a)

array([[1,5],
       [2,6]
       [3,7]
       [4,8]])
       
```
> use np.transpose to permute all the axes at once
> use np.swapaxes to swap any two axes
> use np. rollaxis to rotate  the axes


### np.tile() #repeat n times of the matrix
**ex**
```
a=array([1,2,3,4])
np.tile(a,3).reshape(3,4)

array([1,2,3,4]
      [1,2,3,4]
      [1,2,3,4])

```

### np.diff()
**ex**
```
a=array([1,7,19,37])

np.diff(a)
array([6,12,18])

np.diff(a,n=2)
array([6,6])

np.diff(a,n=3)
array([0])
```


### np.__version__
>test the version of np

