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



### Best Menu
![5 best menu](https://user-images.githubusercontent.com/59614094/190022667-78332cdd-a3df-4260-8913-b0982decd8c1.png)
