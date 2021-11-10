# 📒 Data Visualization - Code Out

This notebook contains **11 tasks** centered around **data visualization** using **matplotlib**📊. 


For each visualization, instructions are provided describing what customizations must be applied to the visualization in order to pass the provided tests. 

Within the instructions, a saved image of the visualization is displayed. **Your goal is to create a visualization that mirrors the displayed image.**
> *Please note:* When developing data visualizations, there are frequently judgment calls that must be made about about a number of visual settings. The provided tests in this notebook will assess many of the matplotlib settings that were used to generate the displayed visualization, but not every setting is tested. **For this notebook, and any future assessments, you should be sure to meet the required instructions *exactly*.** Outside of those settings you are free to customize your visualizations however you feel is best.

This notebook requires you use `plt.subplots` and that you assign matplotlib figure and axis variables to specific variable names.

**For example:**

Given the following prompt:



>➡️**name the figure variable `plot_first_fig`**

>➡️ **name the axis variable `plot_first_ax`.**


The correct code would be as followed:

```python
plot_first_fig, plot_first_ax = plt.subplots()
```

## Task 1 - Import pandas using the standard alias.


```python
import pandas as pd
```

## Task 2 - Import the pyplot module from matplotlib using the standard `plt` alias.


```python
import matplotlib.pyplot as plt
```

## Task 3 - Load a csv file

