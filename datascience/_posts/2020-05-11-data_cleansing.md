---
background: https://cdnb.artstation.com/p/assets/images/images/024/162/177/large/adomas-storpirstis-threeredlights.jpg?1581510248
layout: post
artist: Devin
subtitle: An exploration into automating data gathering, cleansing and processing.
title: Dirty data
category: datascience
---
## Overview
I wanted to create a dataset from scratch and make a convolution neural network to identity different types of ships. I decided to go with a chinese Type 052 destroyer and a DDG Zumwalt class destroyer. The Zumwalt is distinct from all other ships. I used it in hopes of getting a decent result when training on my local machine against the Type 052.

## Mining Op.
I used my standard tools for this; namely VSCode with the Jupyter extension, Python, Numpy and Keras with the Tensorflow backend. Furthermore, I got to use Amazon’s AWS Rekognition software too. All my code can be found on [github](https://github.com/thepinkturtle/rocket_rhino).

## Getting the dataset
This is really the meat of the exploration. Like most data scientists going down this road, I assumed Google would be the defacto resource. I logged into my under utilized Google Cloud Platform account and began reading the documentation to access the Google Images API. 

I got my api registration key and started reading the documentation on how to use the API. I wanted to try it out for free since I had never used it, and wanted to give it a test drive. After a few failed attempts to access the API I hopped over to stackoverflow.com to see what the issue was that I was facing. 

It became apparent that Google doesn’t allow a free API key to use there image search. Then, I read a comment that recommended using Microsoft’s Bing search engine. Naturally I did want any good millennial should do, when presented with such a comment, I chuckled for a bit. However, after attempting some other failed attempts at getting something to work with the Google API I figured, what the heck it’s 2020! Anything could happen. I typed ```www.bing.com``` into my browser and I’ll never be the same again.

## Bing!
How knew Bing actually worked well for image search. I will likely become a laughing stock, and probably forfeit any future software jobs for saying this, I prefer Bing over Google, for image search.

## Up and running
It didn’t take long to find a small project on github that gave me a tool to scrape images from bing. Unlike Google Image search, Bing doesn’t require you to have a paid API account to use the image search API. +1 for Microsoft. 

I started scraping the web for images of Zumwalts and Type 052s. Within hours I had thousands of images.

## Wash your hands and despair
It’s important, in the day and age of COVID19, to wash your hands and keep things clean. This is no exception to data! I took a small sample size of my images and quickly found garbage images. Stuff that had nothing to do with my subject matter. This would likely spell disaster for my CNN later to come. 

There was no way I was manually going to be able to sift through all my images and pick out the ones that were cluttering up my dataset. 

The days began to look gloomy. Darkness began creeping in on all sides. I began contemplating life, and how I got here. What could possibly have gone wrong? Late at night, whilst in a dark place on the web contemplating things that only the most disparate software engineers would consider. Things that began with titles such as, “Javascript” and “Documentation”.

I cast my eyes down toward the ground in my office and my eyes fell on a brown corrugated box. It had a small symbol on it. Was it just my imagination, or was the symbol smiling at me. I l feared I may have pushed too hard, and my mental psyche just couldn’t handle it. Then, I looked closer, and no, it wasn’t my mushy abused brain conjuring up hallucinations to titillate my consciences into false hopes. It was indeed a small old box.

A box that had once delivered a small dose of dopamine when I’d seen it sitting on my front porch, was what I was staring at. It was in fact an old Amazon Prime delivery box. The Amazon Prime symbol did resemble a small cheerful smile. Indeed, I wasn’t going crazy. Then, a spark of genius struck me. I felt something happen in my skull. Something slightly foreign and strange. Something I hadn’t felt for nearly hours. My brain began working!

## Rekognition
Amazon has a very handy free to use tool called Rekognition. You can upload an image to it, and it will classify your image with a reasonable degree of certainty. Better yet, the folks over at AWS have giving you the tools necessary to call this Rekognition from the command line. I used a small python script to sift through my dataset and clean up my images.

I queried Rekognition for the top four tags associated with my validation image. One for the Zumwalt and one for the Type 052. Then, I saved the tags and had it go over every image in my dataset. If the tags produced by Rekognition didn’t match at least one of the tags from my validation image I flagged it for later inspection and moved it to a different folder in my AWS S3 bucket.

## Electricity and heat
Now that my dataset had been cleaned and was free of garbage I created a few different CNN models and played around with different depths. I adjusted the drop out layers, convolutions layers and feature maps.

I took a weekend of constantly training on my poor old machine to produce some adequate results. My dataset was small, nearly 7k images in all, however using the ```ImageDataGenerator``` package from Keras I was able to maximize model learning on my dataset; via sheer, zoom and horizontal_flip arguments. 

## Results 
Using Seaborn I was able to graph my model performance. My focus was to get as high of accuracy as possible with the least amount of over-fitting. Overfitting can be detected by the difference, in this case, of the numbers for the final epoch. The bigger the difference the worse the over fitting. 

Bigger is better? The age of old euphemism. The training results were promising. However, the difference is visibly noticeable. With test results hovering around 89% and training results near 95% I’m not going to accept this model for much more than some decent over-fitting. You can say that the extra convolutional layer with the bigger feature map may have found some extra hidden features given that both the training and test data seems to have out performed later models. However, if a model is exhibiting this much overfitting it’s really only good as a data point toward converging on a better model.
<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/image_search/32_64_128_1_dropout.png" alt="reported cases of immunizable diseases in california plot">

Let's look at the next one.

Dropout helps prevent overfitting. It does a great job at it. The concept is simple. While training the model essentially turns off randomly selected neurons. This prevent strengthening the neurons that are already gaining traction and may eventually dominate the decision process in the entire model. This allows the model to be more balanced and essentially helps stop overfitting. In thi case, adding another layer of dropout didn’t help. A bigger model isn’t necessarily better.

<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/image_search/32_64_128_2_dropout.png" alt="reported cases of immunizable diseases in california plot">

These next two models I kept everything the same except for the dropout and convolutional layers. One dropout layer and only two convolutional layers don’t preform much better than the previous one. The amount of overfitting was very obvious as well. The convergence seems to be getting worse with each epoch up until epoch 60 where it almost looks like it’s approaching an asymptote. 

<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/image_search/32_64_1_dropout.png" alt="reported cases of immunizable diseases in california plot">

We have a winner. No gold ribbons for accuracy, however the overfitting appears to have been solved. Adding that extra layer of drop out and thinning down the convolutional layers appears to be giving promising results.

<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/image_search/32_64_2_dropout.png" alt="reported cases of immunizable diseases in california plot">

## Take-aways
In all the cases we saw that overfitting was really the major issue. There were some promising results in the bigger models with more layers. The overfitting though, removes all confidence that these models would actually do a good job. The smaller models clearly suffered from poor performance regarding accuracy. The major conclusion to draw from these results is, more testing needs to be done. Perhaps, adding a third layer of dropout on the 32x64x128 model would have diminished the overfitting. Or, and more likely, if we could acquire more data, perhaps we’d see better results across the board. Either way, data science is a wide open field with plenty of room for discovery and exploration.


## Sources 
Banner and thumbnail taken from [Adomas Stropirstis](https://www.artstation.com/artwork/Qz4LGB)
