# Working with Categorical Data in Python

## Introduction to Categorical Plots using Seaborn
- Dataset: Las Vegas TripAdvisor Reviews - reviews
  - Rows: 504
  - Columns: 20
  - [Link to Dataset](https://www.kaggle.com/crawford/las-vegas-tripadvisor-reviews)

## Seaborn
- Introduction to Data Visualization with Seaborn
- Intermediate Data Visualization with Seaborn

## Categorical Plots
```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.catplot(x="variable_name", y="variable_name", data=dataframe, kind="plot_type")
plt.show()
```

### The `catplot` Function
Parameters:
- `x`: Name of variable in data
- `y`: Name of variable in data
- `data`: DataFrame
- `kind`: Type of plot to create - options: "strip", "swarm", "box", "violin", "boxen", "point", "bar", or "count"

## Box Plot
- Box Plot wiki page

## Review Score
```python
reviews["Score"].value_counts()
```
- 5: 227
- 4: 164
- 3: 72
- 2: 30
- 1: 11

## Box Plot Example
```python
sns.catplot(x="Pool", y="Score", data=reviews, kind="box")
plt.show()
```

## Two Quick Options
```python
sns.set(font_scale=1.4)
sns.set_style("whitegrid")
sns.catplot(x="Pool", y="Score", data=reviews, kind="box")
plt.show()
```

## Seaborn Bar Plots
### Traditional Bar Chart
```python
reviews["Traveler type"].value_counts().plot.bar()
```

### The Syntax
```python
sns.set(font_scale=1.3)
sns.set_style("darkgrid")
sns.catplot(x="Traveler type", y="Score", data=reviews, kind="bar")
```

## Ordering Your Categories
```python
reviews["Traveler type"] = reviews["Traveler type"].astype("category")
reviews["Traveler type"].cat.categories
```
- 'Business', 'Couples', 'Families', 'Friends', 'Solo'

## Updated Visualization
```python
sns.catplot(x="Traveler type", y="Score", data=reviews, kind="bar")
```
Note: `catplot()` has an `order` parameter.

## The `hue` Parameter
- `hue`: Name of a variable in data used to split the data by a second category and also used to color the graphic
```python
sns.set(font_scale=1.2)
sns.set_style("darkgrid")
sns.catplot(x="Traveler type", y="Score", data=reviews, kind="bar", hue="Tennis court")
```

## Bar Plot Across Two Variables

## Point and Count Plots
### Point Plot Example
```python
sns.catplot(x="Pool", y="Score", data=reviews, kind="point")
```

## Bar Plot vs. Point Plot
- Bar Plot
- Point Plot

## Point Plot with Hue
```python
sns.catplot(x="Spa", y="Score", data=reviews, kind="point", hue="Tennis court", dodge=True)
```

## Using the Join Parameter
```python
sns.catplot(x="Score", y="Review weekday", data=reviews, kind="point", join=False)
```

## One Last `catplot` Type
```python
sns.catplot(x="Tennis court", data=reviews, kind="count", hue="Spa")
```

## Additional `catplot()` Options
### Difficulties with Categorical Plots

### Using the `catplot()` FacetGrid

### Using Different Arguments
```python
sns.catplot(x="Traveler type", kind="count", col="User continent", col_wrap=3, palette=sns.color_palette("Set1"), data=reviews)
```
- `x`: "Traveler type"
- `kind`: "count"
- `col`: "User continent"
- `col_wrap`: 3
- `palette`: sns.color_palette("Set1")

### One More Look

## Updating Plots
- Setup: Save your graphic as an object: `ax`
- Plot Title: `ax.fig.suptitle("My title")`
- Axis Labels: `ax.set_axis_labels("x-axis-label", "y-axis-label")`
- Title Height: `plt.subplots_adjust(top=0.9)`

```python
ax = sns.catplot(x="Traveler type", col="User continent", col_wrap=3, kind="count", palette=sns.color_palette("Set1"), data=reviews)
ax.fig.suptitle("Hotel Score by Traveler Type & User Continent")
ax.set_axis_labels("Traveler Type", "Number of Reviews")
plt.subplots_adjust(top=0.9)
plt.show()
```

Feel free to adjust the code and add more details based on your specific requirements.