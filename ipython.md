## Preparation

**install**

    pip numpy pandas matplotlib ipython notebook
   
Note: `matplotlib` doe not in `virtualenv` as it must use framework python compiled with GUI library while 'virtualenv' 
always use non framework python probably installed by brew.
   
**start**

    ipython notebook
    
**show plot in the web page**

    %matplotlib inline
    
## pandas basic

**read a csv file**

    import pandas as pd
    df_train = pd.read_csv('../input/train.csv')

**show metadata**

    df_train.info()
    
    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 29118021 entries, 0 to 29118020
    Data columns (total 6 columns):
    row_id      int64
    x           float64
    y           float64
    accuracy    int64
    time        int64
    place_id    int64
    dtypes: float64(2), int64(4)

**show mean, std, min, max**

    df_train.describe()
    
**get column(s)**

    df_train['place_id']
    df_train[['place_id','x','y']]
    
**select row(s)**
    
    df_train.head(5)
    df_train.tail(5)
    df_train[df_train['place_id'] == 1757726713]

**add a new column**

    pickle = df_train[df_train['place_id'] == 1757726713][['x','y','time','accuracy']]
    pickle['distance'] = pickle.apply (lambda row: row['x']*row['x'] + row['y']*row['y'], axis=1)
    pickle.sort_values('distance')

**take a simple random sample**

    df_train.sample(n=1000000)

**count value**

    df_placecounts = df_train["place_id"].value_counts()

this will create `Series` object with `place_id` as index order by count of value, so we can take list of top 10 `place_id` as

    list(df_placecounts[:10].index)


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