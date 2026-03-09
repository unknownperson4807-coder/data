
 
Practical 1 


Aim: Perform the analysis for the following. 
A.	Import the data warehouse data in MS-EXCEL & create the Pivot Table and Pivot chart.  
B.	Import the cube in MS-EXCEL and create the pivot table and pivot chart.  


STEPS :- 
Step 1: Open Microsoft excel 2007. 
  
      Step 2: Enter the values into the table which you are creating. 
 
Step 3: Select all the table and go to the insert option and create the pivot table or chart both. 
   
Step 4: Select the table cell which you want to create the pivot table. 
 
Step 5: After the pivot table is done click on the pivot chart and select the different kind of graph you want. 


  
  
Practical 2 
Aim:Apply the what – if Analysis for data visualization. Design and generate necessary reports based on the data warehouse data. Use Excel. 


STEPS:- A book store and have 100 books in storage. You sell a certain % for the highest price of $50 and a certain % for the lower price of $20. 
  
If you sell 60% for the highest price, cell D10 calculates a total profit of 60 * 50 + 40 * 20 = 3800.  
Create Different Scenarios But what if you sell 70% for the highest price? And what if you sell 80% for the highest price? Or 90%, or even 100%? Each different percentage is a different scenario. You can use the Scenario Manager to create these scenarios.  
Note: To type different percentage into cell C4 to see the corresponding result of a scenario in cell D10 we use what if analysis. What-if analysis enables you to easily compare the results of differentscenarios. 



Step 1: In Excel, On the Data tab, in the Data tools group, click What-If Analysis
 
Step 2: Click on What –if-Analysis and selectscenario manager. 
  
The Scenario Manager Dialog box appears. 
Step 3: Add a scenario by clicking on Add. 
 
Step 4: Type a name (60percent), select cell F10 (% sold for the highest price) for the Changing cells and click on OK. Click on icon which is circled.
  
Select F10 cell.
 
Click back on the icon again and then click OK 
  
Step 5: Enter the corresponding value 0.6 and click on OK again. 
 
Step 6: To apply scenarios click on Show 
  
Step 7: Next, add 4 other scenarios (70%, 80%, 90% and 100%) Finally, your Scenario Manager should be consistent with the picture below: 
  
 
 
 

Practical 3 


Aim: Implementation of Classification algorithm in R Programming. 


Code:
rainfall<-c(799,1174.8,865.1,1334.6,635.4,918.5,685.5,998.6,784.2,985,882.8,1071)
rainfall.timeseries <- ts(rainfall,start = c(2012,1),frequency= 12)
print(rainfall.timeseries) 
png(file = "rainfall.png")
plot(rainfall.timeseries)
dev.off() Output: 
 

 
Practical 4 


Aim: Perform the data clustering using clustering algorithm (clusterning:K-means algorithm). 


Code: 
newiris <- iris  
newiris$Species <- NULL  
(kc <- kmeans(newiris,3)) 
  
table(iris$Species,kc$cluster) 
  
plot(newiris[c("Sepal.Length","Sepal.Width")],col=kc$cluster)   points(kc$centers[,c("Sepal.Length","Sepal.Width")],col=1:3,pch=8,cex=2)  
dev.off() 
 



 
Practical 5 


Aim: Perform the Linear regression on the given data warehouse data using R/Python. 


Code: 
x <- c(151, 174, 138, 186, 128, 136, 179, 163, 152, 131) y <- c(63, 81, 56, 91, 47, 57, 76, 72, 62, 48) relation <- lm(y~x)  
print(relation) 
  
a <- data.frame(x = 170)  result <- predict(relation,a)  
print(result) 
png(file = "linearregression.png") 
plot(y,x,col = "blue",main = "Height & Weight Regression", abline(lm(x~y)),cex = 1.3,pch 
= 16,xlab = "Weight in Kg",ylab = "Height in cm") dev.off() 

 
  
 

Practical 6 


Aim: Perform the logistic regression on the given data warehouse data using R/Python. 


