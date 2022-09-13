---
title: Biases in Machines
layout: post
date: 2020-11-20 22:44
image: "/assets/images/InvisibleWomen_BookCover_HeroCrop.jpg"
headerImage: true
tag:
- Machine Learning
- Natural Language Processing
- Fundamental Concept
star: false
category: blog
author: aitikgupta
description: Concepts behind induced biases in Natural Language Processing
---

## Introduction
Tune in as I take you through a flashback, relating human understanding with machine-learnt biases. Weird to say that __You read this, but _You_ don't__. It's your conscience reading this without budging _your_ mouth. \
How and when did we learn this incredible ability? And what exactly did we _learn_? \
This brings me to a fundamental concept of __learning__. How do we incorporate knowledge, and more importantly, how can we make _machines_ incapacitate that knowledge?
## Quick Flashback
> You go to school, probably 1st or 2nd class; you have an English period, the teacher starts with writing strange characters on the blackboard; starts saying ___A for Apple___, ___B for Ball___.

Teacher relates those characters with an object, _which is concrete/universal_. An Apple will always be an Apple right? \
You start relating random combinations of letters together, and learn about _words_, which somehow make a lot of sense. \
But how? What happens within our brain? \
Instead of this, there's _a more interesting question_ - __How can a machine understand the same way we do?__
For this, we need a proper structure to represent a word to a machine; after all, it just understands 0 and 1.

## Representing Words
What's the closest thing to binary? _Whole numbers_. They are discrete but have no limits. They can be extended as much as there are words in a language. \
So imagine you represent a word with a number, let's say, _Apple_ can be represented by __1__, _Ball_ by __2__, and so on. \
What would a machine do? Let's say it'll try to remember these words by their numbers; whenever asked, it'd go and refer to that memory. \
Clearly, using this representation has some flaws:
- Talking just about the English language, it adds a new word ___every 98 minutes___.
_Memory is supposed to overflow some day._
- “I like reddish apples and yellowish \_\_\_." - Fill in the blank. You know the answer, _bananas_. Easy, right? But not for a machine.
    - These words would come under a single context umbrella, say ___types of fruits___; if we assign random numbers to every word, their context information is lost.

We need a better representation. Instead of assigning just a single number, how about if we assign arrays of numbers to words? Imagine an array of 2 dimensions:
```
X-axis - 'type of fruit'
Y-axis - 'type of color'
```
![Img](/assets/images/biases-in-machines.png)


| Quadrants 	|              Description              	|
|:---------:	|:-------------------------------------:	|
|     Q1    	|   (apple-like fruit, reddish color)  	|
|     Q2    	|  (banana-like fruit, reddish color)  	|
|     Q3    	| (banana-like fruit, yellowish color) 	|
|     Q4    	|  (apple-like fruit, yellowish color) 	|

Things are getting simpler now (we now know how to place an _Apple_, and a _Banana_ in this coordinate space), now the machine has the contextual information that _Apple is reddish_ and _more apple-like_, and _Banana is yellowish_ and _more banana-like_. 

Yet again, there are some assumptions/limitations:
In this example, the properties used in the context were just _'type of color’_ and _'type of fruit'_. We need __a lot of__ properties to define a word semantic.
> More context <-> More dimensions

Every dimension would yield information about one of the properties of that word. \
But do we really need to know which dimension relates to which property? Can we not just abstract it as just some property?
## Word Embeddings
Imagine a 100 dimensions to represent a single word! This would slightly solve _addition-of-new-words_ problem too. \
If _grapes_ were a new word, we could take some semantic properties from _already-learnt_ words like _apple_ as they both fall under a  _'type of fruit’_. \
This is inspired a lot from human understanding.
> Remember the English class?

Teacher related letters/words to real-life objects. In a nutshell, we were learning what a machine would learn - the actual numbers which would fit in the _n-dimensional_ representation.

We've established that Word Embeddings are an excellent way to represent a word in a machine (at least for now, at least for us), so that it may understand its semantic properties. But, how can we impute the actual values in n-dimensional arrays for words? To learn these embeddings, there are several techniques, several architectures. But rather than the methods, we’ll look at something which is typical for all the techniques, all the approaches.
> ___The Data___.


## The Problem
For most machine learning algorithms, we need training data. In this context, it's textual: any/all historical documentation, manuscripts, literature. \
Any textual data can be used in training/imputing values to those n-dimensional arrays. \
But here's the catch: ___Data is imperfect___. \
How did we come to this conclusion? Let's say we learnt the embeddings for every word there is; we can confirm this inferring the captured semantic information like:
```
King — Man + Woman = Queen
```
This gives us a green signal that we successfully captured the context. Right? But here's where things _go wrong_:
```
Programmer — Man + Woman = HomeMaker
```
Theoretically, machine learning algorithms did their job remarkably by learning the properties and context of words from existing textual data. __The term _"homemaker"_ appeared more frequently with the pronoun _"she"_ than with _"he"_ or _"others"___, so it was more closely associated with _female-ness_ than _male-ness_.
> Even if the learning process was fair, the end outcome, however, was not.

Revisit the class: Remember when the teacher related those characters/words with objects, which are _universal_? \
What if the _'objects'_ are __not universal__? What if they’re abstract, and have a ___different meaning for every conscience___? That is where data imperfection roots in. \
Let's see another example:
> "There are _ days in a week."

\> 7, as simple as that. But here's when it _gets tricky_:
> "There are _ genders." - ??

What would an ML algorithm fill in the blank? \
This highly depends on the type of _data_ the algorithm was trained on; if it was trained just on historical data, there's a high probability that it'll fill an _invalid number_ in the blank. To back up my assumption, take a look at this sentence from the 4th-century literature:
> "You shall not lie with a male as with a woman; it is an abomination."
> — Torah / Bible, Book of Leviticus, Chapter 18, Verses 22

Doesn’t sound so good in 21st century,  with such a _content-aware_ environment, does it? Now imagine a machine, learning from this _(not so perfect)_ literature. \
Clearly, there’s an __induced Bias in Machine__, where it learnt to ___discriminate based on race, colour, sex, language, religion, political or other opinions, national or social origin, property, birth or other statuses such as disability, age, marital and family status, sexual orientation and gender identity, health status, place of residence, economic and social situation___, without us intending it to.

Put something like this in a realtime utility, things can go horribly wrong.
> Read about [Amazon’s secret AI recruiting tool](https://www.reuters.com/article/us-amazon-com-jobs-automation-insight-idUSKCN1MK08G) that showed bias against women

This is just one type of bias, which can result in discrimination based on prohibited legal terms. These problems are severe, especially now that there's been a _revolution_ around _a lot of conceptual facts_, which were previously anticipated to be ground truths.

## Conclusion
How do we solve this? Do we come up with a _teacher-student_ setup, wherein teacher model makes sure the student model doesn’t induce a bias? Or do we come up with a _better representation_ of words for machines altogether? \
It’s an open question, I don’t intend to take it up here.

> __Artificial Intelligence/Machine Learning has gained a lot of attention these last few years, but so has general understanding of _normalization_ in society.__

We talk and boast about no discrimination based on any grounds, but _actually_ putting words into actions - by originating new ideas, by framing new approaches, all the while by taking this discussion under consideration; is probably one of the _best approaches we developers/engineers/thinkers_ can take! :)
