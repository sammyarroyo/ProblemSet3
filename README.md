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

## Problems 2, 3 and 4 found in the Jupyter Notebook CodeBlock uploaded to this repo. 
