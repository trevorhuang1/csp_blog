---
layout: post
toc: True
title: Pandas, Data Structures / Data Analysis
description: Data connections, trends, and correlation.  Pandas is introduced as it could be valuable for CPT and PBL.
courses: {'csp': {'week': 25}}
type: hacks
---

# Files To Get

Use wget in the **_notebooks** folder for this ipynb

wget https://raw.githubusercontent.com/nighthawkcoders/teacher_portfolio/main/_notebooks/2024-03-05-DS-python-pandas-df_science.ipynb

Use wget in a subfolder named **files** in your **_notebookx** folder on the following

wget https://raw.githubusercontent.com/nighthawkcoders/teacher_portfolio/main/_notebooks/files/data.csv

wget https://raw.githubusercontent.com/nighthawkcoders/teacher_portfolio/main/_notebooks/files/grade.json

Goto link and downlooad, then copy this png file and place into subfolder named **data_structures** in your **images** folder

https://github.com/nighthawkcoders/teacher_portfolio/blob/main/images/data_structures/pandas_dataframe.png


# Pandas and DataFrames
> In this lesson we will be exploring data analysis using Pandas.  

- College Board talks about ideas like 
    - Tools. "the ability to process data depends on users capabilities and their tools"
    - Combining Data.  "combine county data sets"
    - Status on Data"determining the artist with the greatest attendance during a particular month"
    - Data poses challenge. "the need to clean data", "incomplete data"


