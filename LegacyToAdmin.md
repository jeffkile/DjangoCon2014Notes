##Legacy to Admin
*Chris Cabral*

Do not write code unless you have to
If you are doing something hard with django then you are probably doing it wrong

#`inspectdb`
* Reads the tables and rows in our database and produces models.py
* Good For:
    - Building an admin onto a legacy DB


#Issues
* More tables than models
    - Because many to many relationships
* Multiple primary keys
    - Composite keys

#Proccess
* syncdb or inspectdb first?
    - `inspectdb` first
        - `./manage.py inspectdb > models.py`
        - `./manage.py syncdb`
    
#Gotchas
Fix these things in models.py;
* Auto increment fields turn into IntegerFields instead of AutoFields
* M2M with composite keys
    - Composite primary keys need to be turned into auto increment integer keys
    - Then add a validation check to the model to throw an error if a key is not present in other table
* If you give models.py to another developer
    - remove `class Meta: managed = False`
        - Then `syncdb` will create the tables`

