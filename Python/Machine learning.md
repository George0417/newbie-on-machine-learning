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


