# 2. OOP Concepts

[Back to index](README.md)

## Q11. What are the four pillars of OOP?

**Answer:**
- **Encapsulation:** Encapsulation is the OOP principle of wrapping data (variables) and the methods that operate on that data into a single unit, a class, and restricting direct access to the data. We make the variables private and expose them through public methods, so the class controls how its data is read and modified.
  
- **Inheritance:** reuse and extend a parent class.
- **Polymorphism:** Polymorphism means “many forms.” It is the ability of the same method call to behave differently depending on the object it is used with. In Java it comes in two types: compile-time polymorphism (method overloading), where the method is chosen at compile time based on the parameters, and runtime polymorphism (method overriding), where a parent-type reference points to a child object and the JVM decides at runtime, based on the actual object, which version of the method to run.
- **Abstraction:** Abstraction means hiding the implementation details and showing only the essential features. It focuses on what an object does rather than how. In Java we achieve it with abstract classes and interfaces..

## Q12. Overloading vs overriding?

**Answer:** Overloading means the same method name with different parameters in the same class, resolved at compile time. Overriding means a subclass redefines a parent method with the same signature, resolved at runtime through dynamic dispatch.

## Q13. Abstract class vs interface?

**Answer:**
- An abstract class can hold state (fields), constructors, and any method type. A class can extend only one.
- An interface is a template or contract: it says what a class must do.
Methods are public by default. You don’t need to write public.
Traditionally, methods have no body. They are implicitly public abstract.

Use an abstract class for shared state and a partial implementation. Use an interface for a capability or contract.

## Q14. Can we override private, static, or final methods?

**Answer:**
- **private:** no, it isn't visible to the subclass.
- **static:** no, it is *hidden* rather than overridden.
- **final:** no, that is the point of `final`.

## Q15. What is the diamond problem and how does Java handle it?

**Answer:** In Java, the Diamond Problem is avoided in multiple inheritance by using interfaces instead of classes. When a class implements multiple interfaces that contain conflicting default methods, Java forces the class to override the conflicting method and explicitly resolve the ambiguity.”

Example: If interfaces B and C both provide a default show() method, class D must override show() to specify which implementation to use.

## Q16. `this` vs `super`?

**Answer:** The this keyword in Java is a reference variable that refers to the current object of a class. It is commonly used to distinguish instance variables from local variables when they have the same name.

The super keyword in Java is used to refer to the immediate parent class object in an inheritance hierarchy. It allows a subclass to explicitly access parent class members when they are hidden or overridden

## Q17. Constructor chaining and the default constructor?

**Answer:** If you write no constructor, the compiler adds a no-arg one. Once you write any constructor, it doesn't. Every constructor implicitly calls `super()` unless you specify otherwise.

## Q18. What is `final`?

**Answer:** A `final` variable can't be reassigned (a final reference can still point to a mutable object). A `final` method can't be overridden. A `final` class can't be extended.

## Q19. `final` vs `finally` vs `finalize`?

**Answer:** `final` is a modifier. `finally` is the block that runs after try/catch. `finalize()` is an old GC hook, deprecated for removal, so don't use it. Use `try-with-resources` or `Cleaner` instead.

## Q20. What are the access modifiers?

**Answer:** `private` (class only), default/package-private (same package), `protected` (same package plus subclasses), `public` (everywhere).

## Q21. Static vs instance members? Can you use `this` in a static method?

**Answer:** Static members belong to the class and are shared. Instance members belong to each object. You can't use `this` in a static method because no instance exists.

## Q22. Composition vs inheritance?

**Answer:** Inheritance is an "is-a" relationship, and composition is "has-a". Prefer composition because it is more flexible and avoids tight coupling.

## Q23. What is a marker interface?

**Answer:** An interface with no methods that tags a class with a capability, like `Serializable` or `Cloneable`.

## Q24. Shallow vs deep copy?

**Answer:** Shallow copy duplicates the object but shares the nested objects it references. Deep copy also duplicates the nested objects. Do this with a copy constructor, serialization, or manual cloning.

## Q25. Can a constructor be `final`, `static`, or `abstract`?

**Answer:** No.
