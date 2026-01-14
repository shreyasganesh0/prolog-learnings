# Introduction

## Facts Rules and Queries
- 3 basic constructs (facts rules queries)
    - collection of facts and rules is called a knowledge/database
    - prolog programming is creating knowledgebases
    - use the knowledgebase by posing queries

### Knowledge Bases
- knowledge bases collections of facts
    - facts are things that are always true
     ```
    woman(a)
    woman(b)
    playsDrums(a)
    ```
    - in this example a and b are stated to be
    women and a plays drums
    - written in the form of property(name) 
    with names and properties starting with lowercase
- once we have a fact we can use it by posing a query
    ```
    ?- woman(a)
    ```
    - prolog will answer yes
    ```
    ?- playsDrums(b)
    ```
    - answer will be no
    - if the property or name is unknown in the query
    then we will get a "no" reponse

- rules imply conditionality
    ```
    listensToMusic(a) :- happy(a)
    ```
    - the :- reads as "if"
        - a listens to music IF a is happy
    - rules in the format
        - head :- body
        - the body is information present in previous
        parts of the KB
        - the head can be infered since it always follows the body
    - so if we do
    ```
    happy(a)
    listensToMusic(a) :- happy(a)
    ```
    - even tho listensToMusic(a) was never mentioned as fact in the KB
    the fact can be infered so 
    ```
    ?- listensToMusic(a)
    ```
    - prolog will return yes since it can infer it from happy(a) fact
    - facts and rules are known as clauses
    - properites can also be seen a predicates
        - a predicate here would be listensToMusic
        - predicates are defined by the clauses
    - facts can be viewed as degenerate rules (no preceeding requirment/body)
    ```
    playsGuitar(c) :- listensToMusic(c), happy(c)
    ```
    - the , here represents logical and i.e. both GOALS must be true
    ```
    playsGuitar(c) :- listensToMusic(c); happy(c)
    ```
    - the ; can be used as logical or
    - infering answer from one true predicate is called modus ponens (mode of confirmation)
- variables
    ```
    woman(a).
    woman(b).
    woman(d).

    loves(d,a).
    ```
    - the , can be used for the names as well inside the fact
    - if we pose the question
    ```
    ?- woman(X)
    ```
    - here X is capital indicating that it is a variable
    - prolog will bind X to the first fact that validates the predicate
        - X bound to a (X = a)
    ```
    ?- ;
    ```
    - this asks are there any more women since ; is or
    - it will print X = b
    - if all matches are done after pressing ; 2 more times it will print no
    
    ```
    ?- loves(d, X),woman(X).
    ```
    - query asks if there is anyone who is a woman and loves d
        - will print X = a cos it satisfies both predicates
    - this is the main part of prologs abilities **Varible Matching**
- variables can be used in KBs
    ```
    loves(a, b)
    loves(b, c)
    jealous(X, Z) :- loves(X, Y),loves(Y, Z).
    ```
    - here if we do 
    ```
    ?- jealous(a, W)
    ```
    - prolog will infer that the person a is jealous of is c
        - W = c
