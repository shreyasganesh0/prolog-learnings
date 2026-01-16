# Sytnax

- made up 4 components atoms, numbers, variables and complex terms
    - these 4 are called terms
    - atoms and numbers are constants
    - constants + variables make up simple terms

## Atom
- of 3 types
    - a string of made of lower case letters, upper case letters, nubmers and underscore
        - big_butch2
    - a sequence of any characters enclosed in ''
        - '&dsfado(dfqwenf*(&(& &*(F'
    - a string of all special characters only
        - @===&*(
        - :- (has a predefined meaning)
## Numbers
- most support floats (1.23) but not that useful
- integers (-1, 2, 200342) are useful for tasks like counting elements of a list

## Variables
- string of uppercase lowercase digits or underscore
- start with either a captial letter or _
- just _ is a special variable called anonymous variable

## Complex terms
- built out of building blocks of constants, numbers and building blocks
- format: functor(arguments)
    - variables cant be used as functors
```
family(X,hide(hide(abc)))
```
- nested functors possible
    - recursive term structure
- number of args in a complex term is called arity
- different complex terms with different aritys and same functors are treated as different predicates
    - loves(a, b) and loves(x, y, z) are treated as two seperate predicates and will respond differently to
    queries about the facts they state (not related to each other)
