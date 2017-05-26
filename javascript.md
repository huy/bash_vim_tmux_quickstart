**debug**

to start debug at specified line of code add `debugger` in the location

    debugger;

* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Statements/debugger

**string template**

String template is available in ECMAScript 6 feature by using back tick 

    const a = 1
    const str = `a=${a}`
    console.log(str) 
    
**object structuring**
    
    var a = 1;
    var b = 2;
    var h = {a,b};
    console.log(h); // Object {a: 1, b: 2}

**object destructuring**

    var o = {p: 42, q: true};
    var {p, q} = o;

    console.log(p); // 42
    console.log(q); // true

* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

**spread operator**

    function myFunction(x, y, z) { }
    var args = [0, 1, 2];
    myFunction(...args);
    
* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Spread_operator

**exclamation**

Exclamation operator is used to coerce a expression into boolean

    !true # false
    !!true # true
    !undefined # true
    !!undefined # false
    !0 # true
    !!0 # false
    !null # true
    !!null # false
    
**prototypal inheritance**

Javascript inheritance is implemeneted using prototype pointer `__proto__`

* https://javascript.info/prototype-inheritance
