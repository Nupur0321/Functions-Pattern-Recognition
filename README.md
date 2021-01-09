# Functions-Pattern-Recognition
Functions &amp; Pattern Recognition in R


Exercise 1

(i) Run the following two lines of code to generate a dataset corresponding to 5 different process batches:\
Production_Time <- c(1, 3, 6, 4, 9)\
Loss <- c(2, 5, 4, 5, 12)

(ii) Using the par command change the background colour to blue. Hint help(par) could be useful here\
(iii) Plot the Production_Time data and include a main label, a sublabel, an x label and a y label, colour the dots on your plot green and make the y axis span from 0 to 20 and the x axis from 0 to 10. Using the lines function join the dots on this picture.\
(iv) Add the Loss data to this plot in a similar way. You should distinguish the Loss data from the Production_Time data using different point markers and colours.\
(v) Add a legend to the plot to identify the Production_Time and Loss data.\
(vi) Add axes to the top and right of the plot with the same ticks as the bottom and left.\
(vii) Add some text to an empty area of the graph saying “Longer Production gives greater loss”. This text should not obscure any of the data.\
(viii) Add a small rectangle to the plot at any point(s) where the Production_Time and Loss data cross. These rectangles should be a different colour to the data points/lines.


solutions

1 (i)

Production_Time <- c(1, 3, 6, 4, 9)\
Production_Time\
Loss <- c(2, 5, 4, 5, 12)\
Loss

(ii)\
par(bg='blue', plot(Production_Time, Loss))

#Note - if x and y are of different length we cannot plot graph in a similar manner we have to use xlim and ylim

(iii) and (iv)\
plot(Production_Time,xlim = c(0,10), ylim = c(0,20), xlab = "x-axis", ylab = "y-axis", main = "production time data", col = "green", sub="linegraph")\
points(Production_Time, col="green")\
lines(Production_Time)\
axis(side = 2, at=c(0:20))\
axis(side =1, at=c(0:10))\
#sub function is used for sub label the graph
points(Loss, col="red", pch="*")\
lines(Loss)

(v)\
legend("center",legend = c("Production_Time","Loss"), col = c("green", "red"), pch=c("o","*"), lty=c(1,2), ncol=1)

#or 
#lty is to define the type of line we create by 1,2,3 etc and ncol defines either legend will be in row or column
legend(1, 5,legend = c("Production_Time","Loss"), col = c("green", "red"), pch=c("o","*"), lty= 1, ncol=2)

(vi)\
axis(side = 3, at=c(0:10))\
axis(side =4, at=c(0:20))

(vii)\
legend("topleft",legend = c("Longer Production gives greater loss"))



Exercise 2

(i) Type “iris” into the R console to view the iris dataset.\
(ii) Calculate the minimum and maximum of the four numeric columns\
(iii) Calculate the mean, median, mode, IQR, SD and Variance of each column\
(iv) Reset the background colour to white [from Exercise 1 (ii)].\
(v) Plot each of the four variables against the other variables.\
(vi) Generate a boxplot for each of the four columns


solution

(i)\
View(iris)

(ii)\
min(iris$Sepal.Length)\
min(iris$Sepal.Width)\
min(iris$Petal.Length)\
min(iris$Petal.Width)\
max(iris$Sepal.Length)\
max(iris$Sepal.Width)\
max(iris$Petal.Length)\
max(iris$Petal.Width)

(iii)\
mean(iris$Sepal.Length)\
mean(iris$Sepal.Width)\
mean(iris$Petal.Length)\
mean(iris$Petal.Width)\
median(iris$Sepal.Length)\
median(iris$Sepal.Width)\
median(iris$Petal.Length)\
median(iris$Petal.Width)\
mode(iris$Sepal.Length) # mode doesn't has standard inbuilt function 
IQR(iris$Sepal.Length)\
IQR(iris$Sepal.Width)\
IQR(iris$Petal.Length)\
IQR(iris$Petal.Width)\
sd(iris$Sepal.Length)\
sd(iris$Sepal.Width)\
sd(iris$Petal.Length)\
sd(iris$Petal.Width)\
var(iris$Sepal.Length)\
var(iris$Sepal.Width)\
var(iris$Petal.Length)\
var(iris$Petal.Width)\

