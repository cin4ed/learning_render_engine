# Matrices
In computer graphics, matrices are used to calculate object transforms like
translation which is movemment, scaling in X, Y and Z axis, and rotation around
the X, Y and Z axis.

Sometimes we need to change the position of objects from one coordinate system
to the other, which are called space transforms.

Matrices are represented as having rows and columns, A matrix with "m" number of
rows and "n" number of columns is said to be a matrix of size m * n.

Each element of a matrix is represented as indices ij where i specifies the row
number and j represents the column numbmer.

So, a matrix M of size 3 * 2 is represented as follows:

```
    |m11  m12|
M = |m21  m22|
    |m31  m32|
```

So, a matrix M has three rows and two columns and each element is represented as
m11, m12 and so on until m32, which is the size of the matrix.

In 3D graphics progamming, we will be mostly dealing with a 4 * 4 matrix.

```
    |m11  m12  m13  m14|
M = |m21  m22  m23  m24|
    |m31  m32  m33  m34|
    |m41  m42  m43  m44|
```

We can also have a single-dimension matrix like a vector which is called the row
vector or a columnd vector as shown as follows:

```
B = [b21  b22  b23  b24]

    |c1|
M = |c2|
    |c3|
    |c4|
```

- Two matrices are equal if the number of rows and columns are the same and if
  the corresponding elements are of the same value.

- Two matrices can be added if they have the same number of rows and columns. We
  add each element of the corresponding location on both matrices to get a third
  matrix of the same dimension as the added matrices.

## Matrix addition and subtraction
Consider the following two A and B matrices. Both of these are of the size as 3
* 3, shown as follows:

```
    |A  B  C|
A = |D  E  F|
    |G  H  I|

    |a  b  c|
B = |d  e  f|
    |g  h  i|
```

Then C = A + B is given as:


```
    |A+a  B+b  C+c|
C = |D+d  E+e  F+f|
    |G+g  H+h  I+i|
```

Matrix subtraction works in the same way when each element of the matrix is
subtracted with the corresponding element of the other matrix.

## Matrix multiplication
Let's see how a scalar value can be multiplied to a matrix by multiplying each
element of the matrix by the same scalar value. This will give us a new matrix
of the same dimension as the original matrix.

Consider a Matrix A multiplied by some scalars, then S * A is given as follows:

```
        |A  B  C|   |S*A  S*B  S*C|
C = S * |D  E  F| = |S*D  S*E  S*F|
        |G  H  I|   |S*G  S*H  S*I|
```

Two A and B matrices can be multiplied, provided that the number of columns af A
is equal to the numbers of rows of B. So, if matrix A has the dimension a * b
and B has the dimension X * Y then for A to be mutiplied with B, b should be
equal to X.

The resultant size of the matrix will be a * Y. Two matrices are multiplied as
follows:

```
    |a11  a12|
A = |a21  a22|
    |a31  a32|

B = |b11  b12  b13|
    |b21  b22  b23|
```

Here, the size of A is 3 * 2 and the size of B is 2 * 3, therefore the resultant
matrix C will be of size 3 * 3:

```
            |a11*b11 + a12*b21  a11*b12 + a12*b22  a11*b13 + a12*b23|
C = A * B = |a21*b11 + a22*b21  a21*b12 + a22*b22  a21*b13 + a22*b23|
            |a31*b11 + a32*b21  a31*b12 + a32*b22  a31*b13 + a32*b23|
```

Keep in mind that matrix multiplication is not commutative, meaning that A * B
!= B * A. In fact, in some cases it is not even possible to multiply the other
way around just like the case above, as the number of columns of B is no equal
to the number of rows of A.

You can also multiply a vector matrix with a regular matrix as follows:

```
    |A  B  C|     |x|
A = |D  E  F| V = |y|
    |G  H  I|     |z|
```

The resultant will be a one dimensional vector of size 3 * 1 as shown as
follows:

```
            |A*x + B*y + C*z|
C = A * V = |D*X + E*y + F*z|
            |G*x + H*y + I*z|
```

Note that when multiplying the matrix with the vector matrix, the vector is on
the right of the matrix. This is done so that the matrix of size 3 * 3 is able
to multiply the vector matrix of size 3 * 1.

