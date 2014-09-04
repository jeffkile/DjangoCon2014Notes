##High Performance Django



Django does not scale

Instagram, pintrest and disqus, are not actually using Django


#Tools
* Fig
    - Manages docker sessions
* JMeter
    - Like Apache Bench
    - Site traffic testing
    - Jenkins has a JMeter plugin
    - `brew install jmeter`
    - Do load testing from inside the same network of the app server


#uWSGI
* Can specify number of processes
* 72% faster than just `runserver.py`

#Multiple Servers
* NGNX as a proxy
    - Could use Elastic Load Balancer instead
    - NGNX can speak uWSGI's internally protocol, which has slightly better performance
* Continuing to add servers pushes the load problem down the stack
    - Then the DB will be the bottleneck

#Cache using Varnish
    - Serves part of page with cache
    - Good for content sites
    - Cache static pages 
    - Can continue hosting content when django goes down
    - CSRF token must be unique
        - Don't use URLs to determine which pages to cache


