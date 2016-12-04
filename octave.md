Load data file and show fields stored in the data file

  >> load data.mat
  >> who
  Variables in the current scope:

  ans   data

  >> fieldnames(data)
  ans =
  {
    [1,1] = testData
    [2,1] = trainData
    [3,1] = validData
    [4,1] = vocab
  }
  >>
