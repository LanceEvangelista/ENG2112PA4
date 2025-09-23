# ENG2112PA4

## Board Exam Problem

For this problem, we were given a CSV file with data on the results of a board exam, including the names of each board taker.
their scores in Math, Electronics, GEAS, and Communication as well as their chosen track, gender, and their hometown. 

Firstly, to allow python to read the contents of the CSV file we create a variable to store its contents by using `pd.read_csv("sample.csv")`

```python

df = pd.read_csv("board2.csv")

```

This tells Python to create a variable or dataframe `df` with contents from the CSV file we provide it.

## Grouping and Indexing 

To group the data, we will be using Pandas, as it can sort dataframes by their similar key values and can handle boolean indexing for scores.

```Python
import pandas as pd
```

### By Track and Grade

In order to group the data based on the taker's hometown, we can use dataframe indexing, specifically by using Boolean indexing,
to group by takers from the "Instrumentation" track and have a grade in Electronics greater than 70:

```python

Instru = df[(df['Track'] == 'Instrumentation') & (df['Electronics'] > 70)] [['Name', 'GEAS', 'Electronics']] #creates a dataframe named "Instru" to store the  test takers who are from "Instrumentation" and have an electronics score higher than 70

```

`df[(df['Track'] == 'Instrumentation')` ` tells Python to search for elements in 'df', specifically in rows where the 'Track' column is occupied with 
the track named: 'Instrumentation'.

`df['Electronics'] > 70)` tells the program, besides the previous condition, their Electronics grade also has to be more than 70. Both of these conditions must be satisfied 
for the program to add the entry into the new dataframe specifically for test takers from the instrumentation track with a grade higher than 70 in Electronics.

### By Hometown and Average

```python
numeric = ['Math','GEAS','Electronics','Communication']
Mindy = df[(df['Hometown'] == 'Mindanao') & 
           (df['Gender'] == 'Female') &
           (df[numeric].mean(axis=1) >= 55)] [['Name', 'Gender', 'Track', 'Math']]
Mindy
```

To make indexing easier, we first create a list of columns that only have numeric values, so that later on we can easily index them without having to list them one by one.

```python
numeric = ['Math','GEAS','Electronics','Communication'] #is a list of columns with the desired numeric values.
```

### Filtering

In order to filter for Female students from Mindanao with an average score of 55 or higher, we use Boolean indexing with multiple conditions.

`df[(df['Hometown'] == 'Mindanao')` to filter for rows with Mindanao in the Hometown Column

`(df['Gender'] == 'Female')` to filter for rows with Female in the Gender Column

`(df[numeric].mean(axis=1) >= 55)` Calculates the mean of each row using the list of columns we defined 'numeric' earlier. Then checks which is above or equal to 55


### to them as CSV files:

```python
Mindy.to_csv("Mindy.csv") #Saves dataframe Mindy as "Mindy.csv"

Instru.to_csv("Instru.csv") #Saves dataframe Instru as "Instru.csv"
```

## Data Visualization

First, we import the Matplotlib Library to handle the visualization of the data from the previous steps:

```Python
import matplotlib.pyplot as plt
```

First, we group the data together based on their values by gender, by hometown, and by track chosen using `groupby`, and take their mean to easily compare later on

```Python
avg_gender = df.groupby('Gender')[numeric].mean()
avg_hometown = df.groupby('Hometown')[numeric].mean()
avg_track = df.groupby('Track')[numeric].mean()
```

First, the program groups the data `df.groupby("Parameter")` then takes the mean of the numerical data within the group using `.mean()`

### Creating Plots and Graphs
To create a plot, we first use:

`plt.figure(figsize=(x,y))`

Each time this syntax is called, a new plot is created, which allows the program to handle multiple plots.

`plt.bar(xaxis, yaxis)`

This tells the program to create a bar graph with the specific variables' data as the x or y axes

### To graph by Hometown:

```Python
plt.figure(figsize=(8, 5))
plt.bar(avg_hometown.index, avg_hometown.mean(axis=1))
```
Using `avg_gender.mean(axis=1)` takes the averages of the 4 subjects, using `axis=1` specifying the mean of the row should be taken, and turns them into 1 overall average.

### To graph by Gender:

```Python
plt.figure(figsize=(8, 5))
plt.bar(avg_gender.index, avg_gender.mean(axis=1))
```
### To graph by Track:

```Python
plt.figure(figsize=(8, 5))
plt.bar(avg_track.index, avg_track.mean(axis=1))
```

V2
