# Data Structures and Algorithms

**This page will detail key notes on Data Structures and Algorithms, the primary topic tested in coding aptitude tests for internships and full-time jobs alike. It will use JavaScript syntax (although using C++ syntax as an alternative won't be too different from my surface-level research) and plain English where possible, as the primary resource I used to learn this is freeCodeCamp's JavaScript Data Structures and Algorithms Course**

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

### Character Classes

Character classes allow for some flexibility when searching for a literal pattern. For example if you want to match bag, big and bug, but not bog, You can create the regex `/b[aiu]g/` where `[aiu]` is the character class that will only match said characters.

To match a range of characters in the alphabet, a easier syntax to use is this: `/[a-e]/` - this would match every lowercase letter between a and e inclusive.

### Flags and Wildcard

You can have multiple flags on your regex.

We can use `testRegex = /case/i` to avoid the case issue- the i flag ignores case.

To find more than the first match, we use the g flag [global search flag], which would return every instance the regex was present, and can ignore casing if needed with flags 'gi'.

You can use the wildcard in a regex as such: `testRegex = /.un/` and this would return all the words 'nun', 'fun', 'run' etc. **Note that the g flag isn't present,** so an input string such as 'I went on a fun run' would only return fun, the first instance.












