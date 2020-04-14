---
background: https://cdnb.artstation.com/p/assets/images/images/019/174/461/large/olamar-gibson-kd-bk-final.jpg?1581777970
layout: post
artist: Devin
subtitle: NBA players put to the test.
title: Does higher salary mean you're a better preformer?
category: datascience
---
I began wondering, how much does performance affect your salary? If I’m a super-duper programmer, do I get a super-duper salary? It’s really hard to gauge a programmers abilities. Their is so much that goes into being a “good” programmer that it’s a very difficult problem. So much so, that we now have companies that programmers pay to get them up to snuff, straight out of college. The hiring process is broken for programmers. That’s a deep rabbit hole for later.

I decided that athletes’ performance is directly measurable to a good degree. I went out, and found a dataset that gave me a good aggregation of the top NBA players in the spans of 2005-2014, somewhat dated I acknowledge. Nonetheless, It’s an interesting dataset. This set was gathered from the folks over at [superdatascience](https://www.superdatascience.com).

The python scripts used to generate these plots are over on my [github](https://github.com/thepinkturtle/jupyter/blob/master/basketball_matrix(4).ipynb). I used numpy and matplotlib for this mining operation.

In the first plot, it’s interesting to see the divergence between Kobe Bryant (RIP) and the other top players. Even Lebron James didn’t touch Kobe for nine years! Even then, Kobe still made more dough!

<img style="background-color:gray; height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/salary.png" alt="NBA player salaries">


Dwight Howard killed it the field goals per attempt arena. He at one point, had an accuracy of over %60! I mean, that’s amazing! Basically, if you’re his opponent and he goes up for one, you might as well spit in his eyes, because that’s the only chance you might have of stopping the guy. 

<img style="background-color:gray; height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/fieldgoalsperattempt.png" alt="Field Goals per attempt made">

Dwight Howard also was in the median payscale for all these guys in beginning. In 2005-6 he was in the top of his class with accuracy, however he shot for less than the rest of them. Though, it looks like he had a decent agent because after his performance in 2005-6 seasons he more than doubled his salary and it continued to increase. Even though his field goals per game varied by a approximately one attempt.

<img style="background-color:gray; height: 100%; width: 100%;" src="https://raw.githubusercontent.com/thepinkturtle/thepinkturtle.github.io/master/datascience/_posts/images/fieldgoalspergame.png" alt="Field Goals per game">

There are many factors that need to be consider for an analysis on this data. Position is a big one, injuries is another and then there’s a lot of smaller factors. Some of Kobe Bryant’s best performances were when we was less of a household name. Meaning, that to some degree, as you get more fame you get covered a lot more. Naturally, if you're a young upstart prodigy it’s going to take a season or two before other teams start putting their best against you. Once that happens you’re going to have less easy shots available. Which will result in a drop in stats. 

These are just some interesting findings and discussion points. These findings would be a great starting point for some serious deep data mining. 


Background and thumbnail image by: <a style="color:white;" href="https://www.artstation.com/artwork/DxBK3e">Olamar Gibson</a>