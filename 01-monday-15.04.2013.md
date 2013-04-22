Attendance
==========
There was about 11 people attending this first Graphite meetup

Presentation
============
  * Ed with his rails and statsd/graphite presentation Statsd/graphite http://errm.github.io/statsd-slides/ 
  * Hector with a demo of a gdash https://github.com/ripienaar/gdash/

Usage
=====
  80 : already using graphite
  20 : not yet


OS
==
  80 : Red Hat derivative
  20 : Debian derivative

Dashboard Used
=============
  * Graphite : https://github.com/graphite-project/graphite-web
  * Gdash : https://github.com/ripienaar/gdash
  * Tasseo : https://github.com/obfuscurity/tasseo
  * Dashing : http://shopify.github.io/dashing/

Venue
=====
  * Internet : mac users had problem, it seems that it got better at some point (information needed)
  * Space : it seems to be alright for a small number, not sure if that place scales (information needed)

Discussion
==========
  * Other backend
    * Opentsdb/hbase https://github.com/OpenTSDB/opentsdb
    * Hosted graphite redis based https://www.hostedgraphite.com/

  * StatsD
    * Installtion : a breeze on MacOS
    * Admin : to avoid DNS resolution overhead, use a statsd instance per application (who does have 20M)
    * Admin : takes the paint from creating the datapoint in graphite first.
  
  * Java monitoring
    * jmx : needs to create the datapoint twice, in jmx and grapite
    * metrics.codehaus.zzz : just a jar in you load path, give you garbage colector, jetty, log4j and + for free, low overhead.

  * DevOps
    * System metrics : allows you to get your point to the other teams. An example where all the component are tracked, helped a fellow graphite ranger to pin point what was wrong and stopped the finger pointing.

  * Metrics
    * n to 1: extrapolate plenty of metrics to meaningful single data point/curve is difficult.
    * Vanity metrics : your boss/business looks at it, add value to the "graph everything proposal"

  * Package(s)
    * Graphite/dashboard : installation is a pain (especially in the RPM world)
    * Components/Depedencies : Not in the official repo (Red Hat/CentOS) or too old in the alternative repo (EPEL) 
    * Sources : we end up using source (git/tarball) and compile it ourslef.
    * Repo : we all maintain our own packages repository.
    * Glue : we all use scripts that do magic, once in a while from the contrib/ folder
  
  * Bookmarks
    * Anthracite : track event/change managament https://github.com/Dieterbe/anthracite
    * Dashing : a framwork to build screen of dashboards (from lot's of sources) http://shopify.github.io/dashing/    
  
  * Gdash
    * Brings a level of abstraction (reference to made to chef), nice if you don't wnat to do a 400+ characters query by hand.
    * Brings a way to pass json definition (think host definition) to a graph, help to scale.
    * Can be script to automate dashboard creation.
    * Can use some ruby inside the template ( an example inside the gdash documentation could help to promote that feature)
    * Default provided for munin and collectd view.
    * Search in the latest version, comes handy once your dropdowns go bellow the bottom of the web page.

  * Data collection
    * Collectd : seems pretty obvious candidate, still people compile it and have to rely on their version (see packaging )
    * Collectd : Default to help you started
    * Munin : script from R.I. Pienaar for front end as well as back end (munin-graphite)
    * Diamond : Mentionned, i don't know what peoples feedback was.
    * Jmx : maybe not that great (see above)
    * Statsd interface : available for a wide rage of programing languages, easy to plug to.
    * Bash / netcat : You can do a simple script to track some metrics and get the job done.


