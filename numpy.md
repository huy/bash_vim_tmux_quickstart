## numpy basic

**create multi dimension array**

    >>> a = np.arange(9) - 4
    >>> a
    array([-4, -3, -2, -1,  0,  1,  2,  3,  4])
    >>> a.reshape([3,3])
    array([[-4, -3, -2],
           [-1,  0,  1],
           [ 2,  3,  4]])
    >>>
    
**histogram**

    a, b = np.histogram([7, 5, 7, 8], 3)
    plt.bar(b[:-1], a, width = 1)

It returns 2 arrays, the first contains size of each bin i.e. frequency of each range of input value. The second is edges 
of these bins. There are 3 bins, the first has range `[5, 6)` , the second from `[6, 7)`, the last is `[7,8]`, 
    
    print(a)
    print(b)
    
    [1 0 3]
    [ 5.  6.  7.  8.]
    
**diff**

    x = np.array([1, 2, 4, 7, 0])
    np.diff(x)
    
    array([ 1,  2,  3, -7])
    
diff take input array `a` and returns array `b` such that which `b[i] = a[i+1] - a[i]`

**linspace**

    np.linspace(2.0, 3.0, num=5)
    array([ 2.  ,  2.25,  2.5 ,  2.75,  3.  ])
    
split an interval into evenly specified number of ranges. It is somehow similar to `np.arange` 

**arange**

    >>> np.arange(3)
    array([0, 1, 2])
    >>> np.arange(3.0)
    array([ 0.,  1.,  2.])
    >>> np.arange(3,7)
    array([3, 4, 5, 6])
    >>> np.arange(3,7,2)
    array([3, 5])
    
split an interval into evenly ranges of specified size, the default start is `0` and the default step is `1`.

**axis**

    >>> b = np.arange(12).reshape(3,4)
    >>> b
    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11]])

to get number of dimension and their size

    >>> b.ndim
    2
    >>> b.shape
    (3, 4)

there is notion of first dimension `axis=0` and last dimension `axis=-1`. The last one is array list scalar values. 
    
    >>> b.sum(axis=0)
    array([12, 15, 18, 21])
    >>> b.sum(axis=-1)
    array([ 6, 22, 38])
    >>> b.sum(axis=1)
    array([ 6, 22, 38]) 

create a new axis for each element of existing array is done as follow 

    >>> a = np.arange(4)
    >>> a
    array([0, 1, 2, 3])
    >>> c = a[:,np.newaxis]
    >>> c
    array([[0],
           [1],
           [2],
           [3]])
 
this is used mainly to control broadcasting effect of an vectorized operator

    >> a.reshape([2,2])
    >> a.shape
    (2, 2)
    >>> a[:,np.newaxis].shape
    (2, 1, 2)
    >>> a
    array([[0, 1],
           [2, 3]])
    >>> b
    array([1, 2])
    >>> a/b
    array([[ 0. ,  0.5],
           [ 2. ,  1.5]])
    >>> b.shape
    (2,)
    >>> a.shape
    (2, 2)
    >>> a/b[:,np.newaxis]
    array([[ 0. ,  1. ],
           [ 1. ,  1.5]])
 
**references**

* https://docs.scipy.org/doc/numpy-dev/user/quickstart.html
* http://nbviewer.jupyter.org/github/WeatherGod/AnatomyOfMatplotlib/blob/master/AnatomyOfMatplotlib-Part0-Intro2NumPy.ipynb
