Practical Django Security
Levi Gross


2 Main categories:

Laack of or improperly impelemnted
    -DOS
    -Auth bypass
    -Bad crypto primitives

Mixing data and code
    -SQL injection
    -XSS


Mixing Data and code:
Assert as much as possible - Assert all input from users to check its what you indended it to be

Prepared statements = Parameterized queries



Improperly Implemented Security Controls:

Put authorization code all in one place, do not scatter it


Django built in stuff:
Cryptoraphically sign:
    `django.core.crypto.signer`
Encode js:
    `{{foo|js_encode}}`


Django isn't perfect, things to update:
    Set PBKDF2 hasher iterations to 100,000


Put @login put it in urls.py not views.py - urls is easier to maintain
(may be not be possible in an async program)


In forms use an explicit list of fields, don't use exclude


To Encrypt things use KeyCzar - don't use anything else


Reading Material:
- The web application hacker's handbook (second edition) - Best book
- The tangled web
- Art of software security assessment
- Writing Secure code



Questions:
Set general rate limiting in NGNIX 
    If you need individual pages to have different limits then set it in django

Asyncrhonous Security
    Harder
    Banks don't use it because of race conditions

Trust and using assert:
    Create rules what a request can and cant do
    Be explicit of what should happen and why it should happen



