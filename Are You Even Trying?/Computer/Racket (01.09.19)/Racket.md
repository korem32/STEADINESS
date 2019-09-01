# Racket 

> for whom the Racket tutorial needed for, Click this link: https://docs.racket-lang.org/plait/index.html .
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





## Something still confused when you studying this PGM.




