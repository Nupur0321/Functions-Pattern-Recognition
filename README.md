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

