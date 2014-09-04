##A Related Matter
#Optimizing your webapp by using djang-debug-toolbar, select_related() and prefetch_related()
*Christopher Adams*


https://github.com/adamsc64/a-related-matter


#Django ORM
* Abstraction layer


#Queryset
* Lazy
    - Do not evaluate until it needs to
    - Can cause queries to happen from a template
        - example: `comment.submitter.username`
* Immutable
    - Just applying .filter to a queryset does not require access to DB


#Django Debug Toolbar
* Tells you the number of queries for each page

#`select_related()`
* Works by creating a sql join and including the related fields in the SELECT statement
* One to Many or One to One relationships

#`prefetch_related()`
* Does a seperate lookup for each relationship and does the "joining" in python
* Many to Many or Many to One

#Can chain them
*Queryset.select_related().prefetch_related()
