# ProblemSet3
Code for problem set 3 in Zoo6927


## Problem 1


## Problem 2

import pandas as pd 
#import pandas to use
url = 'https://raw.githubusercontent.com/sammyarroyo/Class_Files/master/data/CO-OPS__8729108__wl.csv'
#set the raw data url which I forked to my github from classfiles
df = pd.read_csv(url)
#creates the dataframe from my raw data file
df1 = pd.DataFrame(df, columns = ['Date Time', ' Water Level'])
#create a new dataframe to only contain the Date Time and Water Level columns
print(df1.head(10))
#printed the top 10 lines to check my codes worked

df1[' Water Level'].max()
df1.loc[df1[' Water Level'].idxmax()]
#searched for the maximum water level, and also searched for the max water level and printed the whole row it lies in. 

## Problem 3
df1 = df1.assign(difference=df1[' Water Level'].diff())
#created a new column with the differences in water level from the previous row (every 6 minutes) for every row
print(df1.head(10))
#printed to make sure my code worked

df1.loc[df1['difference'].idxmax()]
#same as before, searched for the maximum value in the new differences column and printed the whole row it lies on. 

## Problem 4
