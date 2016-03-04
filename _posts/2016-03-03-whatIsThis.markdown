---
layout: post
title:  "What is This?"
date:   2016-03-02 22:47:43 -0800
categories: jekyll update
---
Completing the pre-coursework curriculum and assessments has been a daunting challenge, especially with the pressing cohort start date. Working full time has taken a significant amount of my time and it’s been difficult squeezing in spurts of productive learning. Before finding my way to Telegraph Academy, I had tried my hand at katas, and attended a few of Hack Reactor’s [Algorithm Study Groups](http://www.meetup.com/hackreactor/events/228753374/), but the first sprint and assessment required deeper comfort with the material.

The hands-on emphasis using live professional tools, languages, and technologies sped my trajectory enormously. It’s clear that we’ll hit the ground running on Day 1 – beyond the obvious familiarity with github, the command line, and basic Javascript syntax and patterns, we were required to show comfort with some more general Computer Science concepts.

Working through it, I immediately came across difficulties– a strong grasp of the different scopes we must navigate and manipulate is just the start! While many of the skills and concepts we hope to master are applicable in countless other coding languages, we must overcome the nuances of Javascript in particular. Two early projects require us to rewrite the [Underscore.js](http://underscorejs.org/) library, and create a simple Twitter clone.

These two Sprints ultimately required me to spend time Googling the use of arguments and the means to share information between functions. I quickly found my solution depended totally on the methods .call() and .apply(), the standard tools for this problem. To be able to use these nifty functions, we have to understand the keyword ‘this’, and I was surprised how murky its explanations can be.

Although it was clear that ‘this’ “mostly behaves as a parameter.” The specifics are a bit more complex. The discussion provided by the Hack Reactor material was definitely the clearest, but they made sure to explain what it ISN’T before revealing the extra simple answer for what it IS.

Consider the example below:

{% highlight ruby %}

var someObject = {
  someFunction: function(a, b){
    consonle.log(this);
  }
};

var aSecondObject = {
  aContainedMethod: someObject.someFunction
};

{% endhighlight %}

When we’re referring to ‘this’, we’re NOT referring to the following:

-	The function object ‘this’ appears within
-	If ‘this’ is part of an object literal that’s a method, or within another object, that object it’s within
-	A ‘new instance’ of the function where ‘this’ appears within
-	An object that has fn as property

To understand ‘this’ we need to appreciate the fact that it’s only bound to a value, it only means anything, when the function runs at call time. Consider the following:

‘This’ is tied to the object directly to the left of the dot or brackets at invocation.

In fact the most common way we’ll encounter ‘this’ in the wild is when it’s housed as a parameter to the invocation of an object’s method function. Consider the following:

Now we can clearly see how this is bound to the invoking object.

‘This’ is an exceptionally intuitive, although easily confused identifier. I hope to dig into how ‘this’ empowered me to rewrite the Underscore.js library and recreate a simple Twitter clone, but I’ve much to accomplish in a very short amount of time. Wish me calm seas and a steady wind.


Sebastián
---