- [From Pandas Overview](https://pandas.pydata.org/docs/getting_started/index.html) -- When working with tabular data, such as data stored in spreadsheets or databases, pandas is the right tool for you. pandas will help you to explore, clean, and process your data. In pandas, a data table is called a DataFrame.

- DataFrame is a 2-dimensional labeled data structure with columns of potentially different types. It is similar to: 
    - a spreadsheet 
    - an SQL table
    - a JSON object with rows [] with nexted key-values {}

![DataFrame]({{site.baseurl}}/images/pandas_dataframe.png)


```python
# uncomment the following line to install the pandas library
# !pip install pandas 

'''Pandas is used to gather data sets through its DataFrames implementation'''
import pandas as pd
```

# Cleaning Data

When looking at a data set, check to see what data needs to be cleaned. Examples include:
- Missing Data Points
- Invalid Data
- Inaccurate Data

Run the following code to see what needs to be cleaned


```python
# Read the JSON file and convert it to a Pandas DataFrame 
# pd.read_json:  a method that reads a JSON and converts it to a DataFrame (df)
# df: a variable that holds the DataFrame
df = pd.read_json('files/grade.json')

# Print the DataFrame
print(df)

# Additional print statements to understand the DataFrame:
# print(df.info()) # prints a summary of the DataFrame, simmilar to database schema
# print(df.describe()) # prints statistics of the DataFrame
# print(df.head()) # prints the first 5 rows of the DataFrame
# print(df.tail()) # prints the last 5 rows of the DataFrame
# print(df.columns) # prints the columns of the DataFrame
# print(df.index) # prints the index of the DataFrame

# Questions:
# What part of the data set needs to be cleaned?
# From PBL learning, what is a good time to clean data?  
# Could you hav Garbage in, Garbage out problem if you don't clean the data?
```

       Student ID Year in School   GPA
    0         123             12  3.57
    1         246             10  4.00
    2         578             12  2.78
    3         469             11  3.45
    4         324         Junior  4.75
    5         313             20  3.33
    6         145             12  2.95
    7         167             10  3.90
    8         235      9th Grade  3.15
    9         nil              9  2.80
    10        469             11  3.45
    11        456             10  2.75


# Extracting Info

Take a look at some features that the Pandas library has that extracts info from the dataset

## DataFrame Extract Column


```python
#print the values in the points column with column header
print(df[['GPA']])

print()

#try two columns and remove the index from print statement
print(df[['Student ID','GPA']].to_string(index=False))
```

         GPA
    0   3.57
    1   4.00
    2   2.78
    3   3.45
    4   4.75
    5   3.33
    6   2.95
    7   3.90
    8   3.15
    9   2.80
    10  3.45
    11  2.75
    
    Student ID  GPA
           123 3.57
           246 4.00
           578 2.78
           469 3.45
           324 4.75
           313 3.33
           145 2.95
           167 3.90
           235 3.15
           nil 2.80
           469 3.45
           456 2.75


## DataFrame Sort


```python
#sort values
print(df.sort_values(by=['GPA']))

print()

#sort the values in reverse order
print(df.sort_values(by=['GPA'], ascending=False))
```

       Student ID Year in School   GPA
    11        456             10  2.75
    2         578             12  2.78
    9         nil              9  2.80
    6         145             12  2.95
    8         235      9th Grade  3.15
    5         313             20  3.33
    10        469             11  3.45
    3         469             11  3.45
    0         123             12  3.57
    7         167             10  3.90
    1         246             10  4.00
    4         324         Junior  4.75
    
       Student ID Year in School   GPA
    4         324         Junior  4.75
    1         246             10  4.00
    7         167             10  3.90
    0         123             12  3.57
    10        469             11  3.45
    3         469             11  3.45
    5         313             20  3.33
    8         235      9th Grade  3.15
    6         145             12  2.95
    9         nil              9  2.80
    2         578             12  2.78
    11        456             10  2.75


## DataFrame Selection or Filter


```python
#print only values with a specific criteria 
print(df[df.GPA > 3.00])
```

       Student ID Year in School   GPA
    0         123             12  3.57
    1         246             10  4.00
    3         469             11  3.45
    4         324         Junior  4.75
    5         313             20  3.33
    7         167             10  3.90
    8         235      9th Grade  3.15
    10        469             11  3.45


## DataFrame Selection Max and Min


```python
print(df[df.GPA == df.GPA.max()])
print()
print(df[df.GPA == df.GPA.min()])
```

      Student ID Year in School   GPA
    4        324         Junior  4.75
    
       Student ID Year in School   GPA
    11        456             10  2.75


# Create your own DataFrame

Using Pandas allows you to create your own DataFrame in Python.

## Python Dictionary to Pandas DataFrame


```python
import pandas as pd

#the data can be stored as a python dictionary
dict = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}
print("-------------Dictionary------------------")
print(dict)

#stores the data in a data frame
print("-------------Dict_to_DF------------------")
df = pd.DataFrame(dict)
print(df)

print("----------Dict_to_DF_labels--------------")
#or with the index argument, you can label rows.
df = pd.DataFrame(dict, index = ["day1", "day2", "day3"])
print(df)
```

    -------------Dictionary------------------
    {'calories': [420, 380, 390], 'duration': [50, 40, 45]}
    -------------Dict_to_DF------------------
       calories  duration
    0       420        50
    1       380        40
    2       390        45
    ----------Dict_to_DF_labels--------------
          calories  duration
    day1       420        50
    day2       380        40
    day3       390        45


## Examine DataFrame Rows


```python
print("-------Examine Selected Rows---------")
#use a list for multiple labels:
print(df.loc[["day1", "day3"]])

#refer to the row index:
print("--------Examine Single Row-----------")
print(df.loc["day1"])
```

    -------Examine Selected Rows---------
          calories  duration
    day1       420        50
    day3       390        45
    --------Examine Single Row-----------
    calories    420
    duration     50
    Name: day1, dtype: int64


## Pandas DataFrame Information


```python
#print info about the data set
print(df.info())
```

    <class 'pandas.core.frame.DataFrame'>
    Index: 3 entries, day1 to day3
    Data columns (total 2 columns):
     #   Column    Non-Null Count  Dtype
    ---  ------    --------------  -----
     0   calories  3 non-null      int64
     1   duration  3 non-null      int64
    dtypes: int64(2)
    memory usage: 180.0+ bytes
    None


# Example of larger data set

Pandas can read CSV and many other types of files, run the following code to see more features with a larger data set


```python
import pandas as pd

#read csv and sort 'Duration' largest to smallest
df = pd.read_csv('files/data.csv').sort_values(by=['Duration'], ascending=False)

print("--Duration Top 10---------")
print(df.head(10))

print("--Duration Bottom 10------")
print(df.tail(10))

```

    --Duration Top 10---------
         Duration  Pulse  Maxpulse  Calories
    69        300    108       143    1500.2
    79        270    100       131    1729.0
    60        210    108       160    1376.0
    109       210    137       184    1860.4
    65        180     90       130     800.4
    90        180    101       127     600.1
    106       180     90       120     800.3
    61        160    110       137    1034.4
    62        160    109       135     853.0
    70        150     97       129    1115.0
    --Duration Bottom 10------
         Duration  Pulse  Maxpulse  Calories
    100        20     95       112      77.7
    89         20     83       107      50.3
    58         20    153       172     226.4
    139        20    141       162     222.4
    95         20    151       168     229.4
    68         20    106       136     110.4
    135        20    136       156     189.0
    64         20    110       130     131.4
    93         15     80       100      50.5
    112        15    124       139     124.2


# APIs are a Source for Panda Data
> 3rd Party APIs are a great source for creating Pandas Data Frames.  
- Data can be fetched and resulting json can be placed into a Data Frame
- Observe output, this looks very similar to a Database


```python
import pandas as pd
import requests

def fetch():
    '''Obtain data from an endpoint'''
    url = "https://devops.nighthawkcodingsociety.com/api/users/"
    fetch = requests.get(url)
    json = fetch.json()

    # filter data for requirement
    df = pd.DataFrame(json)
 
    # Check if 'active_classes' column exists in the DataFrame
    if 'active_classes' in df.columns:
        # Split the 'active_classes' strings into lists of class names and expand the lists into separate rows
        classes_series = df['active_classes'].str.split(',').explode()

        # Count the unique class names and print the counts
        print(classes_series.str.strip().value_counts())
    else:
        print("Column 'active_classes' does not exist in the DataFrame")

fetch()
```

    active_classes
    APCSP    161
    APCSA     61
    CSSE      60
              20
    Name: count, dtype: int64



```python
import pandas as pd
import requests

def fetch():
    '''Obtain data from an endpoint'''
    url = "https://devops.nighthawkcodingsociety.com/api/users/"
    fetch = requests.get(url)
    json = fetch.json()

    # filter data for requirement
    df = pd.DataFrame(json)
    
    # Check if 'active_classes' column exists in the DataFrame
    if 'active_classes' in df.columns:
        # Split the 'active_classes' strings into lists of class names
        df['active_classes'] = df['active_classes'].str.split(',')

        # Get a list of unique class names by using a set comprehension
        unique_classes = pd.Series([unique_class.strip() for class_list in df['active_classes'] for unique_class in class_list]).unique()
                                    
        # Iterate over the each class name
        for current_class in unique_classes:
            # Filter the DataFrame for students in the current class using a lambda function
            class_df = df[df['active_classes'].apply(lambda classes: current_class in classes)]

            # Select the desired data frame column
            students = class_df[['active_classes','id', 'first_name', 'last_name']]

            # Print the list of students in the current class
            print(students.sort_values(by='last_name').head()) # avoids jupyter notebook truncation, remove .head() to print all students
            print()
    else:
        print("Column 'active_classes' does not exist in the DataFrame")

fetch()
```

        active_classes   id first_name last_name
    60         [APCSA]   86     Aditya          
    33         [APCSA]   55       Finn          
    30         [APCSA]   52    [Edwin]   Abraham
    248        [APCSA]  316   [Vishnu]   Aravind
    118        [APCSA]  161  [Anthony]  Bazhenov
    
        active_classes   id first_name last_name
    299        [APCSP]  369       Test          
    94         [APCSP]  134      Cindy          
    297        [APCSP]  367   testUser          
    12         [APCSP]   29     Saaras          
    151        [APCSP]  199      Gavin          
    
        active_classes   id           first_name last_name
    264             []  334                 Pele          
    255             []  325                 Pele          
    162             []  212              Varnika          
    194             []  246       [Alyssa-Allen]    Abrams
    259             []  329  [Alexander, Graham]      Bell
    
        active_classes   id first_name   last_name
    287         [CSSE]  357     Amelia            
    206         [CSSE]  260    Gabriel            
    266         [CSSE]  336     Yoseph            
    212         [CSSE]  267      Timur            
    91          [CSSE]  130   [Maryam]  Abdul-Aziz
    


# Hacks
> Early Seed award.  Don't tell anyone. Show to Teacher.
- Add this Blog to you own Blogging site.
- Have all lecture files saved to your files directory before Tech Talk starts. 
- Add this Blog to you own Blogging site.  In the Blog add notes and observations on each code cell.

> The next 6 weeks, the Teachers want you to improve your understanding of data structures and data science.  Your intention is to find some things to differentiate your individual College Board project, particularly if your project looks like all other projects.
- Look at this blog and others on data structures for todays date.  
- Create or Find your own dataset.  The suggestion is to use a JSON file, integrating with your CPT/PBL project would be ***Amazing***.
- Build frontend to backend to filter or use your data set in your CPT/PBL.
- When choosing a data set, think about the following...
    - Does it have a good sample size?
    - Is there bias in the data?
    - Does the data set need to be cleaned?
    - What is the purpose of the data set?
    - ...
