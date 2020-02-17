---
layout: post
title:  "Learning Prometheus"
date:   2020-02-16 16:25:34 -0600
published: false
categories: jekyll update
---
I started experimenting with [Prometheus][prometheus] for instrumentation of various micro-services, we've built for our system. [statsd][statsd]+[Graphite][graphite] is another instumentation solution I've used in the past. I am liking Prometheus a lot, but there were a few gotchas (for me) that I needed to keep in mind.

Key difference between statsd+Graphite and Prometheus, is the way metric data reaches the collector (in this case: Graphite or Prometheus).
  * Statsd uses UDP datagram to `push` data to the Graphite. While the recommended way for Prometheus is to let it "scrape" (or `pull`) data at a set interval from a HTTP-endpoint that the service exposes. Most commonly, this endpoint is named `/metrics` (but can be named anything else).
  * Another difference is the default frequency at which data is collected. Statsd by default sends data every 10 seconds, while Prometheus's scrape frequency is 1 minute.

Since, I brought up Prometheus using Docker container and its default configuration, this 2nd difference tripped me up for a while before I realized why my Prometheus queries were not returning any data.

I was collecting request latency in a Histogram called `request_latency_secs`. After running a few tests I curl'd the `/metrics` endpoint and could see the histogram data being populated. Everything looked good so far.


Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[prometheus]: https://prometheus.io/
[statsd]: https://github.com/statsd/statsd
[graphite]: https://graphiteapp.org/
