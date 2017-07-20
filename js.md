#### 1. Implement “Inheritance”

Classical

  ```
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

  ```
  function Parent(){ this.name = "dad" }
  function Child(){ this.name = "child" }
  
  Child.prototype = Object.create(Parent.prototype)
  Child.prototype.constructor = Child

  var c = new Child()
  var p = new Parent()
  ```
  
Es6

  ```
  class Child extends Parent
  ```

#### 2. What is strict mode**

Strict mode changes some previously-accepted mistakes into errors. JavaScript was designed to be easy for novice developers, 
and sometimes it gives operations which should be errors non-error semantics. 
Sometimes this fixes the immediate problem, but sometimes this creates worse problems in the future. 
Strict mode treats these mistakes as errors so that they're discovered and promptly fixed. 

babel-plubin: https://babeljs.io/docs/plugins/transform-strict-mode/

```

'use strict';

mistypeVariable = 17; // accidentally create global variables

delete Object.prototype; // delete undeletable properties

// function parameter names be unique
function sum(a, a, c) { // !!! syntax error
  return a + b + c; // wrong if this code ran
}
```

#### 3. implement Singleton Design Pattern

References
1. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