summary(iris)

(iv)\
par(bg ="white", plot(iris))

(v)\
plot(iris$Sepal.Length, iris$Sepal.Width)\
plot(iris$Petal.Length, iris$Petal.Width, xlab = "petal length", ylab = "petal width", main = "iris datset", col= "purple")\
lines()

(vi)\
boxplot(iris$Species , iris$Sepal.Length, ylab ="sepal_length", xlab = "species" )


Exercise 3\
(i) Apply hierarchical clustering to the iris dataset.\
(ii) Investigate what the clusters mean in these data. Are they related to species?\
(iii) Do any data points appear erroneous?


solution

(i)Apply hierarchical clustering to the iris dataset. (dist is distance)\
library("e1071")\
m <- hclust(dist(iris[,1:4]), method="ave")\
plot(m)\
clusters = cutree(m, 3)\
table(clusters, iris$Species)


Exercise 4: Enter the following code:\
vec <- c("aadd3ddee","abaac345fgh","44555669.67","abbrt44 fgt445.962aa","fgddd aart")\
i) Use grep(), grepl() and grepexpr() to identify which elements of vec contain “aa”.\
ii) Identify which elements contain a space.\
iii) Identify which elements contain a full stop.\
iv) Identify which elements have “aa” at the beginning.\
v) Identify which elements have “aa” at the end.\
vi) Identify which elements have contain a number (digit)\
vii) Which element have the string “dd” followed by a digit\
viii) Which elements have something contained between two d’s?

solution

(i) Use grep(), grepl() and grepexpr() to identify which elements of vec contain “aa”.

vec <- c("aadd3ddee","abaac345fgh","44555669.67","abbrt44 fgt445.962aa","fgddd aart")\
vec\
grep("aa", vec)\
grepl("aa", vec)\
gregexpr("aa",vec)

(ii) Identify which elements contain a space.\
grep("\\s", vec)

(iii) Identify which elements contain a full stop.\
grep("[[:punct:]]", vec)

(iv) Identify which elements have “aa” at the beginning.\
element <- grep('^aa', vec)\
element\
vec[element]  # it will tell the name of element has "aa"

(v) Identify which elements have “aa” at the end.\
grep('aa$', vec)

(vi) Identify which elements have contain a number (digit)\
grep('\\d', vec)

(vii) Which element have the string “dd” followed by a digit\
grep('dd\\d', vec)

(viii) Which elements have something contained between two d’s?\
grep('d*d', vec)\
```
grep('d{2}', vec) #only for 2 d's
```

Exercise 5: Enter the following\
x <- “R Totorials are the best totorials”\
i) Use regular expressions to correct the spelling of tutorials in both instances.\
ii) Change the the capital T to lower case.\
iii) Add a full stop to the end of the sentence.

solution

x <- c("R Totorials are the best totorials")\
x

(i)Use regular expressions to correct the spelling of tutorials in both instances.

y <- gsub("Totorials" , "tutorials", x, ignore.case = T)\
y\
```
ignore.case is insensitive
```

(ii ) Change the the capital T to lower case.\
gsub("T", "t", x)

(iii) Add a full stop to the end of the sentence.\
gsub("$",".",x)


Exercise 6: Enter the following:\
y <- "line 4322: He is now 25 years old, and weights 130lbs"\
i) Change the numbers to underscores, leaving only the letters\
ii) Remove the comma\
iii) Change the letters to underscores, leaving only the numbers

solution

y <- "line 4322: He is now 25 years old, and weights 130lbs"\
y

i) Change the numbers to underscores, leaving only the letters\

z <- gsub("\\d", "_", y)\
z

(ii) Remove the comma\
gsub("[[:punct:]]", "", y)

(iii) Change the letters to underscores, leaving only the numbers\
gsub("\\w", "_", y) #replace all with underscore\
gsub("\\W", "_", y) #replace space with underscore\
gsub("\\D", "_", y)


