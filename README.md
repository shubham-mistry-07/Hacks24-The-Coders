# Main
[11/10, 10:38 AM] Shubham: num_vec <- c(10, 20, 30, 40)
print("Numeric Vector:")
print(num_vec)
char_vec <- c("Apple", "Banana", "Cherry")
print("Character Vector:")
print(char_vec)
log_vec <- c(TRUE, FALSE, TRUE, FALSE)
print("Logical Vector:")
print(log_vec)
seq_vec <- 1:10
print("Sequence Vector using ':' operator:")
print(seq_vec)
even_seq <- seq(from = 2, to = 20, by = 2)
print("Even sequence from 2 to 20:")
print(even_seq)
[11/10, 10:38 AM] Shubham: decimal_seq <- seq(0, 1, length.out = 5)
print("Sequence of 5 numbers between 0 and 1:")
print(decimal_seq)
rep_num <- rep(5, times = 4)
print("Repeated number vector:")
print(rep_num)
rep_seq <- rep(1:3, times = 2)
print("Repeated sequence:")
print(rep_seq)
rep_each <- rep(1:3, each = 2)
print("Each element repeated twice:")
print(rep_each)
empty_vec <- vector(mode = "numeric", length = 5)
print("Empty numeric vector of length 5:")
print(empty_vec)
x <- c(10, 20, 30, 40, 50)
print("Original Vector:")
print(x)
print("First element:")
print(x[1])
print("Elements 2 to 4:")
print(x[2:4])

[11/10, 10:39 AM] Shubham: library(readxl) 
library(writexl)
student_data <- data.frame( 
Name = c("Amit", "Riya", "Karan", "Sneha", "Tina"), 
Age = c(21, 20, 22, 19, 23), 
Marks = c(85, 90, 78, 88, 95) 
)
print("Original Data Frame:") 
print(student_data)
write.csv(student_data, "student_data.csv", row.names = FALSE) 
print("Data exported to 'student_data.csv' successfully!")
imported_csv <- read.csv("student_data.csv") 
print("Imported Data from CSV:")
[11/10, 10:39 AM] Shubham: print(imported_csv)
print("Average Marks of Students:") 
print(mean(imported_csv$Marks))
print("Maximum Marks:") 
print(max(imported_csv$Marks))
print("Minimum Marks:") 
print(min(imported_csv$Marks))
print("Students Scoring Above 85:") 
print(subset(imported_csv, Marks > 85))
write_xlsx(student_data, "student_data.xlsx") 
print("Data exported to 'student_data.xlsx' successfully!")
imported_excel <- read_excel("student_data.xlsx") 
print("Imported Data from Excel:") print(imported_excel)
print("Sorted Data (by Marks):") 
sorted_data <- imported_excel[order(imported_excel$Marks, decreasing = TRUE), ] print(sorted_data)
print("Add a new column: Result (Pass/Fail)") 
imported_excel$Result <- ifelse(imported_excel$Marks >= 80, "Pass", "Fail") print(imported_excel)

[11/10, 10:40 AM] Shubham: rm(list = ls())
makePersonS3 <- function(name, age) {
 obj <- list(name = name, age = age)
 class(obj) <- "PersonS3"
 return(obj)
}
print.PersonS3 <- function(x) {
 cat("Person Details:\n")
 cat("Name:", x$name, "\n")
 cat("Age :", x$age, "\n")
[11/10, 10:40 AM] Shubham: }
greet <- function(x) UseMethod("greet")
greet.PersonS3 <- function(x) {
 cat("Hello", x$name, "! You are", x$age, "years old.\n")
}
p1 <- makePersonS3("Rohit", 38)
print(p1)
greet(p1)

