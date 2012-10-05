elasticsearch-internals
=======================

Architecture &amp; Internal documentation about ElasticSearch

Introduction
============

I have always been a big fan of understanding internals of systems, not because I have to or need to, because I feel much more comfortable using systems when I have a deeper understanding of what is going on.  Sometimes better choices on how to use systems, how to configure them, or when or how not to use them can be made only after understanding what goes underneath the covers.

Having a long background with Microsoft SQL Server (for good or bad! :) ) I have always admired the work of [Kalen Delaney](http://twitter.com/sqlqueen), and how well she exposed the internals of MSSQL in an interesting and highly detailed way.  

Additionally I was also inspired by [Lars George](http://twitter.com/larsgeorge).  See [this][1] for an example of his great work in producing a series of blog posts on the internals of how HBase worked.  Thanks to both of these fine people for their efforts and influence.

Much of this information is actually available within the ElasticSearch documentation on elasticsearch.org, but a lot of it is spread around within different module areas, and there really wasn't anything that took some of the important higher level concepts and laid it out in a continuous flow for an interested reader.

I hope this information becomes useful for the ElasticSearch community, and I hope in some small way it gives back to this awesome Open Source project.  Many thanks to [Shay Banon](http://twitter.com/kimchy) and others for this fine project!

Caveat Emptor
=============
This project was started in October 2012, just after ES 0.19.10 was released.  Some of these details may change over time, and given the speed at which the ES project evolves, it could be quite quickly!  

Additionally, this information was created based on my own understanding of how ElasticSearch works, through operational & engineering experience of using the product, and some deep diving within the source code itself (lots of step-debugging too).  But hey, I could be totally wrong. 

There's even areas I'm pretty vague on, and I hope to highlight these clearly, and leave a TODO trail for areas to cleanup.

Please take care when using this information!

regards,

Paul Smith

[@tallpsmith](http://twitter.com/tallpsmith)

Amendments
==========

By all means if you spot errors, omissions, suggestions for clarity, submit a pull request, or raise an issue.

Table of Contents
=================
Since github and relative references seem to just [suck][2], you'll find a directory for each major high level concept.


[1]: http://www.larsgeorge.com/2009/10/hbase-architecture-101-storage.html  "HBase Architecture post by Lars George"
[2]: http://stackoverflow.com/questions/7653483/github-relative-link-in-markdown-file 