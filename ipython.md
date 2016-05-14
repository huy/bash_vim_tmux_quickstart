## Preparation

**install**

    pip numpy pandas matplotlib ipython notebook
   
Note: `matplotlib` doe not in `virtualenv` as it must use framework python compiled with GUI library while 'virtualenv' 
always use non framework python probably installed by brew.
   
**start**

    ipython notebook
    
**show plot in the web page**

    %matplotlib inline
    

## numpy basic

**histogram**

    a, b = np.histogram([7, 5, 7, 8], 3)
    plt.bar(b[:-1], a, width = 1)

It returns 2 arrays, the first contains size of each bin i.e. frequency of each range of input value. The second is edges 
of these bins. There are 2 bins, the first has range `[5, 6)` , the second from `[6, 7)`, the last is `[7,8]`, 
    
    print(a)
    print(b)
    
    [1 0 3]
    [ 5.  6.  7.  8.]
    
**diff**

    x = np.array([1, 2, 4, 7, 0])
    np.diff(x)
    
    array([ 1,  2,  3, -7])
    
diff take input array `a` and returns array `b` such that which `b[i] = a[i+1] - a[i]`
