# like 

### 1.where CustomerName LIKE 'a%';
>a CustomerName starting with "a"

### 2.WHERE CustomerName LIKE '%a'
>a CustomerName ending with "a"

### 3.where CustomerName LIKE '%or%'
>CustomerName that have "or" in any position

### 4.WHERE CustomerName LIKE '_r%'
>a CustomerName that have "r" in the second position

### 5.WHERE CustomerName LIKE 'a__%'
>starts with "a" and are at least 3 characters in length:

### 6.WHERE ContactName LIKE 'a%o'
>starts with "a" and ends with "o"

### 7.WHERE CustomerName NOT LIKE 'a%'
>a CustomerName that does NOT start with "a"

### 8.WHERE City LIKE '[bsp]%'
>a City starting with "b", "s", or "p"

### 9.WHERE City LIKE '[a-c]%'
>a City starting with "a", "b", or "c"

### 10.WHERE City LIKE '[!bsp]%'
>a City NOT starting with "b", "s", or "p"

```
