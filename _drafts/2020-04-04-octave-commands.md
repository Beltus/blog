size(A) = dimensions of matrix A

size(A, 1) # number of rows in matrix A

size(A,2) #number of columns in matrix A

A(2,3) # retrieve the element in the 2nd row and 3rd column

A(2,:) # retrieves every element in row 2 of matrix A
A(:,1) #retrieve elements of column 1 of matrix A
A([1 3], :) #retrieve all elements of the 1st and 3rd rows of matrix A


H = ones(5) # creates 6 x 6 matrix of all ones
 J = ones(1,5) # create a 5 element row-vector of ones
 L = ones(5,1) # creates a 5 element column vector of ones
A = [A , [1; 2; 5]] # adds the columnn vector to matrix A

C  = A * B # multiplies 2 matrices

D = A .* B # Does element-wise multiplication

A' # Transpose of matrix A


sum(A,1)  #gives the sum of all the columns of the matrices A
sum(A,2) # gives the sum of the rows in matrix A

max(A) #gives the max value of every column in the matrix A

max(max(A))  or max(A(:))#gets the maximum value of the matrix A


pinv(A) # computes the inverse of a matrix

v = zeros(10:1) #creates an empty vector of length 10. V is flexible and can take any number of elements


## For loop

for i = 1:10,
  v(i) = i * 2 ;
end;


## While Loop  with If-else

i = 1;
while i < 15,
    v(i) = i^2;
    i = i + 1;
    if i == 10,
       break;
    else,
       continue;
    end;
end;

* Function name should be the same as file name in octave


## Add column of ones to matrix and also extract the first column from the matrix at same TIME
A =

   17   24    1    8   15
   23    5    7   14   16
    4    6   13   20   22
   10   12   19   21    3
   11   18   25    2    9

>> v = [ones(5,1) , A(:,1)]
v =

    1   17
    1   23
    1    4
    1   10
    1   11
