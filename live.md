# GOV.UK Colophon

The GOV.UK Colophon is a large, but not exhaustive, list of the key components,
tools and services which have been used during the construction of GOV.UK. The
tools we use have changed over time, and we hope that this Git repository allows
you to chart them.

We started the colophon on October 17th 2012, when GOV.UK took over from
Directgov and Businesslink as the best place to find government services and
information. By looking at the commit history on this file, you'll be able to
see exactly which tools we've introduced since launch.

During the [alpha](https://gds.blog.gov.uk/colophon-alpha/) and
[beta](https://gds.blog.gov.uk/colophon-beta/) phases of GOV.UK, we compiled
similar lists. They chart, from a tooling perspective, the site's progress over
time.

### Frontend:

  * HTML/CSS/JS - using HTML5 where appropriate, with a heavy focus on accessibility, and validating where we can
  * We use [jquery](http://en.wikipedia.org/wiki/Jquery) as our primary javascript library
  * Video playback with the [Nomensa Accessible Media Player](https://github.com/nomensa/Accessible-Media-Player)
  * Backend admin systems make use of [Twitter Bootstrap](http://twitter.github.com/bootstrap/)
  * We use [SCSS](http://en.wikipedia.org/wiki/Scss), as seen in [our frontend toolkit](https://github.com/alphagov/govuk_frontend_toolkit)
  * We’ve worked with [A2-Type for font production](http://www.a2-type.co.uk/).

### Infrastructure:

  * We’re making use of [Infrastructure-as-a-Service](http://digital.cabinetoffice.gov.uk/2012/09/25/why-iaas/) from [Skyscape](http://digital.cabinetoffice.gov.uk/2012/09/18/introducing-a-new-supplier-skyscape/)
  * [Fastly](http://www.fastly.com) are our [content delivery](http://en.wikipedia.org/wiki/Content_Delivery_Network) provider
  * We cache requests using [Varnish](http://en.wikipedia.org/wiki/Varnish_(software))
  * We load-balance internally with [HAProxy](http://haproxy.1wt.eu).
  * Our servers are running [Ubuntu GNU/Linux 12.04](http://en.wikipedia.org/wiki/Ubuntu_(operating_system))
  * Servers are managed with [Puppet](http://en.wikipedia.org/wiki/Puppet_(software)). We also rely on PuppetDB, librarian-puppet and Hiera.
  * Web traffic is served by [Nginx](http://en.wikipedia.org/wiki/Nginx) which proxies to [Unicorn](http://unicorn.bogomips.org/) for our Ruby applications.
  * [gUnicorn](http://www.gunicorn.org) is used to run some supporting services, and [one of the team](https://github.com/nickstenning) wrote [Unicorn Herder](https://github.com/alphagov/unicornherder) to make Unicorn work nicely with [Upstart](http://en.wikipedia.org/wiki/Upstart).

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

  * We gather metrics from our applications using [statsd](https://github.com/etsy/statsd)
  * [Grafana](https://github.com/alphagov/grafana), a Graphite frontend, helps us graph our infrastructure and apps to understand what's going on 
  * We collect logs with [Logstash](http://logstash.net), which we pipe in to [Elasticsearch](http://elasticsearch.org), and collate using [Kibana](http://elasticsearch.org/overview/kibana).
  * We monitor systems with [Icinga](http://www.icinga.org), and use [Blinken](https://github.com/alphagov/blinken) tells us if we need to act on any of that data

### Supporting Tools:

  * All our code is tested by [Jenkins](http://en.wikipedia.org/wiki/Jenkins_(software)), which we also use to deploy it to servers
  * We track usage of the site with Google Analytics, using their API heavily to build dashboards
  * We expose GOV.UK's performance data to the world through the [Performance Platform](https://www.gov.uk/performance/dashboard).
  * DNS is hosted by [Dyn](http://www.dyn.com) and [Janet](http://www.ja.net]
  * Email (internal alerts) sending via [Amazon SES](http://aws.amazon.com/ses/)
  * Font handling and preparation with [FontForge](http://fontforge.org/) and [FontTools](http://sourceforge.net/projects/fonttools/)
  * We keep on track and in touch using Google Apps, Pivotal Tracker and Campfire
  * Github helps us manage and discuss our code
  * Zendesk keeps the feedback flowing
  * We use [jekyll](http://jekyllrb.com/) &amp; [heroku](http://www.heroku.com/) for some of our prototyping
  * We’ve built all sorts of internal dashboards. They’re very much our playground and you can find them written in a mixture of Ruby, [Clojure, Node.JS, and PHP](http://digital.cabinetoffice.gov.uk/2012/02/08/radiating-information/)
