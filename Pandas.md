# Pandas
- Works with tabular data. 
- series - index column and data column.
- dataframes - like a table in sql.
## Series

- `import pandas as pd`
- create 2 lists of the same length:
```
index_list = [0,1,2,3,4,5]
data_list = [100,200,300,400,500,600]
series_1 = pd.series(data=data_list,index=index_list)
```

- When run `series_1` - output should show a list of the combined arrays. 
- If you want to access specific values, pass the index value: 
  - `index_list['2']`
- Can access multiple data too:
  - `index_list['1','2']`
- To add a data type in the series:
  - `series_1 = pd.series(data=data_list,index=index_list,dtype='float')`
    - Makes it so the numbers are in decimals - `.0`.
  - To make datatype longdouble (more accurate decimals) - pass in character code `g`. 

### Using one array for a series

- `dict_1={'key1':'value1','key2':'value2','key3':'value3'}`
- `pd.series (data=dict_1,index=dict_1)`
- Output shows the keys as index and the values as data. 

## DataFrames

- Collections of series
- Data in a tabular form 
- Same as series but has additional column name too. 
```
import pandas as pd
column_labels = ['A','B','C']
data = [[1,2,5],[4,2,4],[6,7,9],[3,2,4],[3,3,2]]
df = pd.DataFrame(index=row_labels, data=data, columns=column_labels)
type (df)
df

```
- When running `df` - should see a table with x and y axis labels and then the data in the middle. 
- When you want any changes to be saved, have to specify `inplace=True`.
- `df.set_index('C',drop=False,inplace=True)` - changes index to the C column and then applies changes. 

## read_csv

- `countries_table = pd.read_csv(filepath_or_buffer='top_10_countries.csv')`
- To show table - `countries_csv`
- Need to put in full file path if the file isnt in same folder as jupyter notebook file. 
- Find out type of data - `type (countries_table)`
  - Should output DataFrame
- Column names are automatically generated when    `header = none`. 

### Specific data querying

- `countries_data ['Region']`
- `type(countries_data ['Region'])`
- Selecting multiple columns- `countries_data [['Region`,`Country`]]`
- `countries_data.iloc[3]` - returns index position 3. 
- `countries_data.iloc[3:]` - returns everything from index position 3 and below. 
- `countries_data.iloc[::-1]` - returns everything reversed. 
- `countries_data.iloc[2,3]` - specific data at this location. (remember it starts with 0- co-ordinates). 
- `countries_data.iloc[2:,1:4]` - stop is inclusive - have to stop at 1 position higher than what you need. 
- `countries_data[countries_data=='Asia']` - returns the table with NaN (not any number) or Asia. 
- `countries_data=='Asia` - returns table with true or false values. 
- `countries_data.head()` - first half of the rows. 
- `countries_data.tail()` - last 5 rows. 

## Selecting data
- `DataFrame.isin([list of values])`
- `countries_data[countries_data['Region'].isin(['Asia,'Americas']))` - Shows all rows with asia or america region. 
- `~` reverses the condition - `countries_data[~countries_data['Region'].isin(['Asia,'Americas']))` - shows all with regions that are not americas or asia. 

## Data manipulation
- `countries_df.shape` - shows shape of the series/dataframe.
- `countries_df.columns` - shows column names. 
- Renaming column names - `DataFrame.rename(columns=('Country / Dependency' : 'Country'), inplace=True)`

### DataFrame.drop

- `countries_df.drop(labels='Date',axis=1,inplace=True)`
- Drops the columns. 

### Arithmetic

- `round(countries_df['Population']/1000000,2)` - divides it by 1000000 and rounds it to 2 decimals. 
- Assigning those values into the table in a column called millions:
  - `countries_df['Population (millions)']= round(countries_df['Population']/1000000,2)`

### Concatenating the country and region columns together

- `countries_df['Country / Region'] = countries_df['Country']+ ' / ' + countries_df['Region']` 

### Removing percentages:
- `'17.80%' [:-1]` - output should be 17.80.
```
def remove_pct(x):
  return x[:-1]

```

- This function takes an argument and converts it to return a slice without the last character (the %).
- Use `apply` method to execute the function on all values in the table:
  - `countries_df['& of world'].apply(remove_pct)`
  - Output should show all values without percentage. 
- Use lambda function instead - 
  - `countries_df['% of world'].apply(lambda x: x[:-1])`
- Inputting this in table so it doesnt show % at the end of each value - 
- `countries_df['% of world'] = countries_df['% of world'].apply(lambda x: x[:-1]) `
- Now when `countries_df` dataframe is run, it should show value without %.
- Change the datatype to float - `countries_df['% of world'] = countries_df['% of world'].astype(float)`
- Making a new column with calculation:
`countries_df['World Pop'] = countries_df['Population']/(countries_df['% of world']/100)`


### Deleting columns
- drop method. 
  - e.g. `tfl_df.drop(columns='unnamed:2', inplace =True)`
### Changing datatypes
- astype function
- `tfl_df['Day']=tfl_df['Day'].astype('datetime64')`

### Sorting Values

- `tfl_df.sort_values(by='Number of bicycle hires', ascending=False,inplace=True)`

```
import datetime as dt
tfl_df['Day'].dt.strftime('%m-%y')
```
- Shows just some of the date.

`tfl_df['Month / Year'] = tfl_df['Day'].dt.strftime('%b-%y)`
- Adds the month and year in a separate column. 

### Transpose - switches columns and rows

- `tfl_df.transpose()`

### Describe 
- `countries_df.describe()`

## Joining dataFrames

- Inner join - returns only matching records joined together.  
- Left join - all rows from left table are returned even if not matching to right table. From right table, only the table matching in the left will be retuned. 
- Right join - all rows from right table and only matching ones from left. 
- Outer join - returns all rows whether they match or not. 
- If a table contains duplicate rows, the table would return both of them. 

#######
emp and dept are 2 different tables. 
- `emp.join(dept.set_index('id'), on='dept_id')`
- `(other (other dataframe- join key must be an index), on(key to join on), how(inner, outer, left, right etc default=left))`

## Windowing operations

- 