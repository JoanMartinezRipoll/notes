#Theory

##STI vs Polymorphism

STI works best when dealing with models that are going to share the exact same data but have different behaviour. So the table will have no columns with null values.

##Inheritance vs Composition

Use inheritance for is-a associations and composition for has-a associations

If it makes sense to think that all the methods of the super class will be used by the under-class, use inheritance, otherwise use composition

##Include vs require vs extend

Require is like the java includes, so we can then use that external module and use its methods. Include will actually include the methods of the module as instance methods for that class. Extends will actually include the methods of the module as class methods for that class.

##Class vs module

Modules are about providing methods that you can use across multiple classes - think about them as "libraries". They can be included in classes and modules by using include. Therefore, modules are used for mixin. Modules are about functions.
Classes are about objects. Classes can use inheritance

##Mixins

A set of code wrapped up in a module that a class can include or extend to add additional capabilities without using inheritance.


##Conventions
Controllers and databases use plural names
Models use singular names
View-related code goes to helper classes, logic code goes to controller or other classes

##Concepts
- Methods defined in any helper file are automatically available in any view, but for convenience we separate them by usage (i.e if users_controller uses a helper_method we write it at the users_helper class)

##HSTORE
Fields can be used when we want to store key-value data that only affects the views or that is useful to have in a hash form format (like settings of user).
