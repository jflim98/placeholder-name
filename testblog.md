# The What, How, and Why of Y
Copied from https://martin-henz.github.io/martin-henz/2022/02/17/the_y_combinator_explained_with_javascript.html
## The What of Y
The following JavaScript expression is called the _applicative-order Y combinator_.
```source
const Y = f => (g => g(g))(g => f(y => g(g)(y)));
```
What is interesting about this incomprehensible mess of lambda expressions, which includes something as strange as g(g) not once but twice?

The first Y combinators were conceived by [Haskell Curry](https://en.wikipedia.org/wiki/Haskell_Curry) to show that a minimal language (called the lambda calculus) consisting just of 
expressions `E` of the forms `x => E` (that we call here lambda abstraction) and E1(E2) (function application) in principle suffices to 
express every algorithm. More specifically, the applicative-order Y combinator allows us to express recursive algorithms in a sublanguage 
of JavaScript that does not include declarations. Take for example the factorial function, and recall `factorial(5) = 5 * 4 * 3 * 2 * 1 = 120`. 
Using the applicative-order Y combinator as Y, we can compute `factorial(5)` as follows:

```source
// change 5 to validate that it is indeed the factorial function!
Y(given_fact => n => n <= 1 ? 1 : n * given_fact(n - 1))(5);
```
## The How of Y
But how does this Y applicative-order combinator achieve this? The property needed in a language that uses applicative-order reduction, 
such as JavaScript and most other popular programming languages, is as follows: An application `Y(f)` where `f` is a lambda abstraction should 
lead after some function applications to a lambda abstraction `E` such that `E(x)` leads to `f(E)(x)`. If Y has this property, we can compute `5!` 
by applying `Y` to the following function as `f`:
```source
const f = given_fact => n => n <= 1 ? 1 : n * given_fact(n - 1);
```
Now `Y(f)(5)` leads to `f(E)(5)`, and the recursive call `given_fact(5 - 1)` in f will become `E(5 - 1)`, which will become `f(E)(4)`, and so on, 
until we reach the base case `n <= 1`, which leads to 1 and `E` is no more needed. Then we only need to carry out the accumulated multiplications 
`5 * (4 * (3 * (2 * 1)))` to obtain the correct result 120.

...
