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


**references**

* http://nbviewer.jupyter.org/github/WeatherGod/AnatomyOfMatplotlib/blob/master/AnatomyOfMatplotlib-Part0-Intro2NumPy.ipynb
