# Introduction to R programming
R is case sensitive.

Official Documentation: https://www.rdocumentation.org

## Basics
All commands can be directly run in R console. Comments start with `#`.
```r
> # Calculate 3+4
> 3+4
[1] 5
```
To view all stored data in the current workspace (I call it scope), use `ls()`.

## Arithmetic and Logic operations with R
Arithmetic Operations supported are :
Addition `+`, Subtraction `-`, Multiplication `*`, Division `/`, Exponentiation `^`, Modulo `%%`.

Logical OPerations supported are:
< > == <= >= !=

## Variables
To assign a variable: `my_var <- 6` is the syntax. To print the value of this variable, just type
the variable name in the console, like this `my_var`. Arithmetic operations can also be applied
to variables. Data types of the variables involved here must match to one another.

## Basic DataTypes in R
* **Numerics**: Decimal values like 4.5
* **Integers**: Integer values
* **Logical**: Boolean values TRUE and FALSE (no double quotes required)
* **Characters**: text or strings

Use `class()` to check the datatype of a variable.
```r
my_logical = FALSE
class(my_logical) # [1] "logical"
```

## Vectors
Vectors are one-dimension arrays that can hold numeric data, character data, or logical data.
In other words, a vector is a simple tool to store data.
Create a vector with the combine function `c()`. Place the vector elements separated by a comma between the parentheses.
[Documentation](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/c).
```r
numeric_vector <- c(1, 2, 3)
character_vector <- c("a", "b", "c")
1:6 # c(1,2,3,4,5,6)
```
Give a name to each element of a vector with the `names()` function.
```r
some_vector <- c("John Doe", "poker player")
days_vector <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
names(some_vector) <- days_vector
```
**OUTPUT**
```
Name     Profession
"John Doe" "poker player"
```
Arithmetic and logical operations of two vectors take place elementwise.
```r
a <- c(1, 2, 3)
b <- c(4, 5, 6)
c <- a + b # c(5, 7, 9)
a > 2 # [1] FALSE FALSE TRUE
```
* `sum()` to sum all elements
* `mean()` to find average of all elements
`c(vector1, vector2, vector3)` is like combining all three vectors.

### Accessing elements of vector
* `my_vector[2]` returns the second element in the vector.
* `my_vector[c(1,4)]` will return 1st and 4th element.
* `my_vector[2:4]` will return all elements from index 2 to 4, both inclusive.
* `my_vector["Monday"]`, `my_vector[c("Monday", "Wednesday")]` accessing can be done using the names of the elements
* When a logical vector is passed in square brackets, R will only select the elements that correspond to `TRUE`.

## Matrix
A matrix is a collection of elements of the same data type (numeric, character, or logical) arranged into a
fixed number of rows and columns. Since work is with rows and columns only, a matrix is called two-dimensional.
`matrix()` constructs a matrix. [Documentation](http://www.rdocumentation.org/packages/base/functions/matrix).
The parameters passed are as follows:
* **data**: The first argument is the collection of elements that R will arrange into the rows and columns of the matrix.
* **byrow**: accepts boolean. To fill elements by row or not.
* **nrow**: Number of rows to be formed.
* **dimnames**: list of length 2 to give names to row and column
Example: `matrix(1:9, byrow = TRUE, nrow = 3)`

Few functions applicable to matrices:
* `rownames(my_matrix)` accepts matrix and return a vector of list of rownames. It can also be used to assign row names.
`rowname(my_matrix) <- row_name_vector`. Similarly, `colnames(my_matrix)`.
* `rowSums(my_matrix)` to calculate row-wise sum. Accepts matrix as parameter. Similarly, `colSums(my_matrix)`
* `cbind(matrix, matrix2, vector1)` add a column or multiple columns to a matrix by merging matrices
and/or vectors together by column. Similarly, `rbind()`

Arithmetic and Logical operands and operator are applied to each element in the matrix. Be it a number of matrix
(operator applied elementwise)

### Accessing data in matrix
* `my_matrix[1,2]` access data in 1st row and 2nd column.
* `my_matrix[1:3,2:4]` access 1st to 3rd row 's 2nd to 4th column data.
* `my_matrix[,1]` select all elements in 1st column
* `my_matrix[1,]` select all elements in 1st row.


## Factor
The term factor refers to a statistical data type used to store categorical variables. The difference between a categorical variable and a continuous variable is that a categorical variable can belong to a limited number of categories. A continuous variable, on the other hand, can correspond to an infinite number of values.

It is important that R knows whether it is dealing with a continuous or a categorical variable, as the statistical models you will develop in the future treat both types differently. (You will see later why this is the case.)

A good example of a categorical variable is sex. In many circumstances you can limit the sex categories to "Male" or "Female". (Sometimes you may need different categories. For example, you may need to consider chromosomal variation, hermaphroditic animals, or different cultural norms, but you will always have a finite number of categories.)
