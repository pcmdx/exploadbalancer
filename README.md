# Introduction #

ExploadBalancer is a simple web page that given a list of URLs will redirect to the fastest URL to return a 200. This is useful as a simple load balancer if your environment has several instances without a managed load balancer.

# Quick Start #

### Required ###

1. Download exploadbalancer.html
2. Configure multiple targets (label is for Google Analytics):
~~~~
    {'url':'http://server1.mysite.com/', 'label':'server1'},
    {'url':'http://server2.mysite.com/', 'label':'server2'},
    {'url':'http://server3.mysite.com/', 'label':'server3'}
~~~~
3. Upload it your web entry point (i.e. www.mysite.com/index.html)

### Optional ###

4. Set googleAnalyticsTrackingCode if you want Analytics on target selection
~~~~
var googleAnalyticsTrackingCode = null; // OR 'UA-XXXXXXXXX-1';
~~~~
5. Set fading colours just for fun (and very slow loading)
~~~~
var colors = ['#ffffff', '#65bc55', '#199dd7'];
~~~~

# Why #
> This is stupid, you should just use X

This is probably true; there's *lots* of excellent options, including paid traffic management services, load balancers built into auto-scaling from your friendly cloud provider, or dedicated open source hardware/software.

### However, ExploadBalancer has some advantages ###

1. It can be hosted almost anywhere, including AWS S3, CDNs and locally
2. Configuration is trivial -- perfect for crisis moments
3. It is completely straightforward in operation

# Technical Details #

### How does it work? ###

It asynchronously loads the URLs provided and then redirects the browser to the one that loads fastest. The async calls are looking for a HTTP 200, which means any URL returning content from a GET will work.

It could optionally use a more complicated test page, which returns 200 upon a database call or other environmental conditions you set (i.e. load).

### What's the point of Google Analytics? ###

It acts as a form of logging, by sending the redirect as a 'page load' event to Google Analytics, so you can track what is being redirected to most frequently and when.

# Contact / Get Involved

This is an early project; please provide pull requests and issues!