Exercise 7: Enter the following \
a <- c("foo_5", "bar_7")\
i) Create a numeric vector called anum with the letters and underscores removed, i.e. retain the numeric vector (5,7).\
ii) Returning to the original vector, remove underscores and numbers. Merge this character vector into one character string called achar to read “foobar”

solution

a <- c("foo_5", "bar_7")\
a

(i) Create a numeric vector called anum with the letters and underscores removed, i.e. retain the numeric vector (5,7)\
anum <- gsub("\\D", "",a)\
anum\
as.numeric(anum)  #to pass string

(ii) Returning to the original vector, remove underscores and numbers. Merge this character vector into one character string called achar to read “foobar”\
anum1 <- gsub("[[:punct:]]\\d","", a)\
anum1\
foobar <- paste(anum1[1],anum1[2], sep = "")\
foobar


Exercise 8: Enter the following\
rcats <- c("r cat r", "r category r", "r locate r", "r rescat r")\
i) Identify which elements contain a word beginning with “cat”\
ii) Identify which elements contain a word ending with “cat”\
iii) Identify which elements contain the word “cat”

solution

rcats <- c("r cat r", "r category r", "r locate r", "r rescat r")\
rcats

(i) Identify which elements contain a word beginning with “cat”\
grep("\\scat", rcats)

(ii) Identify which elements contain a word ending with “cat”\
grep('cat\\s', rcats)

(iii) Identify which elements contain the word “cat”\
rcats[grep("cat", rcats)]     # this way print the element


Exercise 9

When transferring some data between different software, some unexpected errors can occur. Below is a vector that was imported to R, which should contain five numbers between 0 and 99999.

data <- c(‘jhhg12nbvc’,’12sifvfibvjfvnbuibv34’, “1dfgr66afsgder23afvfv”, “54bfgb,fhb.bgv44”, “dfb64dfb82cnb5)”

Use regular expressions and the appropriate functions to clean this data and create a vector data containing the numeric values.

solution
```
When transferring some data between different software, some unexpected errors can occur. Below is a vector that was imported to R, which should contain five numbers between 0 and 99999.
```

data <- c("jhhg12nbvc","12sifvfibvjfvnbuibv34", "1dfgr66afsgder23afvfv", "54bfgb,fhb.bgv44", "dfb64dfb82cnb5")\
data
```
Use regular expressions and the appropriate functions to clean this data and create a vector data containing the numeric values.
```
newdata <- gsub("\\D", "",data)\
newdata

[Advanced] Exercise 10\
Import the data set brainsize2.txt to R.\
i) View the data set. You will notice that an error occurred where the digit 6 was imported as the character “b”.\
ii) Fix this error throughout the data set and create a data frame with the cleaned data.\

solution

brainsize2 <- read.delim(file.choose())\
View(brainsize2)\
(i) View the data set. You will notice that an error occurred where the digit 6 was imported as the character “b”.\
(ii) Fix this error throughout the data set and create a data frame with the cleaned data.\
for (i in 1:ncol(brainsize2)) {\
  for (j in 1:nrow(brainsize2)) {\
    brainsize2[j,i] <- gsub('b','6',brainsize2[j,i], ignore.case = F)\
  }\
}\
brainsize2

toC = function(tf){\
  (tf-273)\
}\
toC(1)

x <- 1:20\
y <- 3*x\
df <- data.frame(x,y)\
df[[1]]


as.character(3.8)\
subset(iris,Species=="virginica")


paste("a", "b", sep = ":")\
x = c(0.1, 2, 4.3, 3.1, 5)\
x[x > 4]


a <- c(1,2,3)\
cat("a is the vector", a)\
x=1:100; plot(x,log(x))


as.numeric("b")\
as.logical(3.8)\
a <- c(1,2,3)\
paste("a is the vector", a)


x <- 1:20\
y <- 3*x\
df <- data.frame(x,y)\
df[1]


x <- 1:20\
y <- 3*x\
df <- data.frame(x,y)\
df[[1]]


