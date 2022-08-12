---
layout: post
title: "NumPy: the performance savant"
author: Emmanuel Cortes
---

## NumPy: N-Dimensional Arrays
Today is when we started to write performant simulations with the aid of NumPy. NumPy is a library that we'll use for it's n-dimensional arrays. While NumPy is a Python library, NumPy actually executes C code under the hood; allowing us to take advantage of C's speed. 

With NumPy we can do more with less code. For examples, `np.array`s add/multiply element-wise.
```Python
arr1 = np.array([1, 2])
arr2 = np.array([3, 1])

print(arr1 + arr2)  #  [4 3]
print(arr1 * arr2)  #  [3 2]
```

We can access NumPy array via chained brackets: `arr[1][3]`. Or the more Pythoic way: `arr[1,3]`.

Although `np.array`s have fixed size, through broadcasting we can manipulate arrays with similar shape (again with less code).

The [rules for broadcasting](https://numpy.org/doc/stable/user/basics.broadcasting.html#general-broadcasting-rules) two arrays:
1. they are equal, or
2. one of them is 1

With broadcasting we can scalar multiply.
```Python
print(3*arr1)  # [3 6]
```

If we align the shapes (..., z, y, x) then:
```Python
# compatible
arr3.shape  # (    3)
arr4.shape  # ( 8  3)

# compatible
arr3.shape  # ( 4  1  3)
arr4.shape  # (    5  3)
arr5.shape  # ( 4  5  1)

# not compatible arr4 x=6 but arr3 x=3
arr3.shape  # ( 4  1  3)
arr4.shape  # (    5  6)
arr5.shape  # ( 4  5  1)
```

You can use masks or logical expression to filter values from `np.array`s. Masks are particularly useful when applying the cut off for simulations.

```Python
arr1 = np.array([1, 2, 0])

mask = (arr1 != 0)  # boolean mask
print(mask)  # [ True True False ]
print(arr1[mask])  # [ 1 2 ]
```


Ultimately, with NumPy arrays we can do more with less which is important when modeling larger systems with more complex algorithms.


## Metropolis Monte Carlo meets NumPy.

Today for group discussion we discussed which functions can benefit from incorporating NumPy arrays.

We determined that the two most computationally costly functions are `calculate_total_energy` and `calculate_pair_energy`. `calculate_total_energy` contains a doubly nested for loop thus its time complexity is  O(n<sup>2</sup>). While `calculate_pair_energy` contains a for loop thus O(n) time complexity.

Additionally, NumPy can aid `read_xyz`. Since the input file contains the number of values to read we can initialize an `np.array` of appropriate length. The remaining code requires small changes to utilizes `np.array`-compatible functions (i.e. `math.pow` to `np.power`).