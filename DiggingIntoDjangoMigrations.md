##Digging Into Django Migrations
*Andrew Godwin*

#History of South
* 0.1 Aug 2008
* 1.0 July 2014
* Became "Migrations" in Django 1.7
    - Migrations was written from scratch

#Django Migrations in 1.7
* Schema Backend
* ORM Hooks
* Migration Handling
* User Interface

* Schema
    - Schema Editor
    - field.deconstruct()
    - ModelOptions.apps
* Migrations
    - Operations
    - Loader / Graph
    - Executor
    - Autodetector
    - Optimiser
    _ State

#Available Migration Commands 
* `AddModel`
* `DeleteModel`
* `RenameModel`
* `AddField`
* `DeleteField`
* `AlterModelOptions`
* `RenatmField`
* `AlterModelTable`
* `AlterField`
* `AlterUniqueTogether`
* `AlterIndexTogether`
* `RunSQL`
* `RunPython`


#Advantages of Migrations over South
* Faster
    - Optimiser looks for fastest way to execute commands
* Simpler
    - No need for frozen ORM at the end of migration file
    - Easy to make small or large changes

#Notes
* With master and replica DB setup
    - Only run migrations on master
* Swap migrations
    - Built in command
    - Get rid of all your old migrations

