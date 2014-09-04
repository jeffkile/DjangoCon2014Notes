##The evolution of a RESTful Django backend
*Andrew Brookings*


Django REST API Evaluation


#Plain Django Views
* Pros
    - Easy to return html or read only json
* Cons
    - Lots of boilerplate
    - Serialization
    - Multiple views for different content types


#Piston
* Pros
    - Get a quick API up and running
* Cons
    - No longer being maintained
    - No Pagination
    - Hard to serialize


#TastyPie
* Pros
    - Pagination
    - Serialization better
    - Built in schema generation that clients can use
    - Sets up urls for you
* Cons
    - Poor handling of binary types
    - Monolithic API class
    - "Too much magic"


#Django Rest Framework
* Pros
    - Very well documented
        - Creator on Stack Overflow
    - HTTP REST API browser
    - Out of the box pagination and filtering
    - Supports token auth
    - Calls `model.full_clean()` during object creation 
        - Can do validation here
* Cons
    - No built in schema generation


