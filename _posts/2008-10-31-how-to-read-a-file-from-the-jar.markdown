---
layout: post
date: 2008-10-31 20:57:54 +01:00
tags: [howto, java, programming, software, software-development, utils, tips, jar]
title: How to read a file from the JAR?
category: Programming
---
{% include JB/setup %}

Someone just asked me this question today. And I thought might as well put it down for info.

{% highlight java %}
 	public TestReadFileFromJar() throws FileNotFoundException, IOException {
        	InputStream is = getClass().getResource("txtData/states.properties");
        	read(is);
	}
{% endhighlight %}

In the case above txtData is placed in the jar on the root. Remmember to add the path with the "/"
