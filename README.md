<div align="center">
  <img src="https://github.com/ksalokya/devicon/blob/master/icons/numpy/numpy-original-wordmark.svg" width="300px"/>
</div>
<h1 align="center">NumPy Cheatsheet</h1>

## What is NumPy?
#### A library consisting of multidimensional array objects and a collection of routines for processing those arrays.

## Installing NumPy
```
  pip install numpy 
```

# Basics


```python
# import numpy
import numpy as np
```


```python
# returns list of the attributes and methods
# dir(np)
```


```python
len(dir(np))
```




    608




```python
np_arr = np.arange(1000000)
py_list = list(range(1000000))
```


```python
# time take by python list
%time for _ in range(10): [item*3 for item in py_list]
```

    Wall time: 817 ms
    


```python
# time take by numpy array
%time for _ in range(10): np_arr = np_arr*3
```

    Wall time: 17.9 ms
    

# Operations


```python
# len coloumns of cols must be same for all rows
arr1 = np.array([[1,2,3,4,5],[6,7,8,9,10]])
```


```python
print(arr1)
```

    [[ 1  2  3  4  5]
     [ 6  7  8  9 10]]
    


```python
print(type(arr1))
```

    <class 'numpy.ndarray'>
    


```python
arr1.shape
```




    (2, 5)




```python
arr1.dtype
```




    dtype('int32')




```python
# create 4x6 matrix filled with zeroes
np.zeros((4,6))
```




    array([[0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0.]])




```python
# create 4x6 matrix filled with ones
np.ones((4,6))
```




    array([[1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1.]])




```python
# create 4x6 empty matrix - may be garbage value
np.empty((4,6))
```




    array([[1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1.]])




```python
# m x n matrix
i = 3
j = 2
arr2 = np.zeros(shape=(i,j))

arr2
```




    array([[0., 0.],
           [0., 0.],
           [0., 0.]])




```python
arr1
```




    array([[ 1,  2,  3,  4,  5],
           [ 6,  7,  8,  9, 10]])




```python
# multiplication
arr1*arr1
```




    array([[  1,   4,   9,  16,  25],
           [ 36,  49,  64,  81, 100]])




```python
# division
arr1/2
```




    array([[0.5, 1. , 1.5, 2. , 2.5],
           [3. , 3.5, 4. , 4.5, 5. ]])




```python
1/arr1
```




    array([[1.        , 0.5       , 0.33333333, 0.25      , 0.2       ],
           [0.16666667, 0.14285714, 0.125     , 0.11111111, 0.1       ]])




```python
# power
arr1**arr1
```




    array([[         1,          4,         27,        256,       3125],
           [     46656,     823543,   16777216,  387420489, 1410065408]],
          dtype=int32)



# Slicing


```python
arr2 = np.array([1,2,3,4])
arr2
```




    array([1, 2, 3, 4])




```python
arr2[:]
```




    array([1, 2, 3, 4])




```python
arr2[0:]
```




    array([1, 2, 3, 4])




```python
arr2[:0]
```




    array([], dtype=int32)




```python
arr2[0:999]
```




    array([1, 2, 3, 4])




```python
arr2[999:0]
```




    array([], dtype=int32)




```python
arr2[-1:]
```




    array([4])




```python
arr2[-2:]
```




    array([3, 4])




```python
arr2[-1:2]
```




    array([], dtype=int32)




```python
arr2[-1:-2]
```




    array([], dtype=int32)




```python
# misc
temp_arr = arr2[0:2]
temp_arr
```




    array([1, 2])




```python
# it will change temp_arr & arr2
# temp_arr[1] = 99 
# print("temp_arr : ",temp_arr)
# print("arr2 : ",arr2)
```


```python
# to avoid this
temp_arr = arr2[0:2].copy()
temp_arr[1] = 99 
print("temp_arr : ",temp_arr)
print("arr2 : ",arr2)
```

    temp_arr :  [ 1 99]
    arr2 :  [1 2 3 4]
    


```python
arr3 = np.array([[1,2,3,4,5],[6,7,8,9,10]])
arr3
```




    array([[ 1,  2,  3,  4,  5],
           [ 6,  7,  8,  9, 10]])




```python
# slice row 0
arr3[0]
```




    array([1, 2, 3, 4, 5])




```python
# slice col 0
arr3[:,0]
```




    array([1, 6])




```python
# slice particular element
arr3[0,3]
```




    4




```python
#[row,slice]
arr3[1,0:2]
```




    array([6, 7])




```python
#[slice,col]
arr3[0:2,2]
```




    array([3, 8])



# Axis, Sorting & Other Functions


```python
arr4 = np.array([[1,2,3],
                 [4,5,6],
                 [7,8,9]])
arr4
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])




```python
# row wise sum
arr4.sum(axis=1)
```




    array([ 6, 15, 24])




```python
# col wise sum
arr4.sum(axis=0)
```




    array([12, 15, 18])




```python
# transpose
arr4.transpose()
```




    array([[1, 4, 7],
           [2, 5, 8],
           [3, 6, 9]])




```python
arr5 = np.array([[4,2,3],
                 [1,5,6],
                 [7,9,8]])
arr5
```




    array([[4, 2, 3],
           [1, 5, 6],
           [7, 9, 8]])




```python
# dot product for mxn and kxl -> n == k
arr4.dot(arr5)
```




    array([[ 27,  39,  39],
           [ 63,  87,  90],
           [ 99, 135, 141]])




```python
# cross product for mxn and kxl -> n == k
np.cross(arr4,arr5)
```




    array([[  0,   9,  -6],
           [  0, -18,  15],
           [-17,   7,   7]])




```python
# sorting
arr6 = np.array([[3,2,1,4],[7,6,5,8],[12,11,10,19]])

# row => axis = 1
print(np.sort(arr6,axis=1,kind='mergesort'))

# col => axis = 2
print(np.sort(arr6,axis=1,kind='quicksort'))

# default axis
print(np.sort(arr6,kind='heapsort'))
```

    [[ 1  2  3  4]
     [ 5  6  7  8]
     [10 11 12 19]]
    [[ 1  2  3  4]
     [ 5  6  7  8]
     [10 11 12 19]]
    [[ 1  2  3  4]
     [ 5  6  7  8]
     [10 11 12 19]]
    


```python
# ndim => number of array dimensions
arr6.ndim
```




    2



# Numpy Argsort, Argmin & Argmax 


```python
arr7 = np.arange(8)
arr7
```




    array([0, 1, 2, 3, 4, 5, 6, 7])




```python
# row*col = len(array)
arr7.reshape(4,2)
```




    array([[0, 1],
           [2, 3],
           [4, 5],
           [6, 7]])




```python
# if any value is -ve, it selects the dimension automaitcally

# (-1,x) row is automatically allocated
arr7.reshape(-1,4)
```




    array([[0, 1, 2, 3],
           [4, 5, 6, 7]])




```python
# (x,-1) col is automatically allocated
arr7.reshape(4,-1)
```




    array([[0, 1],
           [2, 3],
           [4, 5],
           [6, 7]])




```python
arr8 = np.array([4,1,5,2,7,6,3])

# Returns min value's element index
np.argmin(arr8)
```




    1




```python
# Returns max value's element index
np.argmax(arr8)
```




    4




```python
# Returns the indices that would sort an array
np.argsort(arr8)
```




    array([1, 3, 6, 0, 2, 5, 4], dtype=int64)




## Tutorial 
[Numpy Tutorial](https://youtu.be/Rbh1rieb3zc)
