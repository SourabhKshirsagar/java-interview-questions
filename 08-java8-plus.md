# 8. Java 8+ Features

[Back to index](README.md)

## Q78. What are lambdas and functional interfaces?

**Answer:** A lambda is a concise implementation of a functional interface (one abstract method), e.g. `Runnable`, `Comparator`, `Function<T,R>`, `Predicate<T>`, `Consumer<T>`, `Supplier<T>`. Annotate custom ones with `@FunctionalInterface`.

## Q79. What is the Stream API?

**Answer:** A declarative pipeline over data: source → intermediate operations (lazy: `filter`, `map`, `sorted`) → terminal operation (`collect`, `forEach`, `reduce`). A stream can be consumed only once.

```java
Map<String, List<Employee>> byDept = employees.stream()
    .filter(e -> e.getSalary() > 50000)
    .collect(Collectors.groupingBy(Employee::getDept));
```

## Q80. `map` vs `flatMap`?

**Answer:** `map` transforms each element one-to-one. `flatMap` transforms each element into a stream and flattens them into one.

## Q81. What is `Optional`?

**Answer:** A container that may or may not hold a value, which reduces null checks. Use `orElse`, `orElseGet`, `orElseThrow`, `map`, and `ifPresent`. Don't use it for fields or method parameters, and avoid a bare `get()`.

## Q82. What are method references?

**Answer:** A shorthand for lambdas: `String::toUpperCase`, `System.out::println`, `Person::new`.

## Q83. What are default and static methods in interfaces?

**Answer:** They let interfaces evolve without breaking implementers.

## Q84. Sequential vs parallel streams?

**Answer:** Parallel streams use the common ForkJoinPool. They help with large, CPU-bound, stateless work but can hurt with small data, I/O, or shared state.

## Q85. Which newer features are worth knowing?

**Answer:** `var` (10), text blocks (15), records (16), sealed classes (17), switch expressions and pattern matching (14-21), and virtual threads (21). The latest LTS releases are 17, 21, and 25.

## Q86. What is a record?

**Answer:** A concise immutable data carrier: `record Point(int x, int y) {}`. It auto-generates the constructor, accessors, `equals`, `hashCode`, and `toString`.
