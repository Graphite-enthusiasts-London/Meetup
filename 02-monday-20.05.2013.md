Note: this is a draft

Attendance
==========
There was about 13-14 people attending this second edition

Venue
========
We had the chance to be in TIM Group's office.
We were warmly welcommed with pizza an refreshment.
Kudo to Adam, Jeffrey, Tom and the team to host us.

Presentation
============
  * Jeffey took the presenter seat and engage the group in a discussion about his experience with graphite so far
  * Another team memmber gave us an interessing ignite talk about why we should use elastic search as a data source backend instead of graphite.

Usage
=====
 * 80 : already using graphite
 * 10 : not yet

OS:
==
 * 50 : Red Hat based
 * 50 : Debian based
 * 10 : Gentoo based

Role
====
 * 3 app devs
 * 7 admins
 * 2 pointy-haired boss


Organiser's corner:
===================
 * Github access: Nobody seems filled with enthousiasm to do the minute, equaly the link to github was missing from the meetup page.
 * Co-owner: Nobody was interested yet into co-owning the meetup
 * Graphite weekly/ mailing list: I will make a mailing list available soon(ish)

What do we use graphite for?
============================
That's the question that got us talking the most this time "realtime vs diagnostic".
 * A self service alerting tool: Add event without ops intervention, Empower devlopers.
 * A real time monitoring tool, usefull for A/B testing, or see the imnpact of a change, help identify a serious situation
 * A tool diagnostic problem and to compare behavior overtime, find trends earlier, Give you some contex on where to go in the stack.
 * A tool to look at thing closer
 * A tool for vanity metrics:
   * today vs yesterday
   * week vs day

yuno graphite :
===============
- easy to graphite
- iteration
- graph from the past
- linking back to the source

The elastic search way
======================
Elastic search is a tool that allows you to index events.
It is a very powerful tool coupled with logstash for data kibana to visualise the results.
By storing logs or structured data with logstash and elastic search, you actually store context and the value you are interesd in.
Logstash also allow to send data out to statsd, that can then be use within graphite.

Starting with Graphite:
=======================
"github default are broken"
Defualt downsampling method is average, there is a naive approach to average, i will defnilty not work for all data type.
Getting the retension time and the definition right is hard.
With no internet package are needed, they are no package in the usual trusted source.

Graphite shortcomings:
======================
Change the data meaning is a risk : graphite data can easily become inconsistent, if the source change the meaning of a certain data point.
"The root hieracy is wrong" : usually a component name, a device name, inherent difficulty to name things consistently accros the board.
A data bag or something looser, more flexible would be better (riak bucket?)
Graphite as a self service iS not performing as well as hope in practice : 
 * IO comes in the way at some point, that will require Ops intervention.
 * The default are not a one size fits all: lots of customisation required to get the data in the right shape overtime.
How often do you remove a tree that has gone stale?
Did it gone stale because the data is not produced anymore or did the component broke.
NIl is indeed different than zero, even if the interpretation of zero and nil is sometime the same.

Scaling issues:
===============
How to scale from 8servers to 2000?
The clustering support is very labor intensive and require some difficult manual task.
In that regards, elastic search is scalable for free.
Sugguestion that we need a (distributed) fs for the metrics ala HDFS (Hadoop Distributed File System)
What about federated mode, and a clever way to use the cache?

Next steps with the data:
=========================
Taking action on the data held within graphite is not trivial.
Not so much going on on automation after the data is stored within the group
Attempt to do trending that lead to be more proactive.
Early warning to be able to predict week end work (disk running out of space etc...)

Statsd
======
"statsd is evil"
30% loss in statsd with UDP.
Ioannis adding tcp to statsd python implementation.
Saulius adding tcp to statsd nodejs imnplementation 
Some people use udp in a loopback and connect with tcp to the graphite host.

Choosen bits
============
Infras are run by humans, there will be errors!
Monitoring screen on your desk is way too old fashion, put your monitoring screen by the loo.

Tools:
======
* Tattle: A self service alerting and dashboard frontend for graphite and ganglia https://github.com/wayfair/Graphite-Tattle
* storm by etsy (the aformentionned project couldn't be found ?)

Metrics porn:
=============
 * infrastructure automation
7 puppet 
3 chef 3
1 cfengine 
1 custom to deploy 

 * Advance usage
3 people on alerting
3 person do HA : carbon relay.

coolest graph:?
==============
This month it was "the number of graph you graph"
Apparently we are not the only one thinking about it.
Jason "obfuscurity" Dixon from github deliver on the subject http://obfuscurity.com/2013/05/Graphite-Tip-Counting-Number-of-Metrics-Reported
