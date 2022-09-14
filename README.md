# Uber-Eats-Restaurant-Menu

![ubereats](https://user-images.githubusercontent.com/59614094/189784478-b5a2a759-04ba-4e99-b341-7e153f067dd4.jpg)

*This is a data project analyzed dataset that contains lists of restaurant and their menus in USA that are partnered with UBER EATS.*



### Preparation:

- csv file read: using read.csv ('file name')
  - you may use relative path to read the csv file
  - or put the csv file under the same directory with the py file to just put name in the input.
  - ![read csv](https://user-images.githubusercontent.com/59614094/189787617-90743740-4df6-4468-99a7-2424491f3331.png)

- Check the data you just read

  - Using dataset.head(i) to take a look at the data from the beginning
    - you may put a number to check the first i number of rows
    - ![head input](https://user-images.githubusercontent.com/59614094/189787558-5dee376f-d205-4e37-8e4d-cfe486520d80.png)


  - Also you may use dataset.tail(j) to take a look at the data from the last

### Graphs creation ###

#### Menu Name - wordCloud ####

*Graph shows the frequency of the items ordered the most to the least.*
![3 Menu name](https://user-images.githubusercontent.com/59614094/189794293-2d397ea8-e130-4c09-a4ae-ff0788ac8ecf.png)

- we firstly retrieve the column name of the menu out of the whole data.
- Secondly convert the data to dictionary using value counts feature then generate the wordcloud.
- thirdly filled up the width, height, background_color....etc., but be careful with how to generate the data, we show data according its number of occurrence.
- Reference:
  - [Usage of wordcloud](https://blog.csdn.net/u010309756/article/details/67637930)
  - [Pandas value.counts()](https://pandas.pydata.org/docs/reference/api/pandas.Series.value_counts.html)
  - [matplotlib.pyplot.imshow](https://pandas.pydata.org/docs/reference/api/pandas.Series.value_counts.html)



#### Top 10 Menu - Bar Graph

*Graph shows the top 10 best sellers of all restaurants*

![top 10 menu](https://user-images.githubusercontent.com/59614094/190021664-b2f9550b-901e-4f66-b80f-e608a1c21ad7.png)

- we firstly retrieve the column name of the menu out of the whole data.
- count the value of the names from the most to least and show the first 10.
- invert the y axis of the graph and set the title to "Top 10 name menu"
- Reference:
  - [matplotlib.pyplot.imshow](https://pandas.pydata.org/docs/reference/api/pandas.Series.value_counts.html)



### Best Menu -  Squarify plot

*Graph shows the top 20 best food among all restaurant*



![5 best menu](https://user-images.githubusercontent.com/59614094/190022667-78332cdd-a3df-4260-8913-b0982decd8c1.png)



- we first merge the restaurants and restaurants_menu together.
- After the merge we group the items by column "name_y".
- plot the graph.
- Reference:
  - [Matplot - Gridspec](https://matplotlib.org/stable/api/_as_gen/matplotlib.gridspec.GridSpec.html)
  - [Squarify plot](https://www.analyticsvidhya.com/blog/2021/06/build-treemaps-in-python-using-squarify/)



### Restaurant Price Types - Pie Charts

*Graph shows the difference expense level of all the restaurants*

![7 pie Chart](https://user-images.githubusercontent.com/59614094/190208908-c69955fd-accc-4f3d-9ab9-eea201eb5e44.png)

- Since the dataset contains the column shows the types of the restaurants
- We simply just enumerate the data and get them together.
- Reference:
  - [Pandas.sort](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_values.html)



### Heatmap Restaurants in USA

*This graph shows the heatmap of all restaurants*

![8 Heat map](https://user-images.githubusercontent.com/59614094/190212750-0ca6d0a7-a3b9-4ef6-b3d9-bc211125b31b.png)


- We first sort the restaurants using the sort value to filter the restaurants from the most popular to least popular.
- Next we gonna drop NA values from the restaurants dataset, also including the latitude not null
- The second step needs us to manually take a look at the data.
- We iteratively append the spots into our places and put it into the map.
