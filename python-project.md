# Python Analysis project

## Objective: Perform a full data analysis pipeline on a real dataset using Python—cleaning, transforming, analyzing, and drawing insights.

## Importing the dataset

1. Need to choose a dataset to analyse from kaggle. 
2. Use anaconda - jupyter notebook to carry out analysis on the dataset. 
3. Upload the downloaded dataset from your pc to the jupyter environment. 
4. In jupyter notebook - create new python file. 
5. Import pandas, numpy and the dataset file so can do analysis on it.

- `Import pandas as pd` - Loads the pandas library for data analysis.
- `Import numpy as py` - Loads the numpy library - used for numerical operations.
- `import seaborn as sns`
- `import matplotlib.pyplot as plt`
- `df = pd.read_csv(disney_princess_popularity_dataset_300_rows.csv")` - Reads a csv file and loads iot into a dataframe (df- 2D table of rows and columns). df is just the name of the variable to store the dataset. 
- `df.head()` - displays the first 5 rows of the DataFrame by default. 

![alt text](<Images/Screenshot 2025-04-29 112648.png>)


## Analysing the dataset - Data visualization

### Box office vs popularity score

- `sns.scatterplot(data=df, x='BoxOfficeMillions', y='PopularityScore', hue='IsIconic')` -  using seaborn's scatter plot function (used to plot individual data points in 2d), each plots vertical position reflects their popularity. The colour of the dot is based on whether or not the princess is marked as "iconic".
- `plt.title('Box Office vs Popularity Score')`- Adds a title to the chart.
- `plt.show ()` - displays the chart created. 

![alt text](<Images/Screenshot 2025-04-30 134916.png>)

### Top princesses by tiktok hashtag views - Data visualization

- `top_tiktok = df.sort_values(by='TikTokHashtagViewsMillions', ascending=False).head(10)` - sorts your entire dataset (df) the column of tiktokhashtagviewsmillions. It sorts from highest to lowest (most viewed at the top). Top 10 princesses only. 

- `sns.barplot(data=top_tiktok, x='TikTokHashtagViewsMillions', y='PrincessName')` - plots a horizontal bar chart using seaborn, uses the previously created DataFrame. 

- `plt.title('Top 10 Princesses by TikTok Views')` - Creates a title for the bar chart. 

- `plt.show()` - displays the bar chart. 

![alt text](<Images/Screenshot 2025-04-29 133854.png>)

### Songs vs popularity

```
sns.boxplot(data=df, x='HasAnySong', y='PopularityScore')
plt.title("Popularity by Song Presence")
plt.show()

```
- This creates a boxplot graph where x is songs and y is the popularity
- The title is popularity by song presence. 

![alt text](<Images/Screenshot 2025-04-30 143732.png>)


## Cleaning the dataset 

- Check for missing values - `df.isnull().sum()`
```
missing_values = df.isnull().sum()
print(missing_values[missing_values > 0])
```
  - This shows the values in the dataset that are empty. 
- Deleting duplicate values - 
```
print(f"Duplicates: {df.duplicated().sum()}")
df = df.drop_duplicates()
```
 
 - This shows the number of duplicate values and then deletes them. 


## Data manipulation

- Example: Create a new column for whether the character has any songs
`df['HasAnySong'] = np.where((df['HasSoloSong'] == 'Yes') | (df['HasDuet'] == 'Yes'), 'Yes', 'No')`
  - Checks if the column hassolosong has the value yes.
  - `|` - OR condition.
  - Also checks if the column hasDuet has yes.
  - So checks if either of these columns has a yes (the character has either solo or duet song) and then creates a new column called `HasAnySong` and if either values are yes then the new column will have a yes. If not, the new column will contain a no. 


