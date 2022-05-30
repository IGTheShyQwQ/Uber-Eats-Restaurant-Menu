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
![Figure_2](https://user-images.githubusercontent.com/59614094/171041189-84c1b1de-ac00-4778-8ee4-748f8a725a63.png)

