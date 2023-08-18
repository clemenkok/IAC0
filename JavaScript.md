# JavaScript and Web Development

This page details some core concepts and syntax details to begin developing your own website using HTML, CSS and JavaScript. Learning everything here should allow you to go on to learn an industry-standard framework such as React, Angular or Vue to develop more complex websites easily and efficiently. As you will have primarily learnt C++ in first year, there are several annotations pertaining to similar features in C++, and a base level understanding of operators, string concatenation and loops is assumed, and not covered, due to its' similarity to C++.

## JSON and localStorage

### JSON and localStorage are functions contained within JavaScript itself, used for compatibility and saving values through different instances of the same webpage respectively

`JSON.stringify(JSObject)` -- converts JS Objects into JSON strings, allowing for compatibility with various languages.

`JSON.parse(JSON)` -- converts JSON strings back to JS Objects (NOTE: It does not convert functions, so it is like a CPP struct).

`localStorage.setItem('identifier', 'value')` -- this only supports strings, identifier, followed by the value.

To get around the limitation of only supporting strings, we can use `localStorage.setItem('identifier', JSON.stringify(JSObject))`.

`localStorage.getItem('identifier')`

`localStorage.removeItem('identifier')` -- throws an error, avoid this with an if loop to check for null.

## DOM (Document Object Model)

### As the name suggests, this models the HTML elements as JavaScript Objects, allowing our HTML and JS to interact.

`document.body.innerHTML = 'hello';`` replaces the content of the body with hello.

-- the document object models the webpage (the DOM).

**The DOM combines JS and HTML**, giving JS full control of the webpage.

The HTML element is converted to a JS Object when referred to as such.

**Methods: methods are function stored inside an object**

`document.querySelector()` is a method, allowing use to take anything from HTML and put it inside our JS.

If we added innerHTML to this, like so: `document.querySelector('button').innerHTML` --  it would return the text inside the first button on the HTML webpage.

We can specify which button by assigning the button a class in HTML, then starting our querySelector input with a period, which searches for classes.

We are able to take the input from a input box in HTML by using `.value` and use it in our JS code :O

${variable} -- inserts the variable into a string.

Use Number() to convert the strings, **which are always what is returned by the DOM**, to integers.
Use String() to do similar in reverse.

Finally, the last object built into JS is the window object -- this refers to the browser itself, whereas the document object we learnt about earlier, refers to the webpage.

We can avoid typing window, as JS will automatically add it in front of things such as console.log and alert.


## Event Listeners

`.addEventListener('action', create a function here)` is preferred to all of the below, as we have more control, it allows us to add & remove multiple listeners in much more concise code.

**NOTE:** If the call to the function is given, instead a function itself, it leads to undefined behaviour when the action occurs.

onclick - as the name suggests
onkeydown - as the name suggests
onscroll - as the name suggests
onmouseenter - hovering over
onmouseleave - stop hovering over

## JavaScript Quirks

If a string **only** contains a number, when subtracting, multiplying or dividing it, JS will auto-convert it to a number.
However, as + is multi-functional with string concatenation, it will add them as strings as shown below:

```
    console.log('25' * 3) = outputs 75

    console.log('25' + 10) = outputs 2510
```

To prevent this issue from arising, we should remember to **always convert our strings before using math operations.**
## Arrays and Loops

Arrays are declared the same as C++:

`const myArray = [10, 20, 30];`

`myArray.splice(startIndex, number)` - **removes** elements starting at the startIndex and the number specified.

Loops are **exactly identical** to C++, aside from a few minor language differences.

In a for loop, we can use **continue** inside if statements, so that the repeating code for that loop will not occur.

**break** does the same thing as in C++.

## Switch Statements

Switch statements are used to match one value against many options, as an alternative to if else chains. See the example below:

```
switch (fruit){
    case "apple:
        console.log("The fruit is an apple");
        break;
    case "orange":
        console.log("The fruit is an orange");
        break;
}
```
The break keyword as mentioned before will stop the switch statement at the position in which it is used, and only output the corresponding text to the console.

Additionally, the keyword default can be used instead of the `case value:` syntax, to give a statement if no matching case statement is found.

## Advanced Functions

We can save functions as variables:
```
    const function1 = function greeting() {
    }
