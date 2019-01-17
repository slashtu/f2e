#### 1. Implement “Inheritance”

Classical

```javascript
function inherit(C, P){
    var F = function(){};
    F.prototype = P.prototype;
    C.prototype = new F();
    C.prototype.constructor = C;
}

function Parent(){ this.name = 'dad'}
function Child(){ this.name = 'son'}

inherit(Child, Parent)

var c = new Child()
var p = new Parent()
```

ES5

```javascript
function Parent(){ this.name = "dad" }
function Child(){ this.name = "child" }

Child.prototype = Object.create(Parent.prototype)
Child.prototype.constructor = Child

var c = new Child()
var p = new Parent()
```

Es6

```javascript
class Child extends Parent
```

#### 2. What is strict mode**

Strict mode changes some previously-accepted mistakes into errors. JavaScript was designed to be easy for novice developers, 
and sometimes it gives operations which should be errors non-error semantics. 
Sometimes this fixes the immediate problem, but sometimes this creates worse problems in the future. 
Strict mode treats these mistakes as errors so that they're discovered and promptly fixed. 

babel-plubin: https://babeljs.io/docs/plugins/transform-strict-mode/

```javascript
'use strict';

mistypeVariable = 17; // accidentally create global variables

Function('"use strict";console.log(this)')() // undefined, not window

delete Object.prototype; // delete undeletable properties

// function parameter names be unique
function sum(a, a, c) { // !!! syntax error
  return a + b + c; // wrong if this code ran
}
```

#### 3. Implement Singleton Design Pattern

```javascript
var Singleton = (function () {
    var instance;
    
    function People(name) {
      this.name = name;
      this.sayName = function() {console.log(this.name)};
    }
 
    function createInstance() {
        var object = new People("Slash");
        return object;
    }
 
    return {
        getInstance: function () {
            if (!instance) {
                instance = createInstance();
            }
            return instance;
        }
    };
})();
 
function run() {
 
    var instance1 = Singleton.getInstance();
    var instance2 = Singleton.getInstance();
 
    alert("Same instance? " + (instance1 === instance2));  
```

ES6

```javascript
// singleton.js
let instance = null;

class Cache{
  constructor() {
    if(!instance){
      instance = this;
    }

    // to test whether we have singleton or not
    this.time = new Date()
    return instance;
  }
}
```

#### 4. How to check nested objecct properties

* immutable.js
* loadash get api
* You can use an utility function like this:

```javascript
get = function(obj, key) {
    return key.split(".").reduce(function(o, x) {
        return (typeof o == "undefined" || o === null) ? o : o[x];
    }, obj);
}

// Usage
 get(user, 'loc.lat')     // 50
 get(user, 'loc.foo.bar') // undefined
```

#### 5. When to Use Function.prototype.call()

```javascript
const map = f => x => Array.prototype.map.call(x, f)

const items = document.querySelectorAll('div')

items.map(doSomething)
// => Uncaught TypeError: items.map is not a function
// document.querySelectorAll (and similar methods) do not return an Array, 
// they return a NodeList and a NodeList does not contain a 
// map method.

// function programing
map(doSomething)(items)
```

#### 6. Implement throttle and debounce

```javascript
var lib = (() => {
  let throttleTime = 0;
  let deounceTimer = 0;
  return {
    throttle: (f, t) => () => {
       const now = new Date().getTime();
       if(now - throttleTime > t) {
         throttleTime = now;
         f();
       }
    },
    
    debounce: (f, t) => () => {
      if(deounceTimer != 0){
        clearTimeout(deounceTimer);
      }
      
      deounceTimer = setTimeout( () => {
        deounceTimer = 0;
        f();
      }, t);
    },
  }
})();

scrollBar.on('scroll', lib.throttle(function() {
  // do something every second
}, 1000));
```

Mutiple
```javascript
function throttle(fn, time) {
  let cb = fn;
  let t = time
  let throttleTime = 0;

  this.getTime = function (){
     return throttleTime;
  }

  this.do = function(fn, time) {
     const now = new Date().getTime();
     if (now - throttleTime > time) {
       throttleTime = now;
       fn();
     
     }
  }
}


t = new throttle()

for(var i = 0; i < 100000000; i++){
    t.do(() => {console.log(new Date().getTime())}, 100)
}
```

#### 7. How do you clone an object?

```javascript
clone = JSON.parse(JSON.stringify(object))
```
```javascript
function deepClone(o) {
  return Object.keys(o).reduce((clone, key) => {
    clone[key] = (typeof o[key] === 'object' && o[key] !== null) ? deepClone(o[key]) : o[key]

    return clone;
  }, {})
}
```


#### 8. How do you compare two objects in JavaScript?

```javascript
function isDeepEqual(obj1, obj2, testPrototypes = false) {
  if (obj1 === obj2) {
    return true
  }

  if (typeof obj1 === "function" && typeof obj2 === "function") {
    return obj1.toString() === obj2.toString()
  }

  if (obj1 instanceof Date && obj2 instanceof Date) {
    return obj1.getTime() === obj2.getTime()
  }

  if (
    Object.prototype.toString.call(obj1) !== Object.prototype.toString.call(obj2) ||
    typeof obj1 !== "object"
  ) {
    return false
  }

  const prototypesAreEqual = testPrototypes ? 
    isDeepEqual(
        Object.getPrototypeOf(obj1),
        Object.getPrototypeOf(obj2),
        true
      )
    : true

  const obj1Props = Object.getOwnPropertyNames(obj1)
  const obj2Props = Object.getOwnPropertyNames(obj2)

  return (
    obj1Props.length === obj2Props.length &&
    prototypesAreEqual &&
    obj1Props.every(prop => isDeepEqual(obj1[prop], obj2[prop]))
  )
}
```
or
```javascript
const equals = (a, b) => {
  if (a === b) return true;
  if (a instanceof Date && b instanceof Date) return a.getTime() === b.getTime();
  if (!a || !b || (typeof a !== 'object' && typeof b !== 'object')) return a === b;
  if (a === null || a === undefined || b === null || b === undefined) return false;
  if (a.prototype !== b.prototype) return false;
  let keys = Object.keys(a);
  if (keys.length !== Object.keys(b).length) return false;
  return keys.every(k => equals(a[k], b[k]));
};
```

References
1. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
