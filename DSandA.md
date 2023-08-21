# Data Structures and Algorithms

**This page will detail key notes on Data Structures and Algorithms, the primary topic tested in coding aptitude tests for internships and full-time jobs alike. It will use JavaScript syntax (although using C++ syntax as an alternative won't be too different from my surface-level research) and plain English where possible, as the primary resource I used to learn this is freeCodeCamp's JavaScript Data Structures and Algorithms Course**

## Contents
- [Data Structures and Algorithms](#data-structures-and-algorithms)
  - [Contents](#contents)
  - [Regular Expressions](#regular-expressions)
    - [The Test Method](#the-test-method)
    - [Extract Matches](#extract-matches)
    - [Character Classes and Flags](#character-classes-and-flags)




## Regular Expressions

Regular expressions, frequently shortened to `regex` or `regexp`, are used in programming languages to match parts of strings: a hugely important feature for many aptitude tests. JavaScript has multiple ways to use regexes, which are detailed below.

### The Test Method

```
    let testStr = "freeCodeCamp";
    let testRegex = /Code/;
    testRegex.test(testStr); // returns true
```

The `.test()` takes the regex, applies it to `testStr` and returns true or false if the pattern is found.

We can also use the OR operator inside `testRegex` like so: `/yes|no|maybe/` and `.test()` would return true if any of the terms were found.

**NOTE: The above code will only return true for exact matches, so "Code" and "code" would not be considered a match.**

### Extract Matches

So far we have only checked whether a pattern exists or not in a string, we can also extract the actual matches found, with the `.match()` method, as seen below.

```
    let extractStr = "Extract the word 'coding' from this string."
    let codingRegex = /coding/;
    let result = extractStr.match(codingRegex);
```

*Please note this is the opposite to the test syntax, and the regex is the parameter, and the string is the object.*

### Character Classes and Flags

We can use `testRegex = /case/i` to avoid the case issue- the i flag ignores case.

To find more than the first match, we use the g flag [global search flag], which would return every instance the regex was present, and can ignore casing if needed with flags 'gi'.

You can use the wildcard in a regex as such: `testRegex = /.un/` and this would return all the words 'nun', 'fun', 'run' etc. **Note that the g flag isn't present,** so an input string such as 'I went on a fun run' would only return fun, the first instance.

Character classes allow for some flexibility when searching for a literal pattern. For example if you want to match bag, big and bug, but not bog, You can create the regex `/b[aiu]g/` where `[aiu]` is the character class that will only match said characters.

To match a range of characters in the alphabet, a easier syntax to use is this: `/[a-e]/` - this would match every lowercase letter between a and e inclusive. You can include other ranges as such `/[a-e0-9]/`, which would match letters a to e and all numbers.

The inverse of including ranges is denoted by ^ as such `[^a-e0-9]`; this would match all characters excluding those listed, and we can also add characters infront of the caret (^) which *would* be included.

You can find situations where characters appear once, or multiple times in a row using the + character, for example `/a+/` would return the first instance that more than one a appeared.

Similar to the functionality of the +, the * character finds instances of the character appearing zero or more times.

The ? character utiliises lazy matching, `/t[a-z]*i/` that would return 'titani' from 'titanic' would return 'ti' when `/t[a-z]*?i/` is used, as that is the shortest occurence of the expression in the string.

Matching at the start of strings again uses the caret character '^' but when used outside a character class, it is used to search for patterns at the start of strings, by placing it in front of said string.

Matching at the end of strings uses the anchor sign, as such `/string$/`

\w can be used to match A-Z, a-z, 0-9 and _ instead of a character class.
\W accomplishes the opposite.
\d matches 0-9, \D is the inverse.
\s matches whitespace, \S is the inverse.

Adding {} after a character and specifying a range within, matches if the number present is within the range, for example, `Oh{2,3}` would return 'Ohh' but not 'Ohhhhhh'. You can also only specify one side of the range, or a specific number of repeats, by omitting the comma.

`/\w/` - syntax for above functions.
















