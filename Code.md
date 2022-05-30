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