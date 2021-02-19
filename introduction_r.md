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

Use `summary()` to get a quick overview of a variable.
```r
x <- 7
summary(x)
#    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.
#      7       7       7       7       7       7
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
Factor refers to a statistical data type to store categorical variables.
The difference between a categorical variable and a continuous variable is that a categorical variable can belong to a limited number of categories.
A continuous variable corresponds to an infinite number of values.
It is important for R to know the variable type (categorial or continuous), as each type is treated differently during model development. Example of a categorical variable is gender ("Male", "Female", "Other"). Here, there are 3 factor levels.
`factor()` method accepts a vector and returns the factor levels. By default, it creates an unordered factor.
```r
gender <- c("Male", "Female", "Male", "Male", "Female")
factor_gender <- factor(gender)  # Levels: Female Male
```
There are two types of categorical variables:
* **nominal categorical variable**: variable without an implied order. All are at equal level. For example, animals_vector with the categories "Elephant", "Giraffe", "Donkey" and "Horse". Levels cannot be compared to one another.
* **ordinal categorial variables**: have a natural ordering. For example, temperature_vector with the categories: "Low", "Medium" and "High". "Medium" stands above "Low", and "High" stands above "Medium".
```r
animals_vector <- c("Elephant", "Giraffe", "Donkey", "Horse")
factor_animals_vector <- factor(animals_vector) # Levels: Donkey Elephant Giraffe Horse

# Ordered Factor
temperature_vector <- c("High", "Low", "High","Low", "Medium")
factor_temperature_vector <- factor(temperature_vector, order = TRUE, levels = c("Low", "Medium", "High"))
# Levels: Low < Medium < High
```
The levels in a factor can be assigned new names using `levels()` function. This function accepts a vector.
The sequence of the new names should be in alphabetic order of the old level names.
```r
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
levels(factor_survey_vector) <- c("Female", "Male")
```
Data comparison is easier using logical operators in ordered factors.
```r
speed_vector <- c("medium", "slow", "slow", "medium", "fast")
factor_speed_vector <- factor(speed_vector, ordered = TRUE, levels = c("slow", "medium", "fast"))
da2 <- factor_speed_vector[2]
da5 <- factor_speed_vector[5]
da2>da5 # FALSE
```

## Data Frames
A data frame stores data in rows and columns. A column has same data type. Different columns can have different data types.
Hence it is a 2-D object. `head()` and `tail()` return the first 5 and last 5 rows of the data frame. `str()` method returns the structure of the data frame.
NOTE: str stands for structure, not string. It returns number of observations, variables, full list of variable names,
data type of each variable, and the first observation. `data.frame()` accepts vectors as columns. Syntax for
accessing data is same as for matrix. Apart from that, columns can be accessed with index number as well as column name.
Example, `planets_df[1:5,"diameter"]` will return first 5 values of the diameter column.
To select an entire column, these syntax are valid: `planets[,3]`, `planets[,"diameter"]`, and `planets$diameter`

Dataframes allow accessing through bool vector. Only those rows are returned for whom the boolean vector element at the
same index is TRUE. The exact same thing can be done using `subset()` function.
```r
my_df <- data.frame(scores, comments)
subset(my_df, subset = some_condition)
subset(my_df, subset = scores > 1) # diameter is a column
```
In the above code, `some_condition` can be a boolean vector.  
`order()` gives the ranked position of each element when it is applied on a variable, such as a vector.
```r
a <- c(100, 10, 1000)
order(a)
# 2 1 3
a[order(a)]
# 10 100 1000

b[order(b$prop),] # if b is a dataframe and prop is a column name
```

## Lists
A list is a datatype that can hold any other dataype objects, like matrix, vector, another list, in an order way.
The objects do not have to be related to one another. It is created using `list()` function. Components of a list
can also be named, like vectors.
```r
my_list <- list(my_vector, my_matrix, my_df)
names(my_list) <- c("vec", "mat", "df") # OR
my_list <- list(vec=my_vector, mat=my_matrix, df=my_df)
```
The components of a list need not be of same length. This is how it is different from a dataframe.
### Accessing list components
* **by index**: `my_list[[1]]` to access the first element
* **by name**: There are two ways for this: `my_list[["name"]]` or `my_list$name`
Now, accessing specific element of the accessed component depends on the type of datatype. If the first component
is a vector, `my_list[[1]][2]` will return the 2nd element of the vector in position 1 of the list.
