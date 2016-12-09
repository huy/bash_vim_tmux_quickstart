Load data file and show fields stored in the data file

    >> load data.mat
    >> who
    Variables in the current scope:

    ans   data

Clear all variable

    >>clear all
    
Show structure of a field

    >> fieldnames(data)
    ans =
    {
      [1,1] = testData
      [2,1] = trainData
      [3,1] = validData
      [4,1] = vocab
    }
    >>

Show dimension of a variable (ncol x nrow)

    >> size(data.trainData)
    ans =

            4   372550

Broadcasting - reshape the operand matrixes so they agree in dimension, replicating elements to fill new matrixes

    >>x = [1 2 3;
         4 5 6;
         7 8 9];

    >>y = [10 20 30];

    >>x + y

      11   22   33
      14   25   36
      17   28   39

Rearrange data of a matrix into new matrix, data is accessed in column major order (https://en.wikipedia.org/wiki/Row-_and_column-major_order)

    >> reshape([1,2,3,4,5,6],2,3)
    ans =

       1   3   5
       2   4   6    

Getting help

    >> help sum
    'sum' is a built-in function from the file libinterp/corefcn/data.cc

     -- Built-in Function: sum (X)
     -- Built-in Function: sum (X, DIM)
