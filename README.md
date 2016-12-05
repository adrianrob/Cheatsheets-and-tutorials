# DATA EXPLORATION

###### basic stats
    mydata  = fread("data.csv")
      summary(mydata)
###### column names

      names(mydata)

###### number of row and col

      nrow(mydata)
      ncol(mydata)

###### desc of the dataset types etc

      str(mydata)

###### Number of missing values in each column

      colSum(is.name(mydata))

###### Number of missing values in one column

      sum(is.na(mydata$myColumn))

# DATA MANIPULATION

## Replacing / Recoding values

By 'recoding', it means replacing existing value(s) with the new value(s).

###### Create Dummy Data

    mydata = data.frame(State = ifelse(sign(rnorm(25))==-1,'Delhi','Goa'), Q1= sample(1:25))

In this example, we are replacing 1 with 6 in Q1 variable

    mydata$Q1[mydata$Q1==1] <- 6

In this example, we are replacing "Delhi" with "Mumbai" in State variable. We need to convert the variable from factor to character.

    mydata$State = as.character(mydata$State)
    mydata$State[mydata$State=='Delhi'] <- 'Mumbai'

In this example, we are replacing 2 and 3 with NA values in whole dataset.

    mydata[mydata == 2 | mydata == 3] <- NA


2. Recoding to a new column

    # Create a new column called Ques1
    mydata$Ques1<- recode(mydata$Q1, "1:4=0; 5:6=1")

Note : Make sure you have installed and loaded "car" package before running the above syntax.

How to use IF ELSE Statement

Sample Data

    samples = data.frame(x =c(rep(1:10)), y=letters[1:10])

If a value of variable x is greater than 6, create a new variable called t1 and write 2 against the corresponding values else make it 1.

    samples$t1 = ifelse(samples$x>6,2,1)

How to use AND Condition

    samples$t3 = ifelse(samples$x>1 & samples$y=="b" ,2,1)

How to use NESTED IF ELSE Statement

    samples$t4 = ifelse(samples$x>=1 & samples$x<=4,1,ifelse(samples$x>=5 & samples$x<=7,2,3))


3. Renaming variables

To rename variables, you have to first install the dplyr package.

*** Install the plyr package
install.packages("dplyr")

*** Load the plyr package
library(dplyr)

*** Rename Q1 variable to var1
mydata <- rename(mydata, var1 = Q1)


4. Keeping and Dropping Variables

In this example, we keep only first two variables .

    mydata1 <- mydata[1:2]

In this example, we keep first and third through sixth variables .

    mydata1 <- mydata[c(1,3:6)]

In this example, we select variables using their names such as v1, v2, v3.

newdata <- mydata[c("v1", "v2", "v3")]


Deleting a particular column (Fifth column)

    mydata [-5]

Dropping Q3 variable

    mydata$Q3 <- NULL


Deleting multiple columns

    mydata [-(3:4) ]

Dropping multiple variables by their names

    df = subset(mydata, select = -c(x,z) )



5. Subset data (Selecting Observations)

By 'subsetting' data, it implies filtering rows (observations).

Create Sample Data

    mydata = data.frame(Name = ifelse(sign(rnorm(25))==-1,'ABC','DEF'), age = sample(1:25))

Selecting first 10 observations

    newdata <- mydata[1:10,]

Selecting values wherein age is equal to 3

    mydata<-subset(mydata, age==3)

Copy data into a new data frame called 'newdata'

    newdata<-subset(mydata, age==3)

Conditional Statement (AND) while selecting observations

    newdata<-subset(mydata, Name=="ABC" & age==3)

Conditional Statement (OR) while selecting observations

    newdata<-subset(mydata, Name=="ABC" | age==3)

Greater than or less than expression

    newdata<-subset(mydata, age>=3)

Keeping only missing records

    newdata<-subset(mydata, is.na(age))

Keeping only non-missing records

    newdata<-subset(mydata, !is.na(age))


6. Sorting

Sorting is one of the most common data manipulation task. It is generally used when we want to see the top 5 highest / lowest values of a variable.

Sorting a vector

    x= sample(1:50)
    x = sort(x, decreasing = TRUE)

The function sort() is used for sorting a 1 dimensional vector. It cannot be used for more than 1 dimensional vector.
Sorting a data frame

    mydata = data.frame(Gender = ifelse(sign(rnorm(25))==-1,'F','M'), SAT= sample(1:25))

Sort gender variable in ascending order

    mydata.sorted <- mydata[order(mydata$Gender),]

Sort gender variable in ascending order and then SAT in descending order

    mydata.sorted1 <- mydata[order(mydata$Gender, -mydata$SAT),]

Note : "-" sign before mydata$SAT tells R to sort SAT variable in descending order.


7. Value labeling

Use factor() for nominal data

    mydata$Gender <- factor(mydata$Gender, levels = c(1,2), labels = c("male", "female"))

Use ordered() for ordinal data

    mydata$var2 <- ordered(mydata$var2, levels = c(1,2,3,4), labels = c("Strongly agree", "Somewhat agree", "Somewhat disagree", "Strongly disagree"))


8. Dealing with missing data

Number of missing values in a variable

    colSums(is.na(mydata))

Number of missing values in a row

    rowSums(is.na(mydata))

List rows of data that have missing values

    mydata[!complete.cases(mydata),]

Creating a new dataset without missing data

    mydata1 <- na.omit(mydata)

Convert a value to missing

    mydata[mydata$Q1==999,"Q1"] <- NA


9. Aggregate by groups

The following code calculates mean for variable "x" by grouped variable "y".

    samples = data.frame(x =c(rep(1:10)), y=round((rnorm(10))))
    mydata <- aggregate(x~y, samples, mean, na.rm = TRUE)


10. Frequency for a vector

To calculate frequency for State vector, you can use table() function.



11. Merging (Matching)

It merges only common cases to both datasets.

    mydata <- merge(mydata1, mydata2, by=c("ID"))

Detailed Tutorial : Joining and Merging


12. Removing Duplicates

    data = read.table(text="
    X Y Z
    6 5 0
    6 5 0
    6 1 5
    8 5 3
    1 NA 1
    8 7 2
    2 0 2", header=TRUE)


In the example below, we are removing duplicates in a whole data set. [Equivalent to NODUP in SAS]

    mydata1 <- unique(data)

In the example below, we are removing duplicates by "Y" column. [Equivalent to NODUPKEY in SAS]

    mydata2 <- subset(data, !duplicated(data[,"Y"]))


13. Combining Columns and Rows

If the columns of two matrices have the same number of rows, they can be combined into a larger matrix using cbind function. In the example below, A and B are matrices.

    newdata<- cbind(A, B)

Similarly, we can combine the rows of two matrices if they have the same number of columns with the rbind function. In the example below, A and B are matrices.

    newdata<- rbind(A, B)


14. Combining Rows when different set of columns

The function rbind() does not work when the column names do not match in the two datasets. For example, dataframe1 has 3 column A B and C . dataframe2 also has 3 columns A D E. The function rbind() throws an error. The function smartbind() from gtools would combine column A and returns NAs where column names do not match.

    install.packages("gtools") #If not installed
    library(gtools)
    mydata <- smartbind(mydata1, mydata2)
