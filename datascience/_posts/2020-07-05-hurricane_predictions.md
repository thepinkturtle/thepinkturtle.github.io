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

## Mining Op.
All my source code can be found in my [Github](https://github.com/thepinkturtle/crazy_coconut) repo. I used Python, Pandas, Numpy, Matplotlib, Jupyter, graphviz, Ann Visualizer, seaborn

## Dataset
My dataset was a curated one from [kaggle](https://www.kaggle.com/noaa/hurricane-database). My goto source for fun and interesting datasets.

## Model creation
I found that best performance from a multi-layered neural net with 18 input features and 9 output features. Observe the following images for a better understanding of the shape of the network.

[picture](picture)
<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/hurricane_network.png" alt="Neural network layers visualized">

<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/hurricane_layer_detail.png" alt="Neural network shape with details">


## latitude and longitude
There are various ways of handling these data points. At first I contemplated making dummy variables for all the combinations of these and then just settling on a huge feature set consisting of a large sparse matrix. After attempting this and watching my features grow from 8 to nearly 1000 I took this back to the drawing board. I did a little research and found that the best method is to map the latitude and longitude onto a x,y,z cartesian coordinate system. 

The actual mapping is quite simple. I converted the latitude and longitude through three simple functions. 
R is the radius of the earth in kilometers (6371)
x = R * (cos(lat) * cos(long))
y = R * (cos(lat) * sin(long))
z = R * sin(lat)

## Feature Selection
This was the most difficult part. I began curating this dataset many weeks prior to any actual results. I struggled with knowing what to do with the time, date, latitude and longitude. I didn’t know if I should “one shot hot encode” everything into dummy variables or remove the features entirely.

After looking over the dataset I decided that the most significant records only utilized the times, 0600, 1200 and 1800. Very few had time measurements beyond the aforementioned ones. I completely disregarded the ocean the storm was in i.e., Atlantic, since I already had global positioning data. I also threw out the name of the storm. 

I noticed that most of the earlier dates had next to no pressure and wind speed measurement. I excluded all data that had garbage measurement. The pressure was measured as being -999 for older storm systems. This is due to older equipment that didn’t have the sensitivity to record meaningful data. In the software world we use the adage “garbage in, garbage out.” I ignored these records and continued building the model without any series implications.

## Performance
The accuracy of the network was admirable with ~85%. Only having 3 hidden layers with neurons between the number of inputs and outputs (18 - 9 respectively). A little be of research indicates that there is no formula to give you the optimum number of neurons per hidden layer. However there are some general guidelines. I decided to experiment with the number of neurons and ended up with this configuration yielding the best results.


<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/hurricane_accuracy.png" alt="Neural network accuracy plot">


## Wrap up
In the end, the model did a decent job classifying hurricanes based on the 18 features. It’d be interesting to build another time series model and an LSTM layer or some other form of an RNN and see if it can predict a hurricane based on previous readings. I might end up doing that and if so I’ll update this exploration. 

For now this was a great exercise in feature encoding and data preparation. Sometimes all your time is spent in that data preparation and only a little bit of time is spent actually creating the model. 

## Sources 
Banner and thumbnail taken from [Alex Rommel](https://www.artstation.com/artwork/3ovPmo)




## Sources 
Banner and thumbnail taken from [Alex Rommel](https://www.artstation.com/artwork/3ovPmo)
