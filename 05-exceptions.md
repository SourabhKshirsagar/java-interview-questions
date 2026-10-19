# 5. Exception Handling

[Back to index](README.md)

## Q36. Checked vs unchecked exceptions?

**Answer:** Checked exceptions (e.g. `IOException`, `SQLException`) are verified at compile time and must be caught or declared. Unchecked exceptions (`RuntimeException` and its subclasses like `NullPointerException`) are not. `Error`s (e.g. `OutOfMemoryError`) are not meant to be caught.

## Q37. `throw` vs `throws`?

**Answer:** `throw` raises an exception object. `throws` declares in a method signature that it may throw one.

## Q38. Does `finally` always run?

**Answer:** Almost always. It doesn't run if the JVM exits (`System.exit()`), crashes, or the thread is killed. A `return` in `finally` overrides a `return` in `try`, which is bad practice.

## Q39. What is try-with-resources?

**Answer:** It auto-closes any `AutoCloseable` resource, even on exceptions.

```java
try (BufferedReader br = new BufferedReader(new FileReader("a.txt"))) {
    return br.readLine();
}
```

If both the body and `close()` throw, the close exception is added as *suppressed*.

## Q40. How do you create a custom exception?

**Answer:** Extend `Exception` for checked or `RuntimeException` for unchecked, and add constructors that take a message and a cause.

## Q41. Can you catch multiple exceptions in one block?

**Answer:** Yes: `catch (IOException | SQLException e)`. The types can't be related by inheritance.

## Q42. What are exception handling best practices?

**Answer:** Catch specific exceptions. Never swallow them silently. Preserve the cause when wrapping. Log once, not at every layer. Don't use exceptions for normal control flow.

## Q43. If a parent method doesn't throw, can the overriding method throw a checked exception?

**Answer:** No. An overriding method can throw only the same or narrower checked exceptions (any unchecked exception is fine).
