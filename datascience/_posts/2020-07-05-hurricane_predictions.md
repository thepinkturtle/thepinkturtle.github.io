---
background: https://cdna.artstation.com/p/assets/images/images/016/158/458/large/alex-rommel-galactical-storm1250.jpg?1551126761
layout: post
artist: Devin
subtitle: Hurricane season is upon us, how can technology help?
title: Supervised Neural Networks classifiying hurricanes?
category: datascience
---
## Overview
<img style="height: .001%; width: .001%;" src="https://cdna.artstation.com/p/assets/images/images/016/158/458/large/alex-rommel-galactical-storm1250.jpg?1551126761" alt="Galactial storm fictional drawing">


## Hurricanes
Everyone knows that hurricanes are one the most destructive forces on the planet. How can we use technology to help aid in advanced warning and potentially save lives? I decided to get my feet wet and build a neural network that classifies storms based on the following parameters: latitude, longitude, month, pressure, wind speed and time of day.

## Overview
I started out naively thinking that I could just toss this data into my neural network and it’d learn the formula for storm classification. Well, it wasn’t quite that easy. There were a few stumbling blocks along the path that I had to overcome in order to boost my accuracy to create a useful classifier. 

## latitude and longitude
There are various ways of handling these data points. At first I contemplated making dummy variables for all the combinations of these and then just settling on a huge feature set consisting of a large sparse matrix. After attempting this and watching my features grow from 8 to nearly 1000 I took this back to the drawing board. I did a little research and found that the best method is to map the latitude and longitude onto a x,y,z cartesian coordinate system. 

The actual mapping is quite elementary

## Mining Op.
All my source code can be found in my [Github](https://github.com/thepinkturtle/crazy_coconut) repo. I used Python, Pandas, Numpy, Matplotlib, Jupyter, graphviz, seaborn
## Purpose


## Dataset
My dataset was a curated one from [kaggle](https://www.kaggle.com/noaa/hurricane-database). My goto source for fun and interesting datasets.

## Wrap up


## Sources 
Banner and thumbnail taken from [Alex Rommel](https://www.artstation.com/artwork/3ovPmo)
