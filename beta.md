# GOV.UK Beta Colophon

We’ve been cataloguing the technologies and tools we’ve used in producing the
beta of GOV.UK. Naturally our technology stack is always evolving, but this
list captures its state at the moment when the beta was released. You can see
[the equivalent list for alpha.gov.uk here](/colophon-alpha).

We’ll be updating this post with links to more detailed blog entries on
various tools and technologies over the coming days.

### Hosting and Infrastructure

  * DNS hosted by Dyn.com
  * [Servers are Amazon EC2 instances running Ubuntu 10.04LTS](/2012/01/24/hosting-the-beta-of-gov-uk/)
  * Email (internal alerts) sending via Amazon SES and Gmail
  * Miscellaneous file storage on Amazon S3
  * Jetty application server
  * Nginx, Apache and mod_passenger
  * Jenkins continuous integration server
  * Caching by Varnish
  * Configuration management using Puppet

### Languages, Frameworks and Plugins

  * Most of the application code is written in Ruby, running on a mixture of Rails and Sinatra  
Rails and Sinatra gave us the right balance of productivity and clean code,
and were well known to the team we’ve assembled. We’ve used a range of gems
along with these, full details of which can be found in the Gemfiles at
[https://github.com/alphagov](https://github.com/alphagov)

  * The router is written in Scala and uses Scalatra for its internal API  
The router distributes requests to the appropriate backend apps, allowing us
to keep individual apps very focussed on a particular problem without exposing
that to visitors. We did a bake-off between a ruby implementation and a scala
implementation and were convinced that the scala version was better able to
handle the high level of concurrency this app will require.

### Databases

  * MongoDB  
We started out building everything using MySQL but moved to MongoDB as we
realised how much of our content fitted its document-centric approach. Over
time we’ve been more and more impressed with it and expect to increase our
usage of it in the future.

  * MySQL hosted using Amazon’s RDS platform  
Some of the data we need to store is still essentially relational and we use
MySQL to store that. Amazon RDS takes away many of the scaling and resilience
concerns we had with that without requiring changes to our application code.

  * [MaPit geocoding and information service from mySociety](http://mapit.mysociety.org/)  
MaPit not only does conventional geocoding (what’s the lon/lat for a postcode)
but also gives us details of all the local government areas a postcode is in,
which lets us point visitors to relevant local services

### Frontend

  * HTML &amp; CSS (naturally), with elements from HTML5 &amp; CSS3 where appropriate
  * Javascript uses jQuery, jQuery UI, Chosen, and a variety of other plugins
  * Gill Sans provided by fonts.com
  * Google web font loader

### Misc

  * Accessibility testing with [Jaws, NVDA, VoiceOver, Window Eyes, and a range of other tools](https://www.gov.uk/support/accessibility).
  * Video playback with the [Nomensa Accessible Media Player](https://github.com/nomensa/Accessible-Media-Player)
  * [Dashboards/Information Radiators in Clojure, Node.JS, and PHP](http://digital.cabinetoffice.gov.uk/2012/02/08/radiating-information/)
  * Campfire for team chat
  * Google Apps
  * MediaWiki
  * Pivotal Tracker
  * Many, many index cards

* * *

_James Stewart is Tech Lead on the beta of GOV.UK. You can follow
[@jystewart](http://twitter.com/jystewart) on Twitter_
