##Activating your site
#Activity Streams

People like contributing.

People like seeing what others are doing.

Activity streams are newsfeeds

#Activity Stream Specification
* "Actor", "verb", "object", "target", "timestamp"
* JSON


#Django Activity Streams
* Implements many common activity stream operations like:
    - following/followers
    - Newsfeed
    - Built in API
* Can be installed on your site using activity_stream

#Horizon
* Uses a graph database
    - Neo4j
    - Property Graphs
        - Doubly linked list under the hood
            - Search O(n), insert and delete O(1)
#Caching
* Redis
* Pre-Computation
    - Storm
        - Distributed processing framework
        - Like Hadoop
* Built on Node and Sails

#Frontend
* Snipptes
* Use local storage for front end caching
* Uses ajax and websockets


#Different Services
*Each has its own github project
    - Django activity streams
        - django-activity-stream
    - Modules
        -modules-activitystream
    - activitystreams
    - Activity streams
        - node service

