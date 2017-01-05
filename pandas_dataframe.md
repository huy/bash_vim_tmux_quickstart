
## pandas

**create series and data frame**

    >>> c1 = pd.Series([1,2,3])
    >>> c2 = pd.Series(['a','b','c'])
    >>> f = pd.DataFrame({'C1': c1,'C2': c2})
    >>> f.head()
       C1 C2
    0   1  a
    1   2  b
    2   3  c

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
    
**select rows**
    
    df_train.head(5)
    df_train.tail(5)
    df_train[df_train['place_id'] == 1757726713]
    
we can use either python `[]` or  `loc[]` i.e. selection  by label

    >>> df = pd.DataFrame({'a': [1,2,3], 'b': [4,5,6]})
    >>> df
       a  b
    0  1  4
    1  2  5
    2  3  6
    >>> df[df.a>2]
       a  b
    2  3  6
    >>> df.loc[df.a>2]
       a  b
    2  3  6
    >>>

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

**iterate over row**

    for index, row in df.iterrows():
       print(row['c1'], row['c2'])
       
**convert to list of dict**

    list = df_train.to_dict(orient='records')

this will create list of dictionary with column names as keys

**drop missing value**

    page_reading = pd.read_csv('reading.csv', delimiter='|')
    page_reading = page_reading.dropna()

**change reorder columns**

    page_modified = pd.read_csv('modifier.csv')
    
    page_modified = page_modified[['username', 'contentid', 'lastmoddate']] # select columns
    page_modified.columns = ['username', 'pageid', 'timestamp'] # rename columns

**label encoding**

    df['username'] = df['username'].astype('category')
    df['usernum'] = df['username'].cat.codes.copy()
    df[['username','usernum']]
