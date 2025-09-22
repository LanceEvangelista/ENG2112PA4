# ENG2112PA4

## Board Exam Problem

For this problem, we a given a CSV file with data on the results of a board exam, included in it are the names of each board taker,
their scores in Math, Electronics, GEAS, and Communication as well as their chosen track, gender, and their hometown. 

Firstly, to allow python to read the contents of the CSV file we create a variable to store its contents:

```python

df = pd.read_csv("board2.csv")

```

This tells Python to create a variable or dataframe `df` with contents from the csv file we provide it.

## Grouping and Indexing 

### By Track and Grade

In order to group the data based on the taker's hometown, we can use dataframe indexing, specifically by using boolean indexing.

To group by takers from "Instrumentation" track and have a grade in Electronics greater than 70:

```python

Intrsu = df[(df['Track'] == 'Instrumentation') & (df['Electronics'] > 70)] [['Name', 'GEAS', 'Electronics']]

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

to make indexing easier we first create a list of column that only have numeric values so that later on we can easily index them without having to list them one by one.

`numeric = ['Math','GEAS','Electronics','Communication']`

is a list of columns with the desired numeric values.

In order to filter for Female students from Mindanao with an average score of 55 or higher, we use Boolean indexing with multiple conditions.

`df[(df['Hometown'] == 'Mindanao')` to filter for rows with Mindanao in the Hometown Column

`(df['Gender'] == 'Female')` to filter for rows with Female in the Gender Column

`(df[numeric].mean(axis=1) >= 55)` Calculates the mean of each row using the list of columns we defined 'numeric' earlier. Then checks which is above or equal to 55


to them as CSV files:

```python
Mindy.to_csv("Mindy.csv")

Instru.to_csv("Instru.csv")
```

