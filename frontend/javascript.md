#Javascript
##Operations and Methods

**=== vs ==** The `==` operator will compare for equality after doing any necessary type conversions. The `===` operator will not do the conversion, so if two values are not the same type `===` will simply return false

**isNaN** `isNaN("Hello") #true`

**typeof** `typeof 3 #number` or `typeof "hi" #string`

**this vs event.target**

`this` always refers to the DOM element the listener was attached to (in the code), event.target is the actual DOM element that was clicked.For example

```
<div class="outer">
  <div class="inner"></div>
</div>
and attach click listener to the outer div
```
$('.outer').click( handler);
The handler will be invoked when you click inside the outer div as well as the inner one. In such a case, inside the handler, this would refer to the .outer DOM element, and event.target would refer to the .inner element.

##Objects
######CREATING OBJECTS
```
var myObj = {
    type: 'fancy',
    disposition: 'sunny'
};
```

or

```
var myObj = new Object();`
`myObj.name = "Charlie";
```

######THE THIS KEYWORD
Refers to whichever object called that method.Notice how methods can too be assigned to objects.
```
var setAge = function (newAge) {
  this.age = newAge;
};
var susan = new Object();
susan.setAge = setAge;
susan.setAge(35)
```

######CUSTOM CONSTRUCTORS
Constructors can include methods and private attributes

```
function Square(height, width) {
  this.height = height;
  this.width = width;
  this.calcArea = function() {
      return this.height * this.height;
  };
  var amount = 3000; //This is private
}
var rex = new Rectangle(7,3);
var area = rex.calcArea();
```

######EXTENDING THE PROTOTYPE
```
function Cat(name, breed) {
    this.name = name;
}

Cat.prototype.meow = function() {
    console.log("Meow!");
}
```

######INHERITANCE
```
function Animal(name, numLegs) {
    this.name = name;
    this.numLegs = numLegs;
   }
function Penguin(name) {
    this.name = name;
    this.numLegs = 2;
}
Penguin.prototype = new Animal();
```

Now cats can use the meow methods. Notice that the custom constructor can also include methods

######METHODS
-  `myObj.hasOwnProperty('name'));`should print true if the object has that property
- `for (var prop in objectInstance)` will print all the properties of the object

