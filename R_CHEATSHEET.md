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

###### Create a dataframe and fill it 

        mydata = data.frame(State = ifelse(sign(rnorm(25))==-1,'Delhi','Goa'), Q1= sample(1:25))

###### Substitue values in columns 
In this example, we are replacing 1 with 6 in Q1 variable

    mydata$Q1[mydata$Q1==1] <- 6 

In this example, we are replacing "Delhi" with "Mumbai" in State variable. We need to convert the variable from factor to character.

    mydata$State = as.character(mydata$State)
    mydata$State[mydata$State=='Delhi'] <- 'Mumbai'

In this example, we are replacing 2 and 3 with NA values in whole dataset.

    mydata[mydata == 2 | mydata == 3] <- NA

Another method

You have to first install the car package.

* Install the car package
    
        install.packages("car")
        library("car")

###### Recode 1 to 6
    
        mydata$Q1 <- recode(mydata$Q1, "1=6")

###### Recoding a given range

Recoding 1 through 4 to 0 and 5 and 6 to 1

    mydata$Q1 <- recode(mydata$Q1, "1:4=0; 5:6=1")


You don't need to specify lowest and highest value of a range.

    The lo keyword tells recode to start the range at the lowest value.
    The hi keyword tells recode to end the range at the highest value.

    # Recoding lowest value through 4 to 0 and 5 to highest value to 1
    mydata$Q1 <- recode(mydata$Q1, "lo:4=0; 5:hi=1")


You can specify else condition in the recode statement. It means how to treat remaining values that was not already recoded.

    # Recoding lowest value through 4 to 0, 5 and 6 to 1, remaining values to 3,
    mydata$Q1 <- recode(mydata$Q1, "lo:4=0; 5:6=1;else = 3")


