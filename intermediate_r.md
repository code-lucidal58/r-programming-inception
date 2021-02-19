# Intermediate R

## Conditionals and Control Flows
### Relational Operators
All operators return a logical value. Can be used to compare characters, numerics,
and other logical values. Operator are
Equality (==) Inequality (!=) Less and Greater than (< > >= <=)
```r
TRUE<FALSE # FALSE becaue TRUE is 1 and FALSE is 0
```
One side can be a vector/matrix, other can be numeric/vector/matrix.

### Logical Operators
& (and), | (or), and ! (not)
Function is same as any other programming language. When these are used with vector or matrices,
element-wise comparison is made.
When && and || (double symbols) are used with vectors, it compares the first element of each operand.

### Conditional Statements
Condition should be inside parentheses.
```r
if(condition) {
  exp1
} else if(condition2) {
  exp2
} else {
  exp3
}
```

## Loops
