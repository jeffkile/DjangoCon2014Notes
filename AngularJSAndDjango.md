##AngularJS + Django = A Perfect Match
*Nina Zakharenko*

Used by reddit on their internal tools

Sample app: github.com/nnja/tweeter


#Problems with django templates
* Need to refresh page to submit form
* Difficult to unit tests
* Slow
* Hard to add JS
* Forms get complex fast
    - Speggetti code
* Front end Devs need to learn back end templating


#Why endpoints are better
* Faster
* Swap FE frameworks
    - Angular, React, Backbone
    - Choosing a JS framework: http://brianholt.me/
* Dogfooding
    - Before exposing public API you can consume it internally 
* Front end devs know how to use APIs already


#Why angular
* MVC
* Single Page App
* Scope
    - Variables well bounded
    - "Automagically" update
* Easy to Unit Test
* Javascript
    - Language of the web


#API Endpoints
* Django Rest Framework
    - serializers.py, permissions.py, routers.py
    - Browsable api
        - `localhost:8000/api`
        - Test all endpoints with all http methods
* Example endpoint:
    `/api/tweets`


#Angular
* Can be used on just part of the app in a div
    - using `ng-app`
* Angular tags and Django tags conflict
    - Both use `{{ }}`
    - Tell Angular to use a different kind of tag
        - use `[[ ]]` instead of `{{ }}`
        - static/js/app/js
            - `interpolateProvider.startSymtbol('[[').endSymbol(']]')`
    - Config CSRF tokens
        - `httpProvider.defaults,xsrfHeaderNAme ='csrftoken'`
        - `httpProvider.defaults,xsrfHeaderNAme ='X-CSRFToken'`
    - Do not strip trailing slashes
        - Trailing slashes are used heavily by Django
        - `resourceProvider.defaults.stripTrailingSlashes = false;`
* You can send django data from django to angular via an angular template without the api:
    - `angular.module(tweetApp.services).factory(function() return {{user.id}})`
* Testing frameworks:
    - Selenium, Jasmine 

