---
layout: post
date: 2008-12-10 16:58:04 +01:00
tags: [howto, programming, software, software,development, utils, tips, sql, dbms_xmlgen]
title: Generate XML - DBMS_XMLGEN
category: Tools
---
{% include JB/setup %}


On my way to my solution store just found this nice to use, old and easy feature.
Possibilities endless, usage typically very easy.

I used the following to generate XML from sqlplus:

	select dbms_xmlgen.getxml('select * from user') from dual; 

Output:
	< ROWSET >
 		< ROW >
			< TNAME >Employee< / TNAME >
  			< TABTYPE > TABLE < / TABTYPE >
 		< / ROW >
	< / ROWSET >