When we have a matrix with just one column, this is called column major matrix.
So, Matrix C is a column major matrix just like matrix V, which is also a column
major matrix.

If the same vector V was expressed with just a row it would be called a row
major matrix and would look like as follows:

```
V = [x y z]
```

So how would we multiply a matrix A of size 3 * 3 with a row major matrix V of
size 1 * 3, since the internal dimensions don't match?

The simple solution here is that instead of multiplying matrix A * V, we
multiply V * A!

This way the internal dimensions of the vector matrix and the regular matrix
will match 1 * 3 and 3 * 3 and the resultant matrix will aso be a row major
matrix.

## 4 * 4 Matrices
If we are going to be using 4 * 4 matrices, how would we multiply a 4 * 4 matrix
using the coordinates of x, y, and z?

So, when multiplying a 4 * 4 matrix with point X, Y, and Z, we add one more row
to the column major matrix and set the value of it to 1.

The new point will be (X, Y, Z, 1), which is called a homogeneous point. This
makes it easy to multiply a 4 * 4 matrix with a 4 * 1 vector.

```
    |A B C D|       |x|
A = |E F G H|   P = |y| 
    |I J K L|       |z| 
    |M N O P|       |1|
```

```
    |A*x + B*y + C*z + D*1|
A = |E*x + F*y + G*z + H*1|
    |I*x + J*y + K*z + L*1|
    |M*x + N*y + O*z + P*1|
```

Matrix multiplication can be extrapolated to multiplication of a 4 * 4 matrix
with another 4 * 4 matrix:

```
    |A B C D|       |a b c d|
A = |E F G H|   B = |e f g h|   
    |I J K L|       |i j k l|
    |M N O P|       |m n o p|

    |Aa + Be + Ci + Dm  Ab + Bf + Cj + Dn  Ac + Bg + Ck + Do  Ad + Bh + Cl + Dp|    
C = |Ea + Fe + Gi + Hm  Eb + Ff + Gj + Hn  Ec + Fg + Gk + Ho  Ed + fh + Gl + Hp|
    |Ia + Je + Ki + Lm  Ib + Jf + Kj + Ln  Ic + Jg + Kk + Lo  Id + Jh + Kl + Lp|
    |Ma + Ne + Oi + Pm  Mb + Nf + Oj + Pn  Mc + Ng + Ok + Po  Md + Nh + Ol + pp|
```

## Identity matrix
An Identity is a special kind of matrix in which the number of rows is equal to
the number of columns called a square matrix. In an identity matrix the elements
in the diagonal of the matrix are all 1 and the rest of the elements are 0.

```
    |1 0 0 0|
A = |0 1 0 0|
    |0 0 1 0|
    |0 0 0 1|
```

Identity matrix acts in a similar way to how we get a result when we multiply
any number with 1 and get the same number. Similarly, when we multiply any
matrix with an identity matrix, we get the same matrix.

## Matrix transpose
A transpose of a matrix occurs when the rows and columns are interchanged with
each other. So, the transpose of a m X n matrix is n X m. The transpose of any
matrix M is writer as M^t. The transpose of matrix is a as follows:

```
    |A B C D|         |A E I M|
A = |E F G H|   A^t = |B F J N|
    |I J K L|         |C G K O|
    |M N O P|         |D H L P|
```

Observe how the elements in the diagonal of the matrix remain in the same place
but all the elements around the diagonal have been swapped.

In Matrices, this diagonal of the matrix which runs from the top left to the
bottom right is called the main diagonal.

Obviously if you transpose a transposed matrix, you get the original matrix, so
(A^t)^t = A.

## Matrix inverse
An inverse of any matrix is such that any matrix, when multiplied by its
inverse, will result in an identity matrix. For a matrix M, the inverse of the
mmatrix is denoted as M^-1.

Inverse is very useful in graphics programming when we want to undo the
multiplication of a matrix.

For example, Matrix M is equal to A * B * C * D where A, B, C and D are also
matrices. And now we want to know what A * B * C is, instead of multiplying the
three matrices, which is a two-step operation as you will first multiply A with
B and then multiply the resulting matrix with.

You can multiply M with D^-1 and that will yield the same result:

```
M = A * B * C * D
A * B * C = M * D^-1
```
