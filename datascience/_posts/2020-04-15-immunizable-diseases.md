---
background: https://cdnb.artstation.com/p/assets/images/images/019/383/585/large/monkeyverse-mv-qs-hum-epidemiologist-final.jpg?1563249587
layout: post
artist: Devin
subtitle: A brief look into immunizable diseases
title: They are trying to kill you
categories: datascience
---
Immunizable diseases are the diseases that have known and effective vaccines. During this time of novel COVID-19 crisis. I thought It’d be interesting to look at historical outbreaks of other known pathogens. I chose California for two reasons: the foremost being, it had the most updated complete publicly available dataset I could easily get my hands on. The second reason; because california is like a small country unto its own. In many ways it can be treated as a simulation of what over states will encounter if they follow the same socio economic trends. 

I got my dataset from the [California Department of Public Health](https://www.cdph.ca.gov/Programs/CID/DCDC/Pages/Immunization/disease.aspx)
and my python scripts can be found on [github](https://github.com/thepinkturtle/jupyter/blob/master/immunizable_diseases_california.ipynb). I used numpy, pandas, seaborn and matplotlib for this data mining operation.

Clearly, the total number of cases is on an upward trend. However, it seems to exhibit a pattern of a small bathtub curve with approximately a 5 year cycle. As though; an outbreak occurs, an effort goes into outbreak control, it's effect and then it happens again. The concerning part is that the cases increase for each new cycle.

This could be due to a variety of factors. Perhaps, population growth. There could be more people moving to California. This would result in more cases reported. However, it might not mean that the overall percentage of the infected population is increasing. The percentage of infected population per outbreak, could be the same or decrease. We really can't tell. All we really know is that California keeps having more cases of immunizable diseases reported, and that’s it. 

<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/reported-cases-california.png" alt="reported cases of immunizable diseases in california plot">

<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/cases-by-county.png" alt="reported cases of immunizable diseases by counties in california plot">

<img style="height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/cases-los-angeles.png" alt="reported cases of immunizable diseases in los angeles county plot">

Thumbnail and banner art sourced from [Yuvraj Jha](https://www.artstation.com/artwork/nQOJkX)
