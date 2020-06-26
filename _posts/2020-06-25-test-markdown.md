---
layout: post
title: Best States To Start Your Real Estate Journey!
subtitle: The best time to start is yesterday, second best time? Now!
comments: true
---
I hear you screaming from thousands of miles away **'TEXAS!'**. I get it, I though the same too. Who can blame us? Texas is the meme state of cheap real estate so what better place to start with right? Well... I'll let the data talk by itself.


## Growth 

You always hear the same cliche saying from stock trading, 'Buy Low, Sell High' (I wish it was that easy). So why shouldn't we use the same principle when it comes to real estate? Except of course for the selling part, how are you gonna build you wealth if you keep giving it away? this is a long term dream, not a get rich quick penny stock. However, the 'buy low' part of the saying is valid, really really valid! If you're going to invest your hard earned money on a propery, you want it to grow so this is the first principle we will be analizing. We want to find states where growth is in the table, not state where growth **was** on the table. In order to accomplish this we'll be looking at 3 different characteristics of each state, staring with:

## Population Growth 

It is a simple supply and demand game, nothing more, nothing less. If you have people fleeing you state chances are there's less people to buy already excisting properties causing them to decreese their prices. If instead you have growing demand and a growing need of housing, the price of properties will rise and include a premium, at the end of the day you are the one that needs a roof and there are another thousand people competing to get that same roof over their head. I manage to scrap some data from the United States Census Bureau and made a comprehensive, easy to read heat map to give you a better idea of which states are getting the biggest population percentage increases. This heat map shows the **average** yearly increase population percentage from 2017 to 2019 (**NOT THE ACTUAL PERCENTAGE POPULATION INCREASE FROM 2017 TO 2019**).

'''
import pandas as pd
#Cleaning data for population change % per state
df = pd.read_csv('http://www2.census.gov/programs-surveys/popest/datasets/2010-2019/national/totals/nst-est2019-popchg2010_2019.csv?#')
dfclean1 = df.iloc[5:56, :]
dfclean1 = dfclean1.reset_index()
dfclean2 = dfclean1.loc[:,['NAME','PPOPCHG_2017','PPOPCHG_2018','PPOPCHG_2019','NRANK_NPCHG2017','NRANK_NPCHG2018','NRANK_NPCHG2019']] 
population_change = dfclean2.copy()
abb = pd.read_csv('https://raw.githubusercontent.com/jasonong/List-of-US-States/master/states.csv', names=['NAME', 'Abbr.'])
population_change = pd.merge(population_change, abb, how='inner', on='NAME')
population_change = population_change.rename(columns={'NAME': 'State','PPOPCHG_2017':'2017 Population Growth %','PPOPCHG_2018':'2018 Population Growth %','PPOPCHG_2019':'2019 Population Growth %','NRANK_NPCHG2017':'Rank 2017','NRANK_NPCHG2018':'Rank 2018','NRANK_NPCHG2019': 'Rank 2019'})
population_change['2017-2019 Population Growth % Mean'] = (population_change['2017 Population Growth %'] + population_change['2018 Population Growth %'] + population_change['2019 Population Growth %'])/3

import plotly.express as px  
fig = px.choropleth(population_change, 
                    locations="Abbr.", 
                    color='2017-2019 Population Growth % Mean',  
                    hover_name="State",
                    locationmode = 'USA-states') 
fig.update_layout(
    title_text = '2017-2019 Population Percentage Growth Mean Per State', 
    geo_scope='usa', 
)
fig.show() 
'''

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

It can also be centered!

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .mx-auto.d-block :}

Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
