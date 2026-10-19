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
- An interface defines a contract. Since Java 8 it can have `default` and `static` methods, and since 9 `private` methods. Its fields are implicitly constants. A class can implement many.

Use an abstract class for shared state and a partial implementation. Use an interface for a capability or contract.

## Q14. Can we override private, static, or final methods?

**Answer:**
- **private:** no, it isn't visible to the subclass.
- **static:** no, it is *hidden* rather than overridden.
- **final:** no, that is the point of `final`.

## Q15. What is the diamond problem and how does Java handle it?

**Answer:** Java doesn't allow multiple class inheritance. With interface default methods, if two interfaces provide the same default, the class must override it explicitly, and it can call one with `InterfaceA.super.method()`.

## Q16. `this` vs `super`?

**Answer:** `this` refers to the current object, and `this(...)` calls another constructor in the same class. `super` refers to the parent, and `super(...)` calls the parent constructor. Either call must be the first statement in a constructor.

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