[11/10, 10:41 AM] Shubham: m <- matrix(c(5, 2, 8, 1, 9, 4, 7, 3, 6), nrow = 3, byrow = TRUE) 
print(m)
max_pos <- which(m == max(m), arr.ind = TRUE) 
min_pos <- which(m == min(m), arr.ind = TRUE)
cat("Maximum Value:", max(m), "at Row:", max_pos[1], "Column:", max_pos[2], "\n") 
cat("Minimum Value:", min(m), "at Row:", min_pos[1], "Column:", min_pos[2], "\n")
df1 <- data.frame(ID = c(1, 2, 3, 4), Name = c("A", "B", "C", "D")) 
df2 <- data.frame(ID = c(3, 4, 5, 6), Age = c(23, 25, 28, 30))
inner_join <- merge(df1, df2, by = "ID") 
left_join <- merge(df1, df2, by = "ID", all.x = TRUE) 
right_join <- merge(df1, df2, by = "ID", all.y = TRUE) 
outer_join <- merge(df1, df2, by = "ID", all = TRUE)
cat("\nInner Join:\n"); print(inner_join) 
cat("\nLeft Join:\n"); print(left_join) 
cat("\nRight Join:\n"); print(right_join) 
cat("\nOuter Join:\n"); print(outer_join)

[11/10, 10:43 AM] Shubham: num <- as.integer(readline(prompt = "Enter a number: ")) 
cat("Multiplication Table of", num, "\n") 
for (i in 1:10) { 
cat(num, "x", i, "=", num * i, "\n") 
}
num1 <- as.numeric(readline(prompt = "Enter first number: ")) 
num2 <- as.numeric(readline(prompt = "Enter second number: ")) 
op <- readline(prompt = "Enter operation (+, -, *, /): ")
result <- switch(op, 
"+" = num1 + num2, 
"-" = num1 - num2, "*" = num1 * num2, 
"/" = ifelse(num2 != 0, num1 / num2, "Division by zero error"), 
"Invalid operation") 
cat("Result:", result, "\n")
data <- data.frame( 
ID = 1:5, 
Name = c("A", "B", "C", "D", "E"), 
Score = c(80, 75, 90, 85, 70) 
)

[11/10, 10:43 AM] Shubham: data("mtcars")
# ---- PIE CHART ----
cyl_data <- table(mtcars$cyl)
pie(cyl_data,
 labels = paste(names(cyl_data), "cyl"),
 main = "Pie Chart of Car Cylinders",
 col = c("lightblue", "lightgreen", "pink"))
# ---- BAR CHART ----
gear_data <- table(mtcars$gear)
barplot(gear_data,
 main = "Bar Chart of Cars by Gear Type",
 xlab = "Number of Gears",
 ylab = "Count of Cars",
 col = c("orange", "lightblue", "lightgreen"))

[11/10, 10:44 AM] Shubham: hist(mtcars$mpg,
 main = "Histogram of Miles per Gallon (mpg)",
 xlab = "Miles per Gallon",
 ylab = "Frequency",
 col = "lightblue",
 border = "black")

[11/10, 10:44 AM] Shubham: setClass(
 "Person",
 slots = list(
 name = "character",
 age = "numeric",
 gender = "character"
 )
)
p1 <- new("Person", name = "Virat", age = 36, gender = "M")
p2 <- new("Person", name = "Rohit", age = 38, gender = "M")
p1@name
p2@age
setGeneric(
 name = "greet",
 def = function(object) {
 standardGeneric("greet")
 }
)
setMethod(
 f = "greet",
 signature = "Person",
 definition = function(object) {
 cat("Hello,", object@name, "! You are", object@age, "years old and gender is", object@gender, "\n")
 }
)
greet(p1)
greet(p2)
[11/10, 10:45 AM] Shubham: mylist <- list(
 numbers = c(10, 20, 30, 40),
 letters = c("A", "B", "C"),
 matrix_data = matrix(1:9, nrow = 3)
)
len1 <- length(mylist[[1]])
len2 <- length(mylist[[2]])
cat("Length of first component:", len1, "\n")
cat("Length of second component:", len2, "\n")
mat <- matrix(1:12, nrow = 3, ncol = 4)
mat_list <- as.list(mat)