Code: quality <-read.csv(‘C:/Users/Vishwakarma vinay/Downloads/quality.csv’) table(quality$PoorCare) install.packages("caTools") library(caTools) Warning message: package ‘caTools’ was built under R version 3.5.2  set.seed(88)  split = sample.split(quality$PoorCare, SplitRatio = 0.75)  
split 
  
qualityTrain = subset(quality, split == TRUE) qualityTest = subset(quality, split == FALSE) > nrow(qualityTrain) 
QualityLog = glm(PoorCare ~ OfficeVisits + Narcotics,data=qualityTrain, family=binomial) summary(QualityLog) predictTrain = predict(QualityLog, type="response") 
ROCRpred = prediction(predictTrain, qualityTrain$PoorCare)  ROCRperf = performance(ROCRpred, "tpr", "fpr")   plot(ROCRperf)  
 
plot(ROCRperf, colorize=TRUE)  
plot(ROCRperf, colorize=TRUE, print.cutoffs.at=seq(0,1,by=0.1), text.adj=c(-0.2,1.7)) 
 
 
 
 
  
Practical 7 


Aim: Write a Python program to read data from a CSV file, perform simple data analysis, and generate basic insights. (Use Pandas is a Python library). 


STEPS: 
Step 1:- Install Required Library  
Before running the program, you need to install Pandas.  
Open a command prompt or terminal and type: pip install pandas 
Step 2:- Open MS EXCEL Prepare a CSV File 
Step 3:- Open PYTHON IDLE Write the Python Code : 
import pandas as pd  file_path = "Book1.csv df = pd.read_csv(file_path)  print("\nz’‘ First 5 rows of the dataset:")  print(df.head()) # Show the first 5 rows  print("\n‘’zDataset Summary:") print(df.info())  print("\n‘’z Basic Statistics:") print(df.describe())  print("\n’‘zMissing Valuesin Each Column:")  print(df.isnull().sum()) print("\n‘’z Column Names:")  print(df.columns) if 'Salary' in df.columns:  
print(f"\n’z‘ Average Salary: {df['Salary'].mean():.2f}")  if 'Age' in df.columns: print(f"\n‘’z Youngest Person's Age: {df['Age'].min()}")  print(f"‘’z Oldest Person's Age: {df['Age'].max()}")  if 'Gender' in df.columns:  
print("\n‘’z Gender Distribution:")  print(df['Gender'].value_counts())  print ( "\n  Data Analysis Completed Successfully!")

  
 
 

 
 
Practical 8(A) 


Aim: Perform data visualization using Python on any sales data. 


Code: import pandas as pd import matplotlib.pyplot as plt data=pd.read_csv(“C:/Users/Vishwakarma vinay/Downloads/quality.csv”) print(data.head(10)) plt.plot(data[‘InpatientDays’]) plt.plot(data[‘PoorCare’]) plt.title(“scatter Plot”) plt.xlabel(“Inpatient Days”) plt.ylabel(“Poor Care”) 
plt.show() 
  
 
 
 
 
 
Practical 8(B) 


Aim: Perform data visualization using PowerBI on any sales data. 


Steps: 
1.	Open Power BI. 
  
2.	Take Blank Report template. 
  
3.	Download "products.xlsx" file from google chrome. 
(Note: Take any sales data( in excel file) ) 
  
Step 4: Go to home -> excel workbook -> select the excel file from download. 
  
  
5.	Your data will be enable in "Power Query Editor" window. 
  
6.	Go to again Power BI desktop window -> click on apply changes button. 
  
7.	Below the file menu -> click on report view -> right side of the window you will see visualization. 
  
8.	Take any graph you want or map -> beside the visualization you will see the data click on products and select the column what all you want to visualization -> you will see your visualization graph of your given data. 
  
Step 9: Take any graph you want to see the visualized data -> after the visualization step you will see the near data option click on it and select the column you want to add in your graph. 
  
Pie chart :
  
Stacked column chart: 
  
 
 
 
 
 
 
 
 
