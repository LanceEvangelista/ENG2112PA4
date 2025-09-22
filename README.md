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

### By hometown

In order to group the data based on the taker's hometown we can use dataframe indexing
