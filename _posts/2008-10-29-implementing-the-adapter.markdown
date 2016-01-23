---
layout: post
date: 2008-10-29 20:47:56 +01:00
tags: [computers, design, design-patterns, gof, howto, java, patterns, programming, software, software-development, adapter-pattern, adapter]
title: Implementing the adapter
category: Programming
---
{% include JB/setup %}

Typically when implementing an interface you would have to implement all the methods that exist in that interface.  A very good example is the MouseListener in the java Swing. When you need to implement more then one method where as typically you might be catching only one of them.  Saying that you would also find a Mouse Adapter provided as well. Some of us use that often. And that is part of the Adapter pattern. It makes life easier for me sometimes.

Adapter a structural pattern will let you adapt to a different environment. The joining between different environment is called Adapter. Thus basically giving others the interface that they expect or vice versa when your program becomes the client.

For example the following class expects that the implementing class should be implementing all three methods.

{% highlight java %}
	public interface RecordListener {
		public void eventPrePerformed(RecordEvent recordEvent);
		public void eventPerformed(RecordEvent recordEvent);}
		public void eventPostPerformed(RecordEvent recordEvent);
	}
{% endhighlight %}

So lets say our implementing class is a rude one and only wants to implement one method. What do you do as an API designer. hmmm

Thats where we step in with the Adapter.

{% highlight java %}
	public abstract class RecordAdapter implements RecordListener {
		public void eventPrePerformed(RecordEvent recordEvent) {}
		public void eventPerformed(RecordEvent recordEvent) {}
		public void eventPostPerformed(RecordEvent recordEvent) {}
	}

	public MyAdapterImpl extends RecordAdapter{

	public void eventPerformed(RecordEvent recordEvent){}

	}
{% endhighlight %}


Now the only thing left to do is use the adapter. And override any method that you might need .

{% highlight java %}
	public MyClientClass {
		public MyClientClass(){
			this.addRecordListener(new MyAdapterImpl());
		}

	}
{% endhighlight %}
