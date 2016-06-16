# javascript
Javascript style guide


###Tips

- Because of hoisting, all var statements in a function should be placed as near to the top of the function as possible. This best practice increases the clarity of the code.
```
var myvar = "my value";
 
(function() {
  console.log(myvar); // undefined
  var myvar = "local value";
})();
```
- Object attributes are not protected in `const` declarations, so the following statement is executed without problems.
```
const MY_OBJECT = {"key": "value"};
MY_OBJECT.key = "otherValue";
```
- In expressions involving numeric and string values with the + operator, JavaScript converts numeric values to strings. For example, consider the following statements:
```
x = "The answer is " + 42 // "The answer is 42"
y = 42 + " is the answer" // "42 is the answer"
```
In statements involving other operators, JavaScript does not convert numeric values to strings. For example:


```
"37" - 7 // 30
"37" + 7 // "377"
```

- An alternative method of retrieving a number from a string is with the + (unary plus) operator:

"1.1" + "1.1" = "1.11.1"
(+"1.1") + (+"1.1") = 2.2   
// Note: the parentheses are added for clarity, not required.

If the finally block returns a value, this value becomes the return value of the entire try-catch-finally production, regardless of any return statements in the try and catch blocks:

```
function f() {
  try {
    console.log(0);
    throw "bogus";
  } catch(e) {
    console.log(1);
    return true; // this return statement is suspended
                 // until finally block has completed
    console.log(2); // not reachable
  } finally {
    console.log(3);
    return false; // overwrites the previous "return"
    console.log(4); // not reachable
  }
  // "return false" is executed now  
  console.log(5); // not reachable
}
f(); // console 0, 1, 3; returns false
```
