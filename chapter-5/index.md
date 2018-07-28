# Chapter 5.8 Exercises

1.  Closures allow functions to access external variables that are in scope when the function is defined. ✅
2.  Closures come with a memory cost. ✅
3.  Mark the identifiers accessed by closures: ✅

```javascript
function Samurai(name) {
  var weapon = "katana";
  this.getWeapon = function() {
    return weapon;
  };

  this.getName = function getName() {
    return name;
  };

  this.message = name + " wielding a " + weapon;
  this.getMessage = function() {
    return this.message;
  };
}

var samurai = new Samurai("Hattori");
samurai.getWeapon(); // weapon
samurai.getName(); // name
samurai.getMessage(); // Because this.message is a property of an object it does not belong to the identifiers of the closure.
```

4.  How many execution contexts are created? What’s the largest size of the execution context stack? ✅

```javascript
function perform(ninja) {
  sneak(ninja);
  infiltrate(ninja);
}

function sneak(ninja) {
  return ninja + " skulking";
}

function infiltrate(ninja) {
  return ninja + " infiltrating";
}

perform("Kuma");
```

Answer: I misunderstood the concept. Since Javascript has a single threaded execution stack, we have the global execution stack initially, then we call `perform` which then creates and pushes its own execution context to the stack. Now within perform, we first invoke `sneak` which creates and pushes its execution context to the stack and (because of the single threadedness of Javascript) we wait until `sneak` resolves and is removed from the top of the execution context stack. Lastly, `infiltrate` is executed and pushed to the top of the execution stack, resolved, and then removed from the stack. Therefore, the largest stack would have a size of 3 execution contexts.

5.  `const` ✅
6.  `var` is defined in the global and function scope while `let` is global, function, and block-level scoped. ✅
7.  `getSamurai` is not defined as a function declaration therefore is declared upon execution, so, any reference to it before it is executed will throw a reference error. ✅
