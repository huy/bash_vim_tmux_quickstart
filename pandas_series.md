# Pandas Series

**create series**

One dimension array of values with index that can be any data types not just integer. 

    >>> import pandas as pd
    >>> s = pd.Series([2,3,5,8],index=['a','b','c','d'])
    >>> s
    a    2
    b    3
    c    5
    d    8
    >>> s['c']
    5
    >>> s.values
    array([2, 3, 5, 7])
    >>> u = pd.Series(range(0,10))
    >>> u
    0    0
    1    1
    2    2
    3    3
    4    4
    5    5
    6    6
    7    7
    8    8
    9    9
 
Series object behave like dictionary where index column contains all keys.

**access value**

We can access value by index key or row position

    >>> s = pd.Series([2,3,5,8],index=['a','b','c','d'])
    >>> s
    a    2
    b    3
    c    5
    d    8
    dtype: int64
    >>> s.loc['c']
    5
    >>> s['c']
    5    
    >>> s.iloc[2]
    5
    >>>
    
**iterate over pair of key, value**    
    
Series object behave like dictionary, we can iterate over it to get value of both key and value

    >>> s = pd.Series([2,3,5,8],index=['a','b','c','d'])
    >>> [x for x in s.iteritems()]
    [('a', 2), ('b', 3), ('c', 5), ('d', 8)]
    
**create a mask**

    >>> m = s >= 4
    >>> m
    a    False
    b    False
    c    True
    d    True
    dtype: bool
    
**select rows using boolean array**

    >>> s.loc[m]
    c    5
    d    7
    dtype: int64

    
