---
layout: post
title:  "What is 'this'?"
date:   2016-03-02 22:47:43 -0800
categories: jekyll update
---
Completing the pre-coursework curriculum has been a daunting challenge, especially with the pressing cohort start date. Working full time really takes nearly <em>all</em> time and it’s been difficult squeezing in spurts of productive learning. Before finding my way to Telegraph Academy, I had tried my hand at many tutorial courses, katas, and attended a few of Hack Reactor’s [Algorithm Study Groups](http://www.meetup.com/hackreactor/events/228753374/), but the first sprint and assessment required deeper comfort with the material right off the bat.

The hands-on emphasis using live professional tools, languages, and technologies sped my trajectory enormously. It’s clear that we’ll hit the ground running on Day 1 – beyond the obvious familiarity with github, the command line, and basic Javascript syntax and patterns, we've been required to show growing comfort with more general Computer Science concepts.

Working through the material, I immediately came across difficulties– a strong grasp of scopes, 'this', and recursion is just the start! While many of the skills and concepts we hope to master are applicable in countless other coding languages, we must overcome the nuances of Javascript in particular. Two early projects require us to rewrite the [Underscore.js](http://underscorejs.org/) library, and create a simple Twitter clone using [jQuery](https://jquery.com/).

These two Sprints ultimately required me to spend time Googling the use of arguments and the means to share information between functions. I quickly found my solution depended totally on the methods [.call()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) and [.apply()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply), the standard tools for this problem. To be able to use these nifty functions, we have to understand the keyword [‘this’](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this), and I was surprised how murky its explanations can be.

Although it was clear that ‘this’ “mostly behaves as a parameter.” The specifics are a bit more complex. The discussion provided by the Hack Reactor material was definitely the clearest, but they made sure to explain what it ISN’T before revealing the extra simple answer for what it IS.

Consider the example below:

{% highlight javascript %}

var someObject = {
  someFunction: function(a, b){
    console.log(this);
  }
};

var aSecondObject = {
  aContainedMethod: someObject.someFunction
};

{% endhighlight %}

When we’re referring to ‘this’, we’re NOT referring to the following:

-	The function object ‘this’ appears within (e.g. someObject{})
-	If ‘this’ is part a method, or within another object, <em>that</em> object 'this' is within (e.g. someFunction())
-	A ‘new instance’ of the function where ‘this’ appears within  (e.g. someFunction() at run time)
-	An object that might happen to have the 'this's containing function as property (e.g. aSecondObject())

To understand ‘this’ we need to appreciate the fact that it’s <em>ONLY</em> bound to a value, it only means anything, when the function runs at call time. Consider the following, while passing some objects to work with:

{% highlight javascript %}

var someObject = {
  someFunction: function(a, b){
    console.log(this);
  }
};

var aSecondObject = {
  aContainedMethod: someObject.someFunction
};

var manzana = {}, naranja = {}, platano = {};

someObject.someFunction(naranja, platano);

{% endhighlight %}

'this' is bound <em>only</em> at the point at which it's called.

{% highlight javascript %}

someObject.someFunction(naranja, platano);

{% endhighlight %}

Finally, ‘this’ is tied to the object <em>"directly to the left of the dot (or brackets) at invocation"</em> and 'this' is bound to someObject{}

In fact the most common way we’ll encounter ‘this’ in the wild is when it’s housed as a parameter to the invocation of an object’s method function. Consider the following:

{% highlight javascript %}

var someObject = {
  someFunction: function(a, b){
    console.log(this);
  }
};

var aSecondObject = {
  aContainedMethod: someObject.someFunction
};

var manzana = {}, naranja = {}, platano = {};

manzana.method = someObject;

manzana.method(naranja, platano); // Console logs "manzana", "naranja", and "platano"

{% endhighlight %}

By making someFunction a method of another object, we can clearly see how 'this' is bound to the invoking object: it gets logged in our example :D

‘This’ is an exceptionally intuitive, although easily confused identifier; I hope to more adequately dig into how ‘this’ empowered me to rewrite the Underscore.js library and recreate a simple Twitter clone, but I’ve much to accomplish in a very short amount of time, I'll have to circle back. Wish me calm seas and a steady wind.


Sebastián
---
