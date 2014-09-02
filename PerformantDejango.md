Performant Django


Start with the front end
80-90% of user response time is spent in the frontend


Front End
---------

* Cache Static Assets 
    * Forever (as long as they do not change)
    * Use:
        - CachedStaticFilesStorage or CachedFilesMixin
            - Built into Django
            - They change file name
            - Works with S3 or other storage
                - Do not have to store files through django
            - Checks hash of file to see if its changed
                - Uses Memcache to make this fast

* Bundle/minify/compress static assests
    * Reduce # of requests, download time
    * Use a static-asset-manager 2 good ones:
        - django-pipline
        - webassets
    * Lower number of requests by using data URIs for images
        - Pipeline does this automatically for small files

* Serve static files via a CDN
    
* Serve more stuff as static assets
    * Why?
        - So they can be cached
    * Examples of things to serve:
        - Front end templates (angular templates)
        - JSON data


Back End
--------

* Cached Sessions
    - `contrib.session.backends.cache`

* Use cached template loader
    - If not on by default

* Jinja2 as template engine
    - Best for new projects, hard to transition to 


Tools
-----

* Backend Profiler:
    - Middleware
    - (link in slides to a good one)
    - Displays: 
        - What function/modules were called
        - How much time was spent in each function
        - SQL time
        - Python time

* New Relic


SQL
---

* django-debug-toolbar
    - Shows slow queries
    - Does not show SQL for queries that just return JSON
    
* Query to slow
    - `values/values_list()`
        - Avoid python object creation overhead when you want a dict or list
    - `only()`
        - Only grab the fields in the model you need
        - Use with caution!
            - Can become much slower if someone tries to access a field not included in the only
    - `defer()`
        - Get all fields except those in defer()
        - Opposite of only

* Too many quires
    - `select_related()`
        - Helps avoid extra queries to grab objects referenced by foreign keys
    - `prefetch_related()`
        - Like `select_related` except the "join" is done in Python and thus works for M2M
    - `bulk_create()`
        - Do one insert instead of multiple

* Redis or Memcache may be better for searching or using lists or key/value store


Python
------

* Algorithms
    - Nested loops

* Doing extra work inside a loop
    - Do not do computations or create variables inside a loop that you can do outside it


Django
______

* `decimal('0.1')` is used a lot and it is slow
    - use DECIMAL_POINT_ONE = decimal('0.1') if you need this in a loop

* `reverse()` is slow
    - Do not call it in a loop
        - Use string replace if you have to do this


Cache
-----

* View Cache

* Template fragment cache

* Function level cache
    - django-cache-utils
    - django-cache-helper
        - Decorator

* Query cache
    - django-cache-machine
    - django-cacheops


