# Chapter 4.5 Exercises

1.  Rewrite with `rest` parameter. ✅

```javascript
// original sum function
function sum() {
  var sum = 0;
  for (let i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}
```

```javascript
// with rest parameter
function sum(...rest) {
  return rest.reduce((acc, cur) => {
    acc += cur;
    return acc;
  }, 0);
}
```

2.  What are the values of the variables `ninja` and `samurai` ✅

```javascript
function getSamurai(samurai) {
  "use strict";
  arguments[0] = "Ishida";
  return samurai;
}

function getNinja(ninja) {
  arguments[0] = "Fuma";
  return ninja;
}
/*
    we expect samurai to have a value of "Toyotomi" since we are in "strict mode" where there is no reference between arguments and the parameter samurai.
*/
var samurai = getSamurai("Toyotomi");

/*
    getNinja however, is not in "strict mode" thus preserving the link between a functions arguments array-like object and the parameters. We expect ninja to be "Fuma";
*/
var ninja = getNinja("Yoshi");
```

3.  Which assertions will pass? ✅

```javascript
function whoAmI1() {
  "use strict";
  return this;
}

function whoAmI2() {
  return this;
}
/*
    Since whoAmI1 is running in "strict mode" we expect the assertion to fail. 
*/
assert(whoAmI1() === "window", "Window?");

/*
    Since whoAmI2 is NOT running in "strict mode" we expect the assertion to be true and display "Window?". 
*/
assert(whoAmI2() === "window", "Window?");
```

4.  Which assertions will pass? ✅

```javascript
var ninja1 = {
  whoAmI: function() {
    return this;
  }
};

var ninja2 = {
  whoAmI: ninja1.whoAmI
};

var identify = ninja2.whoAmI;

// This assertion will pass because ninja1.whoAmI is a function declaration and not an arrow function.
assert(ninja1.whoAmI() === ninja1, "ninja1?");

// This would fail because whoAmI is called as a method of ninja2
assert(ninja2.whoAmI() === ninja1, "ninja1?");

// Identify is called in the context of the global context so this will not pass.
assert(identify() === ninja1, "ninja1 again?");

// Passes because we are calling ninja1's whoAmI method in the context of ninja2 so this will pass.
assert(ninja1.whoAmI.call(ninja2) === ninja2, "ninja2 here?");
```

5.  Which assertions will pass? ✅

```javascript
function Ninja() {
  this.whoAmI = () => this;
}

var ninja1 = new Ninja();
var ninja2 = {
  whoAmI: ninja1.whoAmI
};

// PASS : The arrow function's this parameter is assign upon creation so this would pass.
assert(ninja1.whoAmI() === ninja1, "ninja1 here?");
// FAIL : Again the arrow functions context is assigned at creation so this would fail.
assert(ninja2.whoAmI() === ninja2, "ninja2 here?");
```

6.  Which assertions will pass? ✅

```javascript
    function Ninja(){
        this.whoAmI = function(){
            return this;
    }.bind(this);

    var ninja1 = new Ninja();
    var ninja2 = {
        whoAmI: ninja1.whoAmI
    }
    // When you use bind, you are assigning a permanent context to the function.
    assert(ninja1.whoAmI() === ninja1, "ninja1 here?"); // PASS
    assert(ninja2.whoAmI() === ninja2, "ninja2 here?"); // FAIL
```
