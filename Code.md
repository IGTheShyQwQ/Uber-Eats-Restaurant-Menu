## Set up Part

``` python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
import warnings
warnings.filterwarnings('ignore')
plt.style.use('ggplot')

import folium
from folium import plugins
from folium.plugins import HeatMap

restaurants_menu = pd.read_csv(r'C:\Users\Administrator\Desktop\Python Project\restaurant-menus.csv')
restaurant = pd.read_csv(r'C:\Users\Administrator\Desktop\Python Project\restaurants.csv')

```

### Prep

``` python
in:
free_food = restaurants_menu[restaurants_menu.price == '0.0 USD']
paid_food = restaurants_menu[restaurants_menu.price != '0.0 USD']

print("free_food:", free_food)
print("paid_food:", paid_food)

out:

```

![image-20220530133110692](https://user-images.githubusercontent.com/59614094/171039269-fba47a30-5ec5-4724-8b90-2cb5183bc9a9.png)



``` python
in:
plt.figure(figsize=(16,10))
ax = restaurants_menu['name'].value_counts().iloc[:10].plot(kind="barh", color = 'purple')
ax.invert_yaxis()
ax.title.set_text('Top 10 food menu')
plt.show()
out:

```
![Figure_1](https://user-images.githubusercontent.com/59614094/171039558-55f0bb74-7a2d-4cc8-8456-04b4290c1bb4.png)

``` python
in:
restaurant_merge = pd.merge(restaurant, restaurants_menu, left_on=('id'), right_on=('restaurant_id'))
best_menu = restaurant_merge.groupby('name_y').count().sort_values(by = 'id', ascending = False).head(20)
print(best_menu)

out:
```
![prep image](https://user-images.githubusercontent.com/59614094/171040602-a0329391-85dd-42d5-b632-25c4cc48af49.png)



``` python
in:
from matplotlib import gridspec
import squarify

y = best_menu
fig = plt.figure(figsize=(15,15))
squarify.plot(sizes = y.id, label = y.index, color=sns.color_palette("RdYlGn", n_colors=20), linewidth=4, text_kwargs={'fontsize':14, 'fontweight' : 'bold'})
plt.title('Best Menu', position=(0.5, 1.0+0.03), fontsize = 12, fontweight='bold')
plt.axis('off')
plt.show()

out:
```
![5 best menu](https://user-images.githubusercontent.com/59614094/190022711-cf5ea7fc-1341-4299-9962-7bfdf8f73092.png)





``` python
in:
fig = px.pie(restaurant, names='price_range',title='Price levels in Menus', template = 'plotly_dark')
fig.update_traces(textposition='inside')
fig.update_layout(uniformtext_minsize=14, uniformtext_mode='hide',showlegend=True)

def newLegend(fig, newNames):
    for item in newNames:
        for i, elem in enumerate(fig.data[0].labels):
            if elem == item:
                fig.data[0].labels[i] = newNames[item]
    return(fig)

fig = newLegend(fig = fig, newNames = {'$':'Inexpensive',
                                       '$$' : 'so so',
                                      '$$$' : 'Expensive',
                                      '$$$$' : 'luxury'})


fig.show()

out:
```
![7 pie Chart](https://user-images.githubusercontent.com/59614094/190209045-e27213b3-8e02-430f-99d4-ca467dbdd4c5.png)





``` python
in:
popular_restaurant = restaurant.sort_values(['score','ratings'], ascending=False)
popular_restaurant.head()


df_new = popular_restaurant.dropna()
df_new = df_new[(df_new.lat.notnull())]
df_new = df_new[(df_new.lat != -1) & (df_new.lng != -1)]
df_new = df_new[~df_new.lat.isna()]


places = []

map_offenses = folium.Map(location=[37.09024,-95.712891], zoom_start=4.3)
for i, loc in df_new.iterrows():
    places.append((loc['lat'], loc['lng']))

map_offenses.add_child(plugins.HeatMap(places, radius=18))

out:
```
![8 Heat map](https://user-images.githubusercontent.com/59614094/190212808-74b90aa6-2b71-40d5-8849-736150d093ec.png)

