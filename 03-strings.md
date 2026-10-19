# 3. String Handling

[Back to index](README.md)

## Q26. Why is String immutable?

**Answer:**
- The String pool can safely share instances.
- Immutable means once a String object is created, its content can never change. Java enforces this with a few design choices in the String class itself.
- The class is final. Nobody can extend String and override its methods to sneak in mutation.

## Q27. What is the String pool?

**Answer:** A cache inside the heap for string literals. `String s = "abc"` reuses the pooled object, while `new String("abc")` always creates a new heap object. `intern()` returns the pooled version.

## Q28. `==` vs `equals()` for Strings?

**Answer:** == checks whether two references point to the same object (or whether two primitives have the same value), while equals() checks whether two objects are logically equal based on their content, as defined by the class.

```java
String a = "hi", b = "hi", c = new String("hi");
a == b;        // true  (same pooled object)
a == c;        // false
a.equals(c);   // true
```

## Q29. String vs StringBuilder vs StringBuffer?

**Answer:** String is immutable. StringBuilder is mutable, fast, and not thread-safe. StringBuffer is mutable and synchronized, so it is thread-safe but slower. In single-threaded code use StringBuilder.

## Q30. How many objects does `new String("abc")` create?

**Answer:** Up to two: one in the pool (if "abc" isn't there yet) and one on the heap.

## Q31. Why is `char[]` preferred for passwords?

**Answer:** You can overwrite a `char[]` after use. A String stays in memory until it is collected, which could expose it in a heap dump.
