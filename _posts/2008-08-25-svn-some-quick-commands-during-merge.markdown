---
layout: post
date: 2008-08-25 15:55:54 +02:00
tags: [howto, scripting, svn, build, automation]
title: SVN - some quick commands during merge
category: Programming
---
{% include JB/setup %}

Following are some of the frequently used svn commands during merging and branching. I used to work with tortoise for this but as soon as I learned these, it feels like a more easier space to be in. Although no points taken away from tortoise, it still works pretty good for the gui part, This article is more  targeted towards dark screen lovers.

Create a new branch from trunk:
If you want to create a branch from a specific revision of Trunk following command is handy. It does a remote copy. which means the machine you are on does not need a copy of the whole tree.

{% highlight java %}
	$ svn copy -r REVISION TRUNK_URL NEW_BRANCH_URL --username USERNAME --password PASSWORD -m MESSAGE
{% endhighlight %}

An example

{% highlight java %}
	$ svn copy -r 1234 http://shaafshah.com/trunk http://shaafshah.com/branches/MY_BRANCH --username foo --password bar -m "Remote copy"
{% endhighlight %}

When was this branch created?
If you want to know the day branch was created.

{% highlight java %}
	$ svn log -v --stop-on-copy BRANCH_URL
{% endhighlight %}

The last record will show you the day the branch as created.

List all the branches:
If you want to take a listing of branches or a tree

{% highlight java %}
	$ svn ls BRANCHES_URL
{% endhighlight %}

e.g. http://shaafshah.com/branches

Merge from Branch to Trunk:

Browse to where you have checkedout trunk in the local directory.

{% highlight java %}	
	$ cd shaafshah.com/trunk
{% endhighlight %}

Update trunk to HEAD.

{% highlight java %}
	$ svn update
At revision 1234.
{% endhighlight %}

Following will merge from branch to trunk but will not commit.

{% highlight java %}
	$ svn merge -r BRANCH_REVISION:TRUNK_REVISION BRANCH_URL
{% endhighlight %}

Branch_REVISION will be the revision branch was created if this is the first time you are doing the merge.

{% highlight java %}
	$ svn merge -r 1233:1234 http://shaafshah.com/branches/my_new_branch
{% endhighlight %}

After this you should do an

svn status

to check the status of the files. the files will be marked with following Characters.

'A' Added
'C' Conflicted
'D' Deleted
'I' Ignored
'M' Modified

If there is any 'C' in the status the files will not be committed if you try an svn commit to save the merge to the trunk.

Merge from Trunk to Branch:

To merge from Trunk to branch you would need to browse to the branch checked out in the local direcotry.

{% highlight java %}
$ cd shaafshah.com/branches/mybranch
$ svn update
At revision 1234.
{% endhighlight %}

The following command will try merging trunk from revision 1233 i.e. the day branch was created to branch head.

{% highlight java %}
$ svn merge -r 1233:HEAD TrunkURL BRANCH_URL
{% endhighlight %}

Hopefully this should help. However you should definitely refer to SVN Book for more detail.

svnbook at 
[SVN Book](http://svnbook.red-bean.com/)
