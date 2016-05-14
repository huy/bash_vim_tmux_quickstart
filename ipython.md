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
    df_train.head(5)

    df_train[df_train['place_id'] == 1757726713]

**add a new column **

    pickle = df_train[df_train['place_id'] == 1757726713][['x','y','time','accuracy']]
    pickle['distance'] = pickle.apply (lambda row: row['x']*row['x'] + row['y']*row['y'], axis=1)
    pickle.sort_values('distance')
    
