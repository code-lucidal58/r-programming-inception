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

### Accessing elements of vector
Elements can be accessed using indexing, starting from 1. `my_vector[2]` returns the second element in the vector.
To select multiple elements in one go, use comma-separated indexing inside the square brackets.
`my_vector[c(1,4)]` will return 1st and 4th element. To select a range of elements use `:`.
`my_vector[2:4]` will return all elements from index 2 to 4, both inclusive. Similar accessing can
be done using the names of the elements. `my_vector["Monday"]`, `my_vector[c("Monday", "Wednesday")]`.
When a logical vector is passed in square brackets, R will only select the elements that correspond to `TRUE`.

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
