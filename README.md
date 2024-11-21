# Investigating-Netflix-Movies-Project




```
# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv("netflix_data.csv")
```
```

# Here I'm starting to get familiar with the dataset.
netflix_df.head(5) 

# Exploring the data further. Rows and Columns.
netflix_df.dtypes 

# Identify data patterns. Summarizing key statistics for numerical data in my DataFrame.
netflix_df.describe() 
```
```
# Subset the DataFrame for type "Movie"
netflix_subset = netflix_df [netflix_df['type'] =='Movie']

# Filter to keep only movies released in the 1990s
movies_1990s = netflix_subset[(netflix_df['release_year']>=1990) & (netflix_df['release_year']<2000)]
```
```
# Visualizing the duration column of my filtered data to see the distribution of movie durations
# Goal is to ee which bar is the highest and save/assign the duration value.

plt.hist(movies_1990s['duration'])
plt.title('Distribution of Movie Durations in the 1990s')
plt.xlabel('Duration (minutes)')
plt.xticks([25,50,75,100,125, 150, 175, 200],
           ['25 min','50 min','75 min','100 min','125 min','150 min','175 min','200 min'])
plt.ylabel('Number of Movies')
plt.show()

duration = 100
```
```
# Filter the data again to keep only the Action movies
action_movies_1990s = movies_1990s[movies_1990s['genre'] =='Action']
```
```
# Use a for loop and a counter to count how many short action movies there were in the 1990s
short_movie_count = 0

# Iterating over the labels and rows of the DataFrame to check if the duration is less than 90, if it is, add 1 to the counter, if it isn't, the counter should remain the same.

for lab, row in action_movies_1990s.iterrows():
    if row['duration']< 90:
        short_movie_count += 1
    else:
        short_movie_count = short_movie_count

print('The number of short action movies released in the 1990s is ' + str(short_movie_count) + ' in total.')
```
```

# A quicker way of counting values in a column is to use .sum() on the desired column
# (action_movies_1990s["duration"] < 90).sum()
