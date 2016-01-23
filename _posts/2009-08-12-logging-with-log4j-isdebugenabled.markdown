---
layout: post
date: 2009-08-12 14:39:52 +02:00
tags: [java, programming, log4j, logging, best-practise]
title: Logging with log4J isDebugEnabled
category: Programming
---
{% include JB/setup %}


Excerpt: Alot of times I have seen the questions popping up whether to use isDebugEnabled property or not. Arguably most of the times or rather always about performance. Some of the stuff that I feel important about using it follows.

Alot of times I have seen the questions popping up whether to use isDebugEnabled property or not. Arguably most of the times or rather always about performance. Some of the stuff that I feel important about using it follows.

The answer is simple. It is made to be used. However using it has to be with caution.

For instance 
If I am using the following line in my code.

{% highlight java %}
	log.debug("I am there"); 
{% endhighlight %}

Thats an example of a good practise

However I can really blow it out of proportions if I do the following.

{% highlight java %}
	// Not good practise
	if (log.isDebugEnabled()){
	    log.debug("I am there"); 
	}
{% endhighlight %}

And why exactly is that so. This is because the method debug in the class Category i.e. extended by Logger in the log4j libraries explicitly checks the mode for the logging itself.

Extract from the class org.apache.log4j.Category is below

{% highlight java %}
	public void debug(Object message) {
		if(repository.isDisabled(Level.DEBUG_INT))
			return;
		if(Level.DEBUG.isGreaterOrEqual(this.getEffectiveLevel())) {
			forcedLog(FQCN, Level.DEBUG, message, null);
		}
	} 
{% endhighlight %}


Okay so thats the case where we say dont use it. What about the one where we actually do use the isDebugEnabled property.
	
For instance you have a large parameter going in the debug.
 
{% highlight java %}
	// Bad Practise
 	log.debug("XML "+Tree.getXMLText());
{% endhighlight %}

In such a case it can clearly be said "No dont do it!" If Tree.getXMLText is going to pull out all the hair out of the app then there is no use. As it will be constructed first and if the debug level is not enabled that would be a performance cost.

{% highlight java %}
	// Good Practise
	if (log.isDebugEnabled()){
	    log.debug("XML "+Tree.getXMLText());
	}
{% endhighlight %}

Thus in the example above it would be wiser to use log.isDebugEnabled() just to make sure the mileage or cost stays lesser. 
