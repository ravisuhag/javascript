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
