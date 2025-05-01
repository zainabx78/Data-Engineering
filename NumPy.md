# NumPy

Short for Numerical Python.


- 1 dimensional array = a list 
- E.g. [1,2,3,4,5]
  - **Must be the same data type.**
- 2 dimensional array = a list of lists.
  - Referred to as a matrix.
  - 0 axis = rows
  - 1 axis = columns
  - Forms co-ordinate system
  - Numbering starts with 0
- Arrays are more compactly stored than lists. Useful when working with large amounts of data. 

## Practical 

- `import numpy as np` - can call numpy with `np`.
- Structure for function to turn sequence into an array= `numpy.array(object, datatype, etc)`

```
import numpy as np
list1 = [1,2,3,4,5]
x = np.array(list1) # This just turns the sequence into an array. 

type (x) # shows datatype e.g. ndarray = one dimentional array

np.shape(x) # e.g. (5,1) - means there's 5 elements in each row but since it's a one dimentional array theres only 1 row.

x.shape #same as previous.

# Creating an array
np.array([2,2,2,2])

```

## Creating a 2-dimentional array

```
arr2d = np.array ([[1,1,1],[2,2,2],[3,3,3]]) 

```

- These nested lists form a row 
- Any nested list is a 2-dimentional list (matrix).
- Check the shape- `arr2d.shape`
- 2-dimentional - shape = (3,3) - x and y axis of lists.
- To add 2 lists together in an array: ` array2=np.array([list1,list2])`

## Datatypes in numPy

- E.g. for float numbers (decimals):
  - 100/3 in python is only precise to a specific point and then it's inaccurate. 
  - `np.longdouble(100)/np.longdouble(3)` - more accurate - higher degree of precision.

## Array Slicing and Indexing
- `array1[4:]` - Lists all the numbers after the 4th number (starts counting from 0).
- `array1[2:6]` - lists the numbers from the 3rd number to the 6th. 
- `array1[::-1]` - outputs the list in reverse. 
- In 2-dimentional arrays:
  - `array1[2,6]` - outputs the number at that coordinate. 

### Boolean array indexing- 

- `array1>3` - output shows true or false for each value in the list based on if its more than or less than 3. 
- `array1[array1>3]` - shows only the numbers that are more than 3 from the list. 
  - The output list is a 1 dimentional array. 

- `list1[:] = 10` - all the numbers in the array will change to 10. In a normal list this wont work. 

## Re-shaping

- `np.reshape(array1,(2,5))` 
- OR `array1.reshape(2,5)`
- This reshaping doesnt happen outside of this command - if you call array1, it will show the same previous shape.

## Flatten
- `np.ndarray.flatten(array1)` - changes a 2-dimentional array into a 1 dimentional array.
- `np.ravel(array1)` - does the same. 
- can also do `array1.ravel()` - same thing. 
  
 ## Concatenate
 - Joining the arrays together - on the 0 axis - adding on more rows 
 - `np.concatenate((array1,array2), axis=0)`
 - Arrays must have same sizes/rows or columns to be able to concatenate. 
 
 ## sort
 - `np.sort(array1,axis=1)` - sorts numbers is ascending order. 

## Array creation
- `np.full((2,5),2)`
- `np.full((5,5),fill_value=0,dtype=np.longdouble)`
- Creates an array with 5,5 shape and all 0's as values. 

## Arrange
- `np.arrange(0,12,2)` - creates an array with structure (start, stop, step).
- `np.arrange(0,12,2).reshape(2,3)` - creates a 2 dimentional array instead. 

## Linspace

- `np.linspace(0,100,num=25)` - `start,stop,num`
  - This means the array will contain 25 numbers from 0-100.
- `np.linspace(0,100,num=25).reshape(5,5)` - makes it a 2 dimentional array. 

## Random

- `np.random.rand(2,5)` - random values in the array.
- `np.random.randint(-20,20,(3,3))` - specifies the range of the random numbers and the shape of the array. 

## Array arithmetic and Mathematical functions

- `array1+array1` - output is both arrays added together (the values added together e.g. 2+2=4).
- Can also write this as `np.add(array1,array1)`
- Can only add arrays of the same shape because we add the numbers of the same position together. 
- However, if adding together a 1 dimentional array with an array with 3 rows, the 1d array row gets added to each of the rows of the other array as long as they have the same amount of columns. 
  - = **BROADCASTING**
  
- Can add/subtract/multiple/divide array values 
- `array1-5` - -5 from each value in the array. 
- `array1-array1`
- `np.subtract (array1,array1)`
- `array1*5`
- `array1-5`
- `numpy.sum(a,axis=none)`
  - e.g. `np.sum(array3)` = output of sum total of all values in the array. Can specify an axis. 
- `numpy.cumsum(array1,axis=1)` - values get cumulatively added. The first value gets added to the next, then the next etc. 
- `numpy.mean(a, axis=none)`
  - Or can write it as `array3.mean()`
- `numpy.amax(a,axis=none)`
- `numpy.amin(a,axis=none)`

## Functions
- File for the data has to be in the same folder as the jupyter notebook.
- `import numpy as py`
- `x = np.loadtxt('tfl-daily-cycle-hires.txt' delimiter=',', usecols=(1), skiprows=1)`
- Then run `x` - output should show a lot of values but some skipped since theyre so large.
- `np.count_nonzero(x)` - shows values that arent 0.
- `x.max()` - max number of bikes hired in a single day.
- `x.min()`
- `x.mean()`
- `x.std()` - standard deviation.

## Saving an array into a file

- `np.savetxt('textfile.txt,x)` - saves into same directory as the jupyter notebook. 

## Challenge:

1. Importing the NumPy Library = `import numpy as np`
2. Create a 5 row by 3 column array that contains only 7s = `np.full((5,3),7)`
3. Create a 3 row by 4 column array that contains evenly spaced values between 0-100 = `np.linspace(0,100,num=12).reshape(3,4)`
4. Transform the shape from question3 so the numbers increment down the columns rather than the rows = `np.linspace(0,100,num=12).reshape(3,4).transpose()`

REMEMBER: Index positioning starts at 0!!!