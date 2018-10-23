# ProblemSet3
Code for problem set 3 in Zoo6927


## Problem 1 
#!/usr/bin/env python3
import io, re
import numpy

#Defining new empty files to put data into
waterlev = []
datetime = []

#Open the file for reading, skip first line of headers
rf = open('/ufrc/zoo6927/share/Class_Files/data/CO-OPS__8729108__wl.csv', 'r')
next(rf)

#Read the file line by line, strip lines, create array from comma delimited
#data, define The first and second columns as where date and time and
#water level are kept.
for line in rf:
        line = line.strip()
        commalist = numpy.array(line.split(','))
        water_level =  (commalist[1])
        date_time = (commalist[0])
        try:
            waterlev.append(float(water_level))
            datetime.append(date_time)
        except:
               	pass
#Find the max in the water level column
        max_water_level = max(waterlev)

#Find the row associated with the max water level and print the max water level
#along with the date and time found in the same row!
#This outputs our answer.
index_of_interest = (int(waterlev.index(max(waterlev))))
print(max_water_level)
print(datetime[index_of_interest])

## Problem 2
#!/usr/bin/env python3
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

print(df1.loc[df1[' Water Level'].idxmax()])
#searched for the maximum water level, and also searched for the max water level and printed the whole row it lies in. 

## Problem 3
#!/usr/bin/env python3
df1 = df1.assign(difference=df1[' Water Level'].diff())
#created a new column with the differences in water level from the previous row (every 6 minutes) for every row
print(df1.head(10))
#printed to make sure my code worked

print(df1.loc[df1['difference'].idxmax()])
#same as before, searched for the maximum value in the new differences column and printed the whole row it lies on. 

## Problem 4
#!/usr/bin/env python3
%matplotlib inline
import matplotlib.pyplot as plt
plt.style.use('seaborn-whitegrid')
import numpy as np
#import packages I'll need to plot a graph

df1.plot.line(x='Date Time', y=' Water Level')
#plot a line graph from the dataframe, and set 'Date Time column as the x values 
#set ' Water Level' column as the y values
#I cannot figure out a way to label the x axis with anything...
