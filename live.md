# GOV.UK Colophon

A large but not exhaustive list of the key components, tools and services that have gone into the construction of GOV.UK. The tools we use [will change and evolve over time](http://digital.cabinetoffice.gov.uk/2012/10/12/coding-in-the-open/) so this list represents the state of things on October 17th 2012 when GOV.UK takes over from Directgov and Businesslink. We prepared similar lists for [the alpha of GOV.UK](http://digital.cabinetoffice.gov.uk/colophon-alpha/) and [for the beta](http://digital.cabinetoffice.gov.uk/colophon-beta/) and hope to produce similar documents at key stages of the site’s evolution.

### Frontend:

  * HTML/CSS/JS - using HTML5 where appropriate, with a heavy focus on accessibility, and validating where we can
  * We use [jquery](http://en.wikipedia.org/wiki/Jquery) as our primary javascript library
  * Video playback with the [Nomensa Accessible Media Player](https://github.com/nomensa/Accessible-Media-Player)
  * Backend admin systems make use of [Twitter Bootstrap](http://twitter.github.com/bootstrap/)
  * We use [SCSS](http://en.wikipedia.org/wiki/Scss), as seen in [our frontend toolkit](https://github.com/alphagov/govuk_frontend_toolkit)
  * We’ve worked with [A2-Type for font production](http://www.a2-type.co.uk/).

### The core of the servers:

  * We’re making use of [Infrastructure As A Service](http://digital.cabinetoffice.gov.uk/2012/09/25/why-iaas/) from [Skyscape](http://digital.cabinetoffice.gov.uk/2012/09/18/introducing-a-new-supplier-skyscape/)
  * We use [Akamai](http://en.wikipedia.org/wiki/Akamai_Technologies) as our Content Delivery Network
  * Our servers are running [Ubuntu GNU/Linux 10.04](http://en.wikipedia.org/wiki/Ubuntu_(operating_system)), we’re hoping to upgrade to 12.04 soon.
  * Servers are managed with [Puppet](http://en.wikipedia.org/wiki/Puppet_(software)), using PuppetDB
  * Web serving is handled by [nginx](http://en.wikipedia.org/wiki/Nginx), proxying to [unicorn](http://unicorn.bogomips.org/) for our ruby applications. We’re also using [gunicorn](http://gunicorn.org/) to run some supporting services. One of the team wrote [Unicorn Herder](https://github.com/alphagov/unicornherder) to make Unicorn play nicely with [upstart](http://en.wikipedia.org/wiki/Upstart).
  * We load balance internally with [haproxy](http://haproxy.1wt.eu/) and cache requests using [Varnish](http://en.wikipedia.org/wiki/Varnish_(software))

### Redirection:

  * nginx deserves an extra mention as it’s [letting us do all our redirection](http://digital.cabinetoffice.gov.uk/2012/10/11/no-link-left-behind/)
  * we’re using [perl](http://www.perl.org) to manage and test our redirections
  * there’s some [php](http://en.wikipedia.org/wiki/Php) to add useful links to the “gone” pages where DirectGov and Businesslink content has been retired
  * [node.js](http://en.wikipedia.org/wiki/Node.js) was used to build a side-by-side browser for reviewing the redirections

### Applications:

  * The majority of our applications are written in [ruby](http://en.wikipedia.org/wiki/Ruby_(programming_language)), based on either [Ruby on Rails](http://en.wikipedia.org/wiki/Ruby_on_rails) or [Sinatra](http://en.wikipedia.org/wiki/Sinatra_(software)).
  * A few components are written in [Scala](http://en.wikipedia.org/wiki/Scala_(programming_language)) and built on top of [Play 2.0](http://www.playframework.org/)
  * We’re running [Mapit from MySociety](http://mapit.mysociety.org/) which is built on top of [Django](http://en.wikipedia.org/wiki/Django_(web_framework))

### Databases and other storage:

  * We use [MongoDB](http://en.wikipedia.org/wiki/Mongodb) for most systems, with a few apps also making use of [MySQL](http://en.wikipedia.org/wiki/Mysql). [PostgreSQL](http://en.wikipedia.org/wiki/Postgresql) is used by Mapit and Puppet.
  * Most search on the site is [powered by Elasticsearch](http://digital.cabinetoffice.gov.uk/2012/08/03/from-solr-to-elasticsearch/), though [solr](http://en.wikipedia.org/wiki/Solr) is currently the backend for the need-o-tron.
  * A few event-driven systems use [RabbitMQ](http://en.wikipedia.org/wiki/Rabbitmq)

### Monitoring, managing and alerting:

  * We gather metrics from our apps with[ statsd](https://github.com/etsy/statsd)
  * We collect logs with [logstash](http://logstash.net/)
  * We monitor systems with [ganglia](http://en.wikipedia.org/wiki/Ganglia_(software))
  * [Graphite](http://graphite.wikidot.com/start) helps us make many, many graphs to understand what’s going on
  * [Nagios](http://en.wikipedia.org/wiki/Nagios) tells us if we need to act on any of that data

### Supporting Tools:

  * All our code is tested by [Jenkins](http://en.wikipedia.org/wiki/Jenkins_(software)), which we also use to deploy it to servers
  * We track usage of the site with Google Analytics, using their API heavily to build dashboards
  * We occasionally use [New Relic RPM](http://en.wikipedia.org/wiki/New_Relic) for performance reviews
  * DNS is hosted by ja.net / Dyn
  * Email (internal alerts) sending via [Amazon SES](http://aws.amazon.com/ses/)
  * Font handling and preparation with [FontForge](http://fontforge.org/) and [FontTools](http://sourceforge.net/projects/fonttools/)
  * We keep on track and in touch using Google Apps, Pivotal Tracker and Campfire
  * Github helps us manage and discuss our code
  * Zendesk keeps the feedback flowing
  * We use [jekyll](http://jekyllrb.com/) &amp; [heroku](http://www.heroku.com/) for some of our prototyping
  * We’ve built all sorts of internal dashboards. They’re very much our playground and you can find them written in a mixture of Ruby, [Clojure, Node.JS, and PHP](http://digital.cabinetoffice.gov.uk/2012/02/08/radiating-information/)
