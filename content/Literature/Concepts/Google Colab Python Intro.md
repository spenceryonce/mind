---
title: Google Colab Python Intro
tags:
	- google
	- python
	- howto
	- tutorial
---

Document started from this [Google Colab Document](https://colab.research.google.com/drive/1VNbZeYdnhNnOy5yJ-NnPYhyFXeAcPZs-?usp=sharing)

# Basic Python Syntax and Operations:

## 1. How to define variables?

  The basic data types in python are: (str, int, float, list, tuple, range, set, and bool)

  ```python

  variable_name = "Data" #this auto infers the type to be string (str)
  variable_int = 34 #infers int
  variable_float = 3.4 #infers float
  variable_list = [1,2,3,4] #infers list
  variable_tuple = (1,2,3) #infers tuple
  variable_range = range(10) #contains the numbers 1-10 & infers range
  variable_set = {1,2,3,4} #infers set
  variable_bool = False #infers bool
  ```
 
## 2. How to Control When Things Happen
  
  - Loops can be used to continuously run a section of code (for, while)

  ```python
  fruits = ["apple", "banana", "cherry"]
  for x in fruits:
      print(x)
  ```

  - Conditional Statements allow you to run sections of code based on a condition (if, elif, else). Think of it like this:

  ```vb
  If <condition> then
      do something
  else
      do something2
  ```

  In python, we can do conditional statements like this:

  ```python
  age = 18
  
  if num < 18:
      print("child")
  elif num > 18 and num < 21:
      print("child with rent")
  else:
      print("adult")
  ```

## 3.  Defining Functions And Then Calling Them

-  A **function** is a block of code which only runs when it is called.
-   You can pass **data**, known as **parameters**, into a function.
-   A function can return **data** as a result.
#### Defining Functions

To define a function in python we use the **def** keyword.

  ```python
  def hello():
	  print("hello")
  ```

#### Calling Functions

When we want to run the code inside a function, we can simply write the function's name with () appended to the end like this:

  ```python
  hello()
  ```
  
#### Putting Data into Functions (Arguments)

If we would like to being able to change what happens inside the function from outside the function, we can use **arguments** to pass data (put data) into a function and change the output.

Here is a simple example, where we want to print Doctor in front of the names of our physicians on staff.

  ```python
  def doctor_name(full_name):
	  print("Doctor" + full_name)

  doctor_name("bob rico") #prints to console: Doctor bob rico
  doctor_name("bobby willis") #prints to console: Doctor bobby willis
  ```

  
What if we wanted to have more than one **argument** in our function? No problem! We can have virtually an unlimited amount of arguments in our functions, but should probably stay under 10 when you are starting out.Just remember to include a comma in between each new argument that you add.

Let's try an example, say we wanted to separate the **full_name** into **first_name** and **last_name**.

  ```python
  def doctor_name(first_name, last_name):
	  print("Doctor" + first_name + " " + last_name)

  ```

## 4. Importing Libraries (Using other peoples code)

To enhance the capabilities of Python, we can import libraries that provide additional functions and tools. The `import` statement is used to bring these libraries into your code.

Here's how to import and use the `math` and `datetime` libraries:

  ```python
  import math
  import datetime
  ```

#### Using the `math` Library

The `math` library includes a variety of mathematical functions. For example, to calculate the square root of a number, you can use `math.sqrt()`. Here is how to find the square root of 16:

  ```python
  result = math.sqrt(16)
  print(result)  # Output: 4.0
  ```

#### Using the `datetime` Library

The `datetime` library is useful for handling dates and times. For instance, to get the current date and time, you can create a `datetime` object like this:

  ```python
  now = datetime.datetime.now()
  print(now)  # Output: Displays the current date and time
  ```

Libraries can significantly extend the functionality of your Python programs, without having to write everything yourself. Thus, enabling you to perform complex operations more easily.
  
## 5. File Operations (Reading and Writing)

Handling files is a must-know for reading data from external sources and storing output. Python simplifies file operations with built-in functions. Here's how to read from and write to files:

#### Writing to a File

To write text to a file, you use the `open()` function with the mode `'w'` for writing. If the file doesn't exist, Python will create it for you.

  ```python
  with open('example.txt', 'w') as file:
      file.write("Hello, world!")
  ```

This code snippet opens a file named `example.txt` and writes "Hello, world!" into it. The `with` statement ensures the file is properly closed after the operations are completed.
#### Reading from a File

Reading from a file is just as straightforward. You use the `open()` function with the mode `'r'` for reading:

  ```python
  with open('example.txt', 'r') as file:
      content = file.read()
      print(content)  # Output: Hello, world!
  ```

This will open `example.txt` and print its contents to the console. Using `with` ensures the file is closed once it’s no longer needed.
  
## 6. Data Visualization with Matplotlib

  Matplotlib is a powerful library for creating a wide range of static, animated, and interactive visualizations in Python. Here’s how to use it for basic plotting tasks:
#### Basic Line Graph

To create a simple line graph, you first need to import Matplotlib and prepare some data:
 
  ```python
  import matplotlib.pyplot as plt
  
  # Data for plotting
  x = [1, 2, 3, 4, 5]
  y = [2, 3, 5, 7, 11]

  plt.plot(x, y)
  plt.title('Simple Line Graph')
  plt.xlabel('X Axis Label')
  plt.ylabel('Y Axis Label')
  plt.show()
  ```

This code will display a line graph illustrating the relationship between `x` and `y`.

#### Creating a Bar Chart

Bar charts are another common visualization type. Here's how to create one:

  ```python
  import matplotlib.pyplot as plt
  
  # Data for bar chart
  categories = ['Red', 'Blue', 'Green', 'Yellow', 'Black']
  values = [10, 15, 7, 5, 9]

  plt.bar(categories, values)
  plt.title('Simple Bar Chart')
  plt.xlabel('Categories')
  plt.ylabel('Values')
  plt.show()
  ```

  This plots a basic bar chart with colored categories and their corresponding values.

#### Generating a Histogram

Histograms are great for showing distributions. Here’s how to plot one:

  ```python
  import matplotlib.pyplot as plt
  import numpy as np

  # Generating some data
  data = np.random.normal(0, 1, 1000)

  plt.hist(data, bins=30)
  plt.title('Histogram')
  plt.xlabel('Value')
  plt.ylabel('Frequency')
  plt.show()
  ```

  This histogram displays the distribution of 1000 random numbers generated with a normal distribution, using 30 bins to group the data.
  
  Try to come up with a few of your own graphs and plots to make! What things can you think of that would be fun to visualize? There are so many!!

## 7. Basic Data Manipulations with pandas

Pandas is a powerful library for data manipulation and analysis in Python. It provides structured data operations and functions that make it easy to manipulate tabular data. Here's how to perform some basic data manipulations using pandas:

#### Selecting Columns and Rows

First, let's see how to select specific columns and rows from a DataFrame:

  ```python
  import pandas as pd
  
  # Create a sample DataFrame
  data = {'Name': ['John', 'Anna', 'James', 'Linda'],
          'Age': [28, 22, 35, 32],
          'City': ['New York', 'Paris', 'London', 'Berlin']}
  df = pd.DataFrame(data)

  # Selecting a column
  print(df['Name'])

  # Selecting a row
  print(df.loc[1])
  ```

#### Filtering Data

You can filter rows in a DataFrame based on column values to isolate data that meets certain conditions:

  ```python
  # Filtering based on a condition
  young_people = df[df['Age'] < 30]
  print(young_people)
  ```

This code will display rows where the 'Age' is less than 30.

#### Aggregations

Pandas makes it simple to perform aggregations like summing or averaging data:

  ```python
  # Calculate average age
  average_age = df['Age'].mean()
  print(f"Average Age: {average_age}")

  # Sum of ages
  total_age = df['Age'].sum()
  print(f"Total Age: {total_age}")
  ```

## 8. Introduction to numpy and Array Operations

Numpy is fundamental for numerical operations in Python. It provides support for large, multi-dimensional arrays and matrices, along with a collection of high-level mathematical functions to operate on these arrays.

#### Creating and Manipulating Arrays

Here's how to create and manipulate numpy arrays:

  ```python
  import numpy as np

  # Create a numpy array
  a = np.array([1, 2, 3, 4, 5])
  print(a)

  # Create a 2D array (matrix)
  b = np.array([[1, 2], [3, 4]])
  print(b)
  ```

#### Element-wise Operations

Numpy arrays support element-wise operations, which apply a function or operator to each element individually:

  ```python
  # Element-wise addition
  c = a + 2
  print(c)  # Output: [3 4 5 6 7]

  # Element-wise multiplication
  d = a * 2
  print(d)  # Output: [2 4 6 8 10]
  ```

#### Matrix Multiplication

Matrix operations are straightforward with numpy. Here's how to perform matrix multiplication:

  ```python
  # Matrix multiplication
  result = np.dot(b, b)
  print(result)
  ```

This will calculate the dot product of matrix `b` with itself.

You have now been equipped with the basic tools needed for more advanced data science tasks.

## 9. Using Google Colab Features

Google Colab offers a variety of features that make it a powerful tool for coding, especially for those who utilize Python for data science and machine learning. Here’s how to take advantage of some key features:
#### Installing Packages

To install Python packages in Google Colab, use the `!pip install` command. For example, to install the latest version of `seaborn` for data visualization, you would run:

  ```python
  !pip install seaborn
  ```
  
#### Saving and Loading Files from Google Drive

You can easily link your Google Drive to Colab to access your files:

1. Mount your Google Drive in the notebook:
    ```python
    from google.colab import drive
    drive.mount('/content/drive')
    ```

    2. You can then read from or write to files in your Drive:
    ```python
    with open('/content/drive/My Drive/myfile.txt', 'w') as f:
        f.write('Hello Google Drive!')
    ```

    3. To read the same file:
    ```python
    with open('/content/drive/My Drive/myfile.txt', 'r') as f:
        print(f.read())
    ```

#### Sharing Colab Notebooks

Sharing your notebooks is straightforward:

1. Click on the `Share` button at the top right of the Colab interface.
2. You can then add people by email or copy a link to share with others. You can also set permissions, deciding whether others can view, comment on, or edit the notebook.

## 10. Interactive Widgets in Google Colab

Interactive widgets in Colab can enhance the interactivity of your notebooks, allowing users to manipulate data or control what's displayed dynamically. Here's how to use `ipywidgets`:

#### Creating a Simple Slider

Use `ipywidgets` to create interactive controls. First, install `ipywidgets`:

  ```python
  !pip install ipywidgets
  ```

Then, create a slider that changes the displayed number:

  ```python
  import ipywidgets as widgets
  from IPython.display import display

  slider = widgets.IntSlider(value=5, min=0, max=10, step=1, description='Slider:')
  display(slider)

  def on_value_change(change):
      print(change['new'])

  slider.observe(on_value_change, names='value')
  ```

#### Dropdown Menu

  Create a dropdown menu that outputs the selection:

  ```python
  dropdown = widgets.Dropdown(options=['Option 1', 'Option 2', 'Option 3'], description='Choose:')
  display(dropdown)

  def on_dropdown_change(change):
      print(f"Selected: {change['new']}")

  dropdown.observe(on_dropdown_change, names='value')
  ```

  These interactive elements make Google Colab a more versatile platform for experiments, teaching, or presentations, engaging users directly in the data manipulation process.

## 11. Create Random Numbers And A Chart

We can use python's random library for the random number generation and we can use pandas for making a simple chart by first creating a DataFrame with our requested data in it, and then we can use the plot() function to draw many types of charts. (Bar chart in this example)
```python
import random
import pandas as pd

random_list = [random.randint(1, 100) for _ in range(10)]

df = pd.DataFrame(random_list, columns=['Random Numbers'])

df.plot(kind='bar')
```

## 12. Get Data From An API

For example, let's try to pull data from a [free population api](https://datausa.io/api/data?drilldowns=Nation&measures=Population) which has its data come in this format:
```json
{
	"data": [
    {
		"ID Nation": "01000US",
		"Nation": "United States",
		"ID Year": 2021,
		"Year": "2021",
		"Population": 329725481,
		"Slug Nation": "united-states"
	},
	]
}
```


We can do this easily by using python's request library, to fetch the data from a URL. Once we have the data, we can make a pandas DataFrame from it. We want to extract only specific years of the data to show in our plot, we can do this by using the `isin()` function to check for specific values in a DataFrame.
```python
import pandas as pd
import requests

url = "https://datausa.io/api/data?drilldowns=Nation&measures=Population"
response = requests.get(url)
data = response.json()

df = pd.DataFrame(data["data"])

df_years = df[df["Year"].isin(["2016", "2017", "2018", "2019", "2020", "2021"])]

df_years.plot(x="Year", y="Population", kind="line")
```

## 13. Install Custom Packages on Google Colab

Many times you will want to install a packages not included in python or within Google Colab already. To do this, simply run the following command in an empty cell. 
```bash
!pip install <packagename>
```

For example, to install the ipywidgets library, we can use this command:
```bash
!pip install ipywidgets
```

Combining all of our knowledge so far, we can build a little interactive widget with a chart that updates when you change the Plot Type and Threshold value. 
```python
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import ipywidgets as widgets
from IPython.display import display

# Create some sample data
data = {
    'Category': ['A', 'B', 'C', 'D', 'E'],
    'Values': [23, 45, 56, 78, 33]
}
df = pd.DataFrame(data)

# Define a function to update the graph based on the widget's inputs
def update_graph(threshold, kind):
    # Filter the dataframe
    filtered_df = df[df['Values'] > threshold]
    
    # Plot the dataframe
    plt.figure(figsize=(10, 5))
    if kind == 'Bar':
        plt.bar(filtered_df['Category'], filtered_df['Values'])
    elif kind == 'Line':
        plt.plot(filtered_df['Category'], filtered_df['Values'], marker='o')
    plt.title(f'Graph of Values Greater than {threshold}')
    plt.xlabel('Category')
    plt.ylabel('Values')
    plt.grid(True)
    plt.show()

# Create widgets
threshold_slider = widgets.IntSlider(
    value=20, min=0, max=100, step=5, description='Threshold:',
    style={'description_width': 'initial'}
)

plot_dropdown = widgets.Dropdown(
    options=['Bar', 'Line'], value='Bar', description='Plot Type:',
    style={'description_width': 'initial'}
)

# Display widgets
display(threshold_slider, plot_dropdown)

# Use `interactive_output` to create the interactive elements without immediate display
from ipywidgets import interactive_output

interactive_plot = interactive_output(update_graph, {'threshold': threshold_slider, 'kind': plot_dropdown})

display(interactive_plot)
```

