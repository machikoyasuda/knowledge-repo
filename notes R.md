## Expressions:
Numbers
"Strings"

## Logical values: booleans
TRUE (T)
FALSE (F)
==, not =

## Variables: 
x <- 42
store values, T, F in variables, re-assign them any time and used in any expression in place of original result

## Functions:
sum(1, 3, 5) - sum
rep("Yo",­ times­ = 3) - repeat
sqrt() - square root
help(sum) - help
example(sum) - example use

## Files in Terminal: 
save as: plaintextfile.R
list files: list.files()
run script: source("file.R")

------

##Vectors: list of values of numbers, strings, logical values, or any other time as long as they are the same type 

c(4, 8, 9) - c for combine
c('a', 'b', 'c') 

##Sequence vector: sequence of numbers

start:end - 5:9
seq(start,end) - seq(5,0)
seq(5,0,0.5) - increment other than 1

##Vector Access - store vector in variable, access individual value within vector with []

var <- c('a', 'b', 'c')
var[3]
c

var[c(1, 3)] (two values)
a, c

var[1:3] (range of values)
"a" "b" "c"

var[5:7] <- c('the', 'pop', 'dek') (assign values in range of values)

** R STARTS INDICES AT 1 **

## Assignment - assign new values within existing vector

var[4] <- "dog"

## Vector Names: labeling data
Asigning names to vector elements by passing a second vector filled with names to the names function. 

names(vector_var) <- c("name1", "name2", "name3")

## Plotting a vector
barplot(vector_name) - draws bar chart of vector

barplot(first:last) - draws range

## Vector Math
Most operations can be done on vectors. 

a <- c(1,2,3)
a + 1 
// adds to each vector value

**scalar** value: a single value

b <- c(4,5,6)
a + b
// adds two vectors

a == c(1, 9, 3)
// compares two vectors, results in logical values

## Scatter plotting

plot takes two vectors, one for x another for y and draws a graph with them 

x <- seq(1, 20, 0.1)
y <- sin(x)
plot(x,y)

## NA Values
NA = sample not available

To sum a vector with a NA, and remove NA:
sum(a, na.rm=TRUE)

======

## Matrices: data in rows and columns, 2-d array

// create matrix
matrix(default, rows, cols)

matrix(0,3,4)
  [,1] [,2] [,3] [,4]
[1,]    0    0    0    0
[2,]    0    0    0    0
[3,]    0    0    0    0

// fill matrix with vector
a < 1:12 # create vector range

matrix(vector, rows, cols)
matrix(a, 3, 4)
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12

> matrix(1:25, 5, 5)
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    6   11   16   21
[2,]    2    7   12   17   22
[3,]    3    8   13   18   23
[4,]    4    9   14   19   24
[5,]    5   10   15   20   25


// reshape vector

dim(vector) <- c(row, col)

// matrix access

matrix[2,3] (2nd row, 3rd col)
matrix[2,] (get entire row 2)
matrix[,4] (get entire col 4)
matrix[,2:4] (col 2 - 4)


// re-assign

matrix[1,2] <- 0 

// assign more into matrix

matrix[4,6] <-0
(assign 0 to row 4 col 6)

## Plotting Matrices
contour(matrix) - contour map
persp() - 3d perspective
persp(, expand=0.1)
image() - heat map

======

Summary Statistics

## Mean -> average
barplot(matrix)
abline(h = mean(matrix))
meanValue <- mean(pounds)

// add line at mean

## Median -> middle
median(matrix)
abline(h = median(limbs))

## Standard Deviation
"Standard Deviation" from the mean = range of typical values for a data set.

Shows how much they typically vary from the average.

deviation <-sd(vector)
abline(h = meanV­alue + devia­tion) 
// one sd above mean

======

Factors 

## Factors

Group data into categories called factors - special collection types 

// create factor
types <- factor(vector)

> chests <- c('gold', 'silver', 'gems', 'gold', 'gems')
> types <- factor(chests)
> print(chests)
[1] "gold"   "silver" "gems"   "gold"   "gems"  

> print(types)
[1] gold   silver gems   gold   gems  
Levels: gems gold silver

// factor's levels = group of unique values (no repeats), no "" b/c they are not strings but integer references to factor's levels

// look at integer references
as.integer(types)
[1] 2 3 1 2 1

levels(types)
[1] "gems"   "gold"   "silver"

## Plotting Factors
plot two vectors
> weights <- c(300, 200, 100, 250, 150)
> prices <- c(9000, 5000, 12000, 7500, 18000)
> plot(weights, prices)

**pch** plot characters

plot(weights, prices, pch=as.integer(types))

// add legend

hardcoded
legend("topright", c("gems", "gold", "silver"), pch=1:3)

derive from levels
legend("topright", levels(types), pch=1:length(levels(types)))

### Data Frames

Data frames similar to database table - has specific number of cols, each with values of a particular type. Indeterminate number of rows. 

/ Convert vector<-data.frame

vector <- data.frame(col1, col2, col3)

 print(treasure)
  weights prices  types
1     300   9000   gold
2     200   5000 silver
3     100  12000   gems
4     250   7500   gold
5     150  18000   gems

/ Access data.frames
variable[[2]] (2nd column)

vector[["column name"]]

shorthand: vector$col

**treasure$types**
[1] gold   silver gems   gold   gems  
Levels: gems gold silver

/ Loading data.frames from CSV

list.files()
"targets.csv" "infantry.txt"

"Port","Population","Worth"
"Cartagena",35000,10000
"Porto Bello",49000,15000
"Havana",140000,50000
"Panama City",105000,35000

/ Load CSV

read.csv("targets.csv")

Load CSV and name it as variable

variable <- read.csv("target.csv")

/ Load tab-separated
read.table­("infantry­.txt", sep="­\t") 

           V1       V2
1        Port Infantry
2 Porto Bello      700
3   Cartagena      500
4 Panama City     1500
5      Havana     2000

read.table("infantry.txt", sep="\t", header=TRUE)
         Port Infantry
1 Porto Bello      700
2   Cartagena      500
3 Panama City     1500
4      Havana     2000


# Merging Data Frames

Joins two data frames together using the contents of one or more columns. By default, it joins frames on columns with the same name. 

targets <- read.csv("targets.csv")

infantry <- read.table("infantry.txt", sep="\t", header=TRUE)

merge(x = targe­ts, y = infan­try) 

// Test for correlation

cor.test()

The key result we're interested in is the "p-value". Conventionally, any correlation with a p-value less than 0.05 is considered statistically significant, and this sample data's p-value is definitely below that threshold.

We can, if we calculate the linear model that best represents all our data points (with a certain degree of error). The lm function takes a model formula, which is represented by aresponse variable (piracy rate), a tilde character (~), and a predictor variable (GDP). (Note that the response variable comes first.)

line <- lm(co­untries$Pi­racy ~ count­ries$GDP) 

## ggplot 2 ##

install.packages("ggplot2")

help(packa­ge = "ggpl­ot2") 

--

library(ggplot2)
qplot(w, p, c = types)
