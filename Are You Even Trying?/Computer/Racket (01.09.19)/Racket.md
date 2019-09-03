# Racket 

> for whom the Racket tutorial needed for, Click this link: https://docs.racket-lang.org/plait/index.html 

> All the data below are referenced from:  https://docs.racket-lang.org/plait/index.html

[Purpose]

1. I've been learning this program for PL class.

2. And I wanted to know what the PL course academically mean, and why we should know more about that subject is.


[목차]


## Something new you got from learning how to used this PGM.

## Tutorial

### 1.1 Getiing started 

-In a few places, the tutorial shows lines that include a semicolon, ;. A semicolon starts a comment that continues to the end of the line.

### 1.2 Simple Data

-Strings are written the usual way with a starting and ending ":

-In addition to strings, Plait includes string-like values called symbols. A symbol is written with a single quote ' followed by a sequence of non-whitespace characters.

-Individual characters are infrequently used in Plait, but they’re written with #\:


### 1.3 Using Built-in Functions

-Plait includes some of the usual functions on numbers, like floor and max.

-The parenthesis must be before the function, not after. Don’t use commas between arguments. ex) (max (3) 5) -> X

-The same error happens if you add parentheses around the call to max, since the result of max is a number: ex) ((max 3 5)) -> X
-so if you evaluate just max without calling it, then Plait will show the type and print that the result is a procedure (which is synonymous with “function” in Plait)

-If you try to put the operator-as-function in the middle of its arguments, Plait will complain that the first argument isn’t a function, because the opening parenthesis means that first thing in the parenthesis should be a function to call

-The style of syntax that puts a function/operation name up front and grouped with its arguments in parentheses is called parenthesized prefix notation.