```
Due to this, in the instance above, we do not actually need the name 'greeting' instead just calling the function through the variable, ''function1()''.

A function written as such is known as an 'anonymous function'. A key difference between saving a function in a variable versus giving it it's own name is that
we are not able to 'hoist' it, that is, to call it before we instantiate it in the code, whereas functions written in the traditional method can be.

As functions are seen as values in JavaScript, they can be stored inside objects, like member functions in C++, but here they are known as 'methods'
By the same virtue, we can pass functions into functions; the child function called by the parent, is known as a **callback function**.

For all these advanced functions, we can use a built-in function known as ''setTimeout(function to be run in the future, how long to wait before running aforementioned function)''.

This is how **asynchronous** code is written in JS, in that said code will not wait for a line to finish before going to the next line, as otherwise, anytime setTimeout() is called, the program will stop doing anything for however long is specified.

A similar built-in function setInterval(), will run the function specified endlessly with the interval given. This is stopped by using the id returned by setInterval(),
so we can use ''let idInterval = setInterval()'' then ''clearInterval(idInterval)'' to stop the interval running.

We are able to use the method of an array - ''.forEach()'' to loop through it, as shown.

```
    let myArray = [
                'make dinner',
                'wash dishes',
                'watch youtube',

                ].forEach(function(value, index)) {
                    console.log(value);
                }
```

The above code would output the values in the array until there were none left.

Minor difference from regular for loops, here, we use ''return;'' instead of ''continue;'' and if ''break;'' is deemed to be necessary, we should use the regular for loops.

## Arrow Functions


Like delta functions in C++, these provide a shorter way to write functions, as seen:

```
    const arrowFunction = (param1, param2) => {
        console.log('hello);
    }
```

These work the same as regular functions generally, however, they have a few shortcuts, for example, when an arrow function has only **one parameter**, the regular brackets around them are optional, so we are able to remove them. Similarly, if the arrow function only has one line, we can remove the curly braces as well as the return keyword and write the code to be run inline, as shown below:

''const simpleMath = num => 2 + num;'' -- this is a valid line of code in JS

In industry, it is recommended to write arrow functions where we are passing a function as a parameter to another function, as it increases code readability.

## Destructoring

### Array Destructoring

Destructoring is one of the most useful practices for using any front-end framework, particularly relevant with the prevalance of React, Angular and Vue in the web development workflow. 

`const alphabet = ['A', 'B', 'C', 'D', 'E']`

`const [a, b] = alphabet;` -- this outputs A and B, but how does this work?

The element, an array "alphabet" in this case we want to destruct is on the right hand side in this case, and the variables we want to store into on the left.
As a and b are in the first and second positions, we take the first and second element in the array.
To take elements in different, non-consecutive places, we can use the spread operator "..." to take the rest of the array following the last actually named values.

This philosophy can be used in function as such, which is a key way it is used in React:

```function sumAndMultiply (a, b){
    return [a+b, a*b, a/b];
}

const [sum, multiply, 'No division'] = sumAndMultiply(2, 3)

console.log(sum);
console.log(multiply);
console.log(division);
```

In the code above, the destructor will return 'No division' if only two values are in the return of the function, if `a/b` is present, it will return a result.

### Object Destructoring

This works similar to that of an array, but we use the following syntax:

```
const personTwo = {
    name: 'Sally',
    age: 32;
}

const {name : firstName, age} = personTwo

console.log(name);
console.log(age);

```

The `name : firstName` assigns a new property to the object personTwo, and using `console.log(firstName)` would also output Sally.
We can also nest object destruction, if the object contains another one.







