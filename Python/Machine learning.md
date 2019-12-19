# Mean, Median, and Mode
>> speed = [99,86,87,88,111,86,103,87,94,78,77,85,86]

### Mean - The average value
```
import numpy

speed = [99,86,87,88,111,86,103,87,94,78,77,85,86]
x = numpy.mean(speed)
print(x)

89.77
```
### Median - The mid point value
```
import numpy

speed = [99,86,87,88,111,86,103,87,94,78,77,85,86]
x = numpy.median(speed)
print(x)

87.0
```
### Mode - The the most common value
```
from scipy import stats

speed = [99,86,87,88,111,86,103,87,94,78,77,85,86]
x = stats.mode(speed)
print(x)

ModeResult(mode=array([86]), count=array([3]))
```
### standard deviation
```
import numpy

speed = [86,87,88,86,87,85,86]
x = numpy.std(speed)
print(x)

0.90
```
### Variance
**the square root of the variance, you get the standard variation!**
```
import numpy

speed = [32,111,138,28,59,77,97]
x = numpy.var(speed)
print(x)

1432.2
```

### Percentiles
**describes the value that a given percent of the values**
```
import numpy

ages = [5,31,43,48,50,41,7,11,15,39,80,82,32,2,8,6,25,36,27,61,31]
x = numpy.percentile(ages, 90)
print(x)

61
```

### Linear Regression
```
import matplotlib.pyplot as plt
from scipy import stats

x = [5,7,8,7,2,17,2,9,4,11,12,9,6]
y = [99,86,87,88,111,86,103,87,94,78,77,85,86]

slope, intercept, r, p, std_err = stats.linregress(x, y)
#Create a function that uses the slope and intercept values to return a new value. 
#This new value represents where on the y-axis the corresponding x value will be placed:

#print(r)
#The r-squared value ranges from 0 to 1, where 0 means no relationship, and 1 means 100% related

def myfunc(x):
  return slope * x + intercept

mymodel = list(map(myfunc, x))

plt.scatter(x, y)
plt.plot(x, mymodel)
plt.show()
```

### Polynomial Regression
```
import numpy
import matplotlib.pyplot as plt

x = [1,2,3,5,6,7,8,9,10,12,13,14,15,16,18,19,21,22]
y = [100,90,80,60,60,55,60,65,70,70,75,76,78,79,90,99,99,100]

mymodel = numpy.poly1d(numpy.polyfit(x, y, 3))
#print(r2_score(y, mymodel(x)))---show R-Squared

#speed = mymodel(17)
#Predict the speed of a car passing at 17 P.M

myline = numpy.linspace(1, 22, 100)
#Then specify how the line will display, we start at position 2, and end at position 22

plt.scatter(x, y)
plt.plot(myline, mymodel(myline))
plt.show()
```
