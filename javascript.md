**string template**

String template is available in ECMAScript 6 feature by using back tick 

    const a = 1
    const str = `a=${a}`
    console.log(str) 
    
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

**prototypal inheritance**

Javascript inheritance is implemeneted using prototype pointer `__proto__`

* https://javascript.info/prototype-inheritance