A dataset called `friends_info.csv` containing information about the tv show [Friends](https://en.wikipedia.org/wiki/Friends) is saved inside the `data/` folder of this repository.

In the cell below:
- import the `friends_info` dataset using pandas
- save the resulting pandas dataframe to the variable `df`.


```python
df = pd.read_csv('data/friends_info.csv')
```

## Task 4 - Drop all rows that contain null values


```python
df.dropna(inplace=True)
```

## Task 5 - Using `plt.subplots` create a bar plot that visualizes the total number of episodes produced for each season. 

➡️ **name the figure variable `plot_one_fig`**

➡️ **name the axis variable `plot_one_ax`.**


This visualization should include the following customizations:
1. A figsize of (15, 6)
2. A title set to `'Episodes per Season'` with a fontsize of 30.
3. xtick labels with a fontsize of 20.
4. An xaxis label set to `'Season'` with a fontsize of 15.
5. A yaxis label set to `'Episode Count'` with a fontsize of 15.


**Below is an example of what your visualization should look like:**

![](static/episodes_per_season.png)


```python
season_counts = df.Season.value_counts()
x = season_counts.index.astype(str)
y = season_counts.values


plot_one_fig, plot_one_ax = plt.subplots(figsize=(15,6))
plot_one_ax.bar(x, y)
plot_one_ax.set_title('Episodes per Season', size=30)
plot_one_ax.set_xticklabels([tick for tick in x], size=20)
plot_one_ax.set_xlabel('Season', size=15)
plot_one_ax.set_ylabel('Episode Count', size=15)
plot_one_fig.savefig('static/episodes_per_season.png')
```

    /var/folders/js/czdv1g1d4877gnqnxm3b1y4m0000gn/T/ipykernel_30008/3056951045.py:9: UserWarning: FixedFormatter should only be used together with FixedLocator
      plot_one_ax.set_xticklabels([tick for tick in x], size=20)



    
![png](../README_files/README_10_1.png)
    


## Task 6 - Using `plt.subplots` visualize the number of episodes produced by the ten most frequent directors.

➡️ **name the figure variable `plot_two_fig`**

➡️ **name the axis variable `plot_two_ax`.**

This visualization should include the following customizations:

1. A title set to `'Top Ten Directors - Frequency'` with a fontsize of 35.
2. An xlabel set to `'Directors'` with a fontsize of 15.
3. A ylabel set to `'Number of films directed'` with a fontsize of 15.
4. For each xtick label, the spaces `' '` should replace with `'\n'`.

**Below is an example of what your visualization should look like:**

![](static/director_frequency.png)


```python
director_counts = df['Directed By'].value_counts()[:10]
x = director_counts.index
y = director_counts.values

plot_two_fig, plot_two_ax = plt.subplots(figsize=(20,6))
plot_two_ax.bar(x, y)
plot_two_ax.set_xticklabels([tick.replace(' ', '\n') for tick in x], size=20)
plot_two_ax.set_title('Top Ten Directors - Frequency', size=35)
plot_two_ax.set_xlabel('Directors', size=15)
plot_two_ax.set_ylabel('Number of films directed', size=15)
plot_two_fig.savefig('static/director_frequency.png')
plt.show()
```

    /var/folders/js/czdv1g1d4877gnqnxm3b1y4m0000gn/T/ipykernel_30008/3481402958.py:7: UserWarning: FixedFormatter should only be used together with FixedLocator
      plot_two_ax.set_xticklabels([tick.replace(' ', '\n') for tick in x], size=20)



    
![png](../README_files/README_12_1.png)
    


## Task 7 - Plot a histogram for the `Rating` column.

➡️ **name the figure variable `plot_three_fig`**

➡️ **name the axis variable `plot_three_ax`.**

This visualization should include the following customizations:
1. The figsize should be set to (10,5)
2. The title should be set to `'Episode Ratings - Distribution'`
3. The xlabel should be set to `'Rating'`
4. The ylabel should be set to `'Frequency'`
5. The color should be set to `'red'`
6. The alpha should be set to `.6`

Below is an example of what your visualization should look like:

![](static/ratings_distribution.png)


```python

# Isolate the data
x = df.Rating

# Create the fig, ax objects
plot_three_fig, plot_three_ax = plt.subplots(figsize=(10,5))

# Plot the data
plot_three_ax.hist(x, color='red', alpha = .6)

# title
plot_three_ax.set_title('Episode Ratings - Distribution')

# xlabel
plot_three_ax.set_xlabel('Rating')

# ylabel
plot_three_ax.set_ylabel('Frequency')

# Save the visualization
plt.savefig('static/ratings_distribution.png')
```


    
![png](../README_files/README_14_0.png)
    


## Task 8 - Visualize the average episode duration per year. 
> Because this is a time based visualization, a line plot is typically best.

➡️ **name the figure variable `plot_four_fig`**

➡️ **name the axis variable `plot_four_ax`.**

This visualization should include the following customizations:
1. The linewidth should be set to `5`.
2. The linestyle should be set to `--`.
3. The color should be set to `'green'`.
4. The title should be set to `'Average Duration - Per Year'`
5. The xlabel should be set to `'Year'`.
6. The ylabel should be set to `'Average Duration'`

**Hint:** You will need to use a groupby for this problem!

Below is an example of what your visualization should look like:

 
![](static/yearly_duration.png)


```python
plot_four_fig, plot_four_ax = plt.subplots(figsize=(15,4))

duration = df.groupby('Year').mean()['Duration']

x = duration.index
y = duration.values

plot_four_ax.plot(x, y, linewidth=5, linestyle='--', color='green')
plot_four_ax.grid()
plot_four_ax.set_title('Average Duration - Per Year', fontsize=20)
plot_four_ax.set_xlabel('Year', fontsize=15)
plot_four_ax.set_ylabel('Average Duration', fontsize=15)
plot_four_fig.savefig('static/yearly_duration.png')
```


    
![png](../README_files/README_16_0.png)
    


## Task 9 - Import Seaborn using the standard `sns` alias.


```python
import seaborn as sns
```

## Task 10 - Using seaborn's [`boxplot`](https://seaborn.pydata.org/generated/seaborn.boxplot.html), visualize the box plots for each season's Duration. 

➡️ **name the figure variable `plot_five_fig`**

➡️ **name the axis variable `plot_five_ax`.**

The visualization should have the following customizations:
1. A title set to `'Episode Duration - Grouped by Season'`
2. An xlabel set to `'Season'`
3. A ylabel set to `'Rating'`

Below is an example of what your visualization should look like:

![](static/season_duration_boxplot.png)


```python
plot_five_fig, plot_five_ax = plt.subplots(figsize=(15,6))

sns.boxplot(x="Season", y="Rating", data=df, ax=plot_five_ax)
plot_five_ax.set_title('Episode Duration - Grouped by Season', fontsize=20)
plot_five_ax.set_xlabel('Season', fontsize=15)
plot_five_ax.set_ylabel('Rating', fontsize=15)
plot_five_ax.set_xticklabels([tick for tick in range(1, 11)], size=20)
plot_five_fig.savefig('static/season_duration_boxplot.png')
```


    
![png](../README_files/README_20_0.png)
    


## Task 11 - Create a scatter plot

In the cell below, plot the relationship between U.S. Viewers and ratings.

➡️ **name the figure variable `plot_six_fig`**

➡️ **name the axis variable `plot_six_ax`.**

This visualization should have the following customizations:
1. A title set to `'U.S. Viewers vs Ratings'`
2. An xlabel set to `'U.S. Viewers'`
3. A ylabel set to `'Ratings'`

Below is an example of what your visualization should look like:

![](static/viewers_vs_ratings.png)


```python
x = df['U.S. Viewers']
y = df.Rating

plot_six_fig, plot_six_ax = plt.subplots(figsize=(10,4))

plot_six_ax.scatter(x, y)
plot_six_ax.set_title('U.S. Viewers vs Ratings', fontsize=20)
plot_six_ax.set_xlabel('U.S. Viewers', fontsize=15)
plot_six_ax.set_ylabel('Ratings', fontsize=15)
plot_six_fig.savefig('static/viewers_vs_ratings.png')
```


    
![png](../README_files/README_22_0.png)
    

