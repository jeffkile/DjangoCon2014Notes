#Inheriting a Sloppy Codebase
*A practical guide to wrangling chaotic code*
*Case Kinsey*

http://hireloft.com/djangocon14

Main cause of sloppy code is developing to fast.

Rapid Prototyping is a lie. In other forms of engineering prototypes are not used in production, they are thrown away and the production version is recreated from scratch.

Beta is just another word for "Prototype that went into production".

#Key Concepts
* Test first
* Dependencies Introduce Complexity
* Organization is important
* Watch for hidden... (get rest from slides)

#What you need to work on a sloppy codebase:
*A good editor (PyCharm)
    - Code navigation
    - Code introspection
    - Refactoring tools

*A good debugger (pdb)           
    - Integrate with text editor

*Coverage.py
    - Gives coverage report

*pep8
    -Integrate with text editor

#What to do when you first start looking at sloppy code base
Implement tests before starting on modifying the code
* Integration Tests
    - Make sure that changing something in one place does not break something someplace else
    - Not checking if data or rendering is correct, just making sure all requests are working
*Unit Tests
    - Goal is not yet full unit test coverage
        - Focus on core components where accuracy is critical
            - Billing processes
            - Transactional communication
            - Aysnchronous tasks
        - Shoot for 95% coverage
        - No files left untested

#Monoliths are an organizational nightmare
    - You cannot tell what depends on what
    - Spagetti Code
    - `import *`
        - pylint helps removing these

*Refactoring monoliths
    - Move models
        - Everything follows moving the models
    - Moving data
        - Checkout "how do I migrate a model out of one django app into another" on stack overflow

#Every model is an app
    - Functionality to distributed
    - Cyclical import

#Hidden Business Logic
* Recievers
    - Changing data in the ORM should not cause things to happen outside of the database
* Context Processors
* Middleware

#Undocumented code
* Document as you go
    - Make it policy
* Write a docstring for every
    - Function
    - Class
    - Module
    - Method
* Break apart long multi-step processes with comments

#Other Gotchas
* Hard coded urls
* Broad try/except blocks
* Rename badly named things
    - Rename things whose name changed to the end user
        - All stakeholders should use the same names for things

#Working with teams
* Have someone in a neutral position arbitrate refactoring decisions
    - Developers are opinionated
    - Sloppy code is code someone else wrote
    - Leadership is important