(ex) 
-> (not #t)
- Boolean

#f

> (not #f)
- Boolean

#t

> (+ 1 2)
- Number

3

> (- 1 2)
- Number

-1

> (* 1 2)
- Number

2

> (< 1 2)
- Boolean

#t

> (> 1 2)
- Boolean

#f

> (= 1 2)
- Boolean

#f

> (<= 1 2)
- Boolean

#t

> (>= 1 2)
- Boolean

#f

> (string-append "a" "b")
- String

"ab"

> (string=? "a" "b")
- Boolean

#f

> (string-ref "a" 0)
- Char

#\a

> (string=? "apple" (string-append "a" "pple"))
- Boolean

#t

> (equal? "apple" (string-append "a" "pple"))
- Boolean

#t

> (eq? 'apple 'apple)
- Boolean

#t

> (eq? 'apple 'orange)
- Boolean

#f

### 1.4 Conditionals

-The line breaks above don’t matter to Plait, but readers of your programs will appreciate it if you normally put the “then” and “else” branches on their own lines and correctly intent them. 

-The cond form is a multi-way if

-The cond form tries the clauses in order, and as soon as it finds a true result from a question, it produces the corresponding result. The last clause’s question cal be else as a synonym for #t.

ex) 

> (cond
    [(< 2 1) (/ 1 0)] ; result expression skipped
    [(> 2 1) 18])
- Number
18

> (cond
    [#t 8]
    [#t (/ 1 0)]) ; second clause not reached
- Number
8

-Plait doesn’t distinguish between square brackets [ and ] and parentheses ( and ), as long as each opener and closer match.
-You could use parentheses instead of square brackets in the above examples—but don’t. __Plait programmers should use square brackets in specific places by convention to make programs more readable. Follow the conventions that you see in this tutorial.__

ex)

> (cond
    [(< 3 1) 0]
    [(< 3 2) 1]
    [(< 3 3) 2]
    [(< 3 4) 3])
- Number
3

-The and and or forms are short-cicuiting, too, and they work with any number of boolean subexpressions: (Finding True)

ex)

> (and #t #t)
- Boolean

#t

> (and #t #f)
- Boolean

#f

> (and (< 2 1) #t)
- Boolean

#f

> (and (< 2 1) (zero? (/ 1 0))) ; second expression is not evaluated
- Boolean

#f

> (or #f #t)
- Boolean

#t

> (or #f #f)
- Boolean

#f

> (or (< 1 2) (zero? (/ 1 0))) ; second expression is not evaluated
- Boolean

#t

> (and #t #t #t #t)
- Boolean

#t

> (or #f #f #f)
- Boolean

#f

*** > (or (< 2 1) (zero? (/ 1 0)))
. . /: division by zero [error]
> (and (< 2 1) (zero? (/ 1 0)))
#f
> (and (zero? (/ 1 0) (< 2 1)))
. . /: division by zero [error]

__We can learn the lesson from above codes,__

__1. (zero? (/ 1 0) ==> this cannot be divied by zero__

__2. even thought that, the result was #f (false), but why? because 'and' is a function to return the false if there's false statement like (and (< 2 1)). because first argument is arleady false, so rest of statement doesn't need to be checked__

### 1.5 Lists

-Plait lists are uniform, meaning that all of the elements of a list must have the same type. The list form creates a list:

ex)

> (list 1 2 (+ 3 4))
- (Listof Number)

'(1 2 7)

> (list (string-append "a" "b") "c")
- (Listof String)

'("ab" "c")

- The cons function takes an element and a list and “adds” the element to the front of the list, creating a new list with all of the elements:

ex)

> (cons 1 '(2 3))
- (Listof Number)

'(1 2 3)

> (cons "apple" '("banana"))
- (Listof String)

'("apple" "banana")

__*how to read?__

__Symbol: milk__

__String: "milk"__

__number: 1__

- The expression '(1 2 (+ 3 4)) fails because that’s the same as (list 1 2 '(+ 3 4)), and '(+ 3 4) fails because it’s the same as (list '+ 3 4), but a list cannot mix a symbol with numbers.

-The cons operation is constant-time, because a list is internally represented as a singly linked list, and cons simply creates a new cell that contains the new value and then points to the existing list.

ex)

> (cons 1 '(2 3))
- (Listof Number)

'(1 2 3)

> (cons "apple" '("banana"))
- (Listof String)

'("apple" "banana")

-__Don’t confuse cons and append. The cons function takes an element and a list, while append takes a list and a list. That difference is reflected in their types:__

ex)

> (append '(1 2) '(3 4))
- (Listof Number)

'(1 2 3 4)

-The empty list is so useful that it has a name: empty. Although the list form may seem fundamental, the true list-construction primitives are empty and cons, and you can build up any other list using those:

ex)

> empty
- (Listof 'a)

'()

> (cons "food" empty)
- (Listof String)

__;empty '()__

__;that is, put the element ("food") into empty(list -> '())__

'("food")

> (cons "dog" (cons "food" empty))
- (Listof String)

'("dog" "food")

-The empty? function determines whether a list is empty, and cons? determines whether a list has at least one item:

ex)

> (empty? empty)
- Boolean

#t

> (empty? '())
- Boolean

#t

> (cons? (cons 1 '()))
- Boolean

#t

> (cons? '(1))
- Boolean

#t

> (cons? empty)
- Boolean

#f

> (empty? '(1))
- Boolean

#f

-The cons operation constructs a new value from two pieces. The first and rest operations are the opposite of cons. Given a value produced by cons, first returns the item that cons added to the start of the list, and rest returns the list that cons added to. More generally, first gets the first item from a list, and rest gets everything list in the list when the first argument is removed.

ex)

> (first (cons 1 '(2 3)))
- Number

1

> (rest (cons 1 '(2 3)))
- (Listof Number)

'(2 3)

> (first '("apple" "banana" "coconut"))
- String

"apple"

> (rest '("apple" "banana" "coconut"))
- (Listof String)

'("banana" "coconut")

> (first (rest '("apple" "banana" "coconut")))
- String

"banana"

> (rest (rest '("apple" "banana" "coconut")))
- (Listof String)

'("coconut")


### 1.6 Definitions

The define form defines an identifier to be a synonym for a value:

ex)

> (define pi 3.14)
> pi
- Number

3.14

> (define tau (+ pi pi))
> tau
- Number

6.28


The define form can also define a function. The difference is that define for a function definition is followed by an open parenthesis,

> (define (circle-area r)
    (* pi (* r r)))
> (circle-area 10)
- Number

314.0

we have been evaluating forms only in DrRacket’s bottom area, which is also known as the interactions area. Definitions normally go in the top area—which is known as the definitions area, naturally.


(define (is-odd? x)
  (if (zero? x)
      #f
      (is-even? (- x 1))))
 
(define (is-even? x)
  (if (zero? x)
      #t
      (is-odd? (- x 1))))
      
Click Run. The functions is-odd? and is-even? are now available in the interactions area:

> is-odd?
- (Number -> Boolean)

#<procedure:is-odd?>

> (is-odd? 12)
- Boolean

#f


-------------------------read again below---------------------

In our definitions of pi and tau, plait inferred that the newly defined names have type Number and that is-odd? has type (Number -> Boolean). Programs are often easier to read and understand if you write explicitly the type that would otherwise be inferred. Declaring types can sometimes help improve or localize error messages when Plait’s attempt to infer a type fails, since inference can other end up depending on the whole program.

Declare a type for a constant by writing : followed by a type after the defined identifier:

(define groceries : (Listof String) '("milk" "cookies"))
Alternatively, you can declare an idenitifier’s type separate from its definition by using :.

(groceries : (Listof String))
(define groceries '("milk" "cookies"))
The declaration can appear before or after the definition, as long as it is in the same layer of declarations as the definition. You can even have multiple type definitions for the same identifier, and the type checker will ensure that they’re all consistent.

For a function, attach a type to an argument by writing square brackets around the argument name, :, and a type. Write the function’s result type with : and the type after the parentheses that group the function name with its arguments.

(define (starts-milk? [items : (Listof String)]) : Boolean
  (equal? (first items) "milk"))
Or, of course, declare the type separately:

(starts-milk? : ((Listof String) -> Boolean))
(define (starts-milk? items)
  (equal? (first items) "milk"))


-------------------------read again avobe---------------------








###

## Something still confused when you studying this PGM.




