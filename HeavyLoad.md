##A Nice Problemto Have: Django Under Heavy Load
*Joshua Ginsberg*

#Drinking form the Firehose
* Handle fewer requests
    - Downstream cache is better than upstream cache
* Ask fewer questions during requests
    - select_related, select_prefetch_related
* Answer fewer questions during
    - Indexes
    - Multiple kinds of data stores
    - Shared
* Increase concurrency
    - Switch to evented I/O
* Offload to client
    - Template rendering code
    - 100ms page load reduction inceased sales 4% at match.com


#Measure everything
* New relic
* Statsd
    - Track and graph key performance indicators
* SQL Statistics analysis
    - Postgres
        - `select * from pg_stat_activity`


#Scalpel instead of sledgehammer
* Elastic search to search instead of SQL
* Columnar for aggregation
* Key object for single record lookup
* Must be able to test any changes

#Risk Analysis and Disaster Migration
* Every new subsystem adds complexity and risk
* Use solutions other have tested and rely on


#Database
* `select_related` and `prefetch_related`
* Django 1.7 allows multi_column joins
* Multi-column Indexes
    - Must be created in SQL or through migration, no Django syntax
* More indexes means slower writes and thus possibly more locks
* Use query planner - Explain
    - Can be done in the dbshell
* Where constraint without an index is an entire table scan
* Tune database
    - Nobody should use default settings
    - Sort and Join may be done on disk which is slow
        - Research how DB engine runs queries
* Sharding
    - Do not do cross-shard queries 


#SQL
* Not good at:
    - Agrigtation
    - Search
    - Single Record Access
    - Highly Dimensional Data
    - Graph Traversal
* Alternate datastore should be derived datastore
     - Need a single point of truth

#Downstream caching
* Return 304 in views when you know content has not changed
* Use Redis to track modification timestamps



