# Chapter 3.6

_I skipped over a couple of chapters so that is why I am starting at section 6._

1.  The functions which are callbacks are,

```javascript
// callback 1
function sortAsc(a, b) {
  return a - b;
}
// callback 2
function handleClick() {
  alert("Clicked!");
}
```

2.  Function expression, arrow function, function declaration

```javascript
function sortAsc(a, b) {
  return a - b;
} // this is a function declaration.

(a, b) => b - a; // this is an arrow function.

function(){} // this is a function expression.

function outer(){
  function inner(){

  } // function declaration
} // function declaration

function(){} // function expression

() => "Yoshi" // arrow function
```

3.  `var samurai = "Tomoe"` and `var ninja = undefined`

4.  `function test(a, b, ...c){ /* a, b, c*/}`

    * `test(1, 2, 3, 4, 5)` => `a = 1, b = 2, c = [3, 4, 5]`
    * `test()` => `a = undefined b = undefined c = []`
    * _Looks like in both cases, c returns an array which is contrary to my understanding before. I thought this would return an object!_

5.  `message1`? `message2?`

```javascript
function getNinjaWieldingWeapon(ninja, weapon = "katana") {
  return ninja + " " + katana;
} // getNinjaWieldingWeapon

var message1 = getNinjaWieldingWeapon("Yoshi"); // expect "Yoshi katana"
var message2 = getNinjaWieldingWeapon("Yoshi", "wakizashi"); // expect "Yoshi wakizashi"
```
