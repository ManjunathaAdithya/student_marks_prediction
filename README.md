# student_marks_prediction
#Prediction of student marks based on number of study hours


#READING THE DATA
library(readxl)
marks <- read_excel("marks.xlsx")
View(marks)


#APPLYING THE MACHINE LEARNING MODEL i.e, LINEAR REGRESSION MODEL
Linearmodel <- lm(Scores~Hours, data = marks) 
Linearmodel


# ASSIGNING THE INTERCEPT VALUE TO C IN ORDER TO PERFORM Y=MX+C
L <- Linearmodel$coefficients
L <- as.data.frame(L)
c <- as.integer(L[1,1])
m <- as.integer(L[2,1])


#PREDICTING THE MARKS FOR THE GIVEN HOURS OF STUDY
#x <- as.integer(readline(prompt = "Enter the hours of study"));
x <- 6.0
y <- m*x+c
y

#PLOTTING THE OBTAINED LINEAR REGRESSION MODEL
plot(Scores~Hours, data = marks, pch = 19, cex = .875, col="dark red", 
     main = "Percentage of a student based on the number of study hours",
     xlab = "Hours of study" , ylab = "Obtained scores ")
abline(Linearmodel,lwd =1.8, col="dark green")
print("Predicted score is " )
print(y)

