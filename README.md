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

- In statements involving other operators, JavaScript does not convert numeric values to strings. For example:

 ```
  "37" - 7 // 30
  "37" + 7 // "377"
 ```

- An alternative method of retrieving a number from a string is with the + (unary plus) operator:

 ```
  "1.1" + "1.1" = "1.11.1"
  (+"1.1") + (+"1.1") = 2.2   
  // Note: the parentheses are added for clarity, not required.
 ```

- If the finally block returns a value, this value becomes the return value of the entire try-catch-finally production, regardless of any return statements in the try and catch blocks:

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

- Difference between a for...of loop and a for...in loop. While for...in iterates over property names, for...of iterates over property values:

 ```
  let arr = [3, 5, 7];
  arr.foo = "hello";

  for (let i in arr) {
     console.log(i); // logs "0", "1", "2", "foo"
  }
  
  for (let i of arr) {
     console.log(i); // logs "3", "5", "7"
  }
 ```
- Recursion itself uses a stack: the function stack. The stack-like behavior can be seen in the following example:
 ```
  function foo(i) {
    if (i < 0)
      return;
    console.log('begin:' + i);
    foo(i - 1);
    console.log('end:' + i);
  }
  foo(3);

  // Output:

  // begin:3
  // begin:2
  // begin:1
  // begin:0
  // end:0
  // end:1
  // end:2
  // end:3
 ```
- Nested function is a closure, this means that a nested function can "inherit" the arguments and variables of its containing function.
 
 ```
  function addSquares(a,b) {
   function square(x) {
     return x * x;
   }
   return square(a) + square(b);
 }
 a = addSquares(2,3); // returns 13
 b = addSquares(3,4); // returns 25
 c = addSquares(4,5); // returns 41
 ```
