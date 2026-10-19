# 9. Generics, Inner Classes and Misc

[Back to index](README.md)

## Q87. What are generics and type erasure?

**Answer:** Generics give compile-time type safety. At runtime the type parameters are erased, so `List<String>` and `List<Integer>` are both just `List`. That is why you can't do `new T()` or `instanceof List<String>`.

## Q88. `? extends T` vs `? super T`?

**Answer:** Use `extends` to read from a producer, and `super` to write to a consumer (PECS: Producer-Extends, Consumer-Super).

## Q89. What are the types of inner classes?

**Answer:** Member inner, static nested, local, and anonymous. Non-static inner classes hold a reference to the outer instance.

## Q90. What is autoboxing, and what is the Integer cache pitfall?

**Answer:** Boxing converts a primitive to a wrapper. `Integer` values from -128 to 127 are cached, so `==` can return true for small values and false for larger ones. Always use `equals()`.

## Q91. Is Java pass by value or pass by reference?

**Answer:** Always pass by value. For objects, the *reference* is copied, so you can mutate the object but can't reassign the caller's variable.

## Q92. What is serialization and `transient`?

**Answer:** Serialization converts an object into a byte stream via `Serializable`. `transient` fields are skipped, and `serialVersionUID` versions the class.

## Q93. What is reflection?

**Answer:** Inspecting and manipulating classes, methods, and fields at runtime via `java.lang.reflect`. It is powerful but slower and can break encapsulation.

## Q94. What are annotations?

**Answer:** Metadata on code, e.g. `@Override`, `@Deprecated`, `@FunctionalInterface`, or custom ones with `@Retention` and `@Target`.

## Q95. What are enum features?

**Answer:** Enums are type-safe constants that can have fields, constructors, and methods, and can implement interfaces. They are the safest way to build singletons.

## Q96. `static` block vs instance initializer?

**Answer:** A static block runs once when the class loads. An instance initializer runs before each constructor.

## Q97. Java I/O vs NIO?

**Answer:** I/O is stream-based and blocking. NIO (`java.nio`) uses buffers and channels, supports non-blocking I/O with selectors, and `Files`/`Path` give a cleaner file API.

## Q98. What is the Date/Time API?

**Answer:** Use `java.time` (`LocalDate`, `LocalDateTime`, `ZonedDateTime`, `Duration`, `Period`). It is immutable and thread-safe, unlike `Date` and `SimpleDateFormat`.

## Q99. `java.util.Date` vs `java.sql.Date`?

**Answer:** `java.sql.Date` extends `java.util.Date` and holds only the date part, for SQL `DATE`.

## Q100. What are strong, soft, weak, and phantom references?

**Answer:** Strong is the normal reference. Soft is collected only when memory is low (good for caches). Weak is collected at the next GC. Phantom is used for cleanup actions after finalization.
