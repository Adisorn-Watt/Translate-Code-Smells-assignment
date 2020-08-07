# Code Smells

## Bloaters 
Bloaters are code, methods and classes that have increased to such gargantuan proportions that they are hard to work with. Usually these smells do not crop up right away, rather they accumulate over time as the program evolves (and especially when nobody makes an effort to eradicate them).
+ Long Method
+ Large Class
+ Primitive Obsession
+ Long Parameter List
+ Data Clumps

## Object-Orientation Abusers
All these smells are incomplete or incorrect application of object-oriented programming principles.
+ Switch Statements
+ Temporary Field
+ Refused Bequest
+ Alternative Classes with Different Interfaces

## Change Preventers
These smells mean that if you need to change something in one place in your code, you have to make many changes in other places too. Program development becomes much more complicated and expensive as a result.
+ Divergent Change
+ Shotgun Surgery
+ Parallel Inheritance Hierarchies

## Dispensables
A dispensable is something pointless and unneeded whose absence would make the code cleaner, more efficient and easier to understand.
+ Comments
+ Duplicate Code
+ Lazy Class
+ Data Class
+ Dead Code
+ Speculative Generality

## Couplers
All the smells in this group contribute to excessive coupling between classes or show what happens if coupling is replaced by excessive delegation.
+ Feature Envy
+ Inappropriate Intimacy
+ Message Chains
+ Middle Man

## Other Smells
+ Incomplete Library Class
