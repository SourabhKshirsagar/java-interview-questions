# 1. Java Basics and JVM

[Back to index](README.md)

## Q1. How is Java platform independent?

**Answer:** Source code compiles to bytecode (`.class`), not machine code. Each OS has its own JVM that turns bytecode into native instructions. So you compile once and run anywhere there is a JVM.

## Q2. JDK vs JRE vs JVM?

**Answer:**
- **JVM** runs bytecode.
- **JRE** is the JVM plus the core libraries.
- **JDK** is the JRE plus development tools (`javac`, `jar`, `javadoc`, debugger).

## Q3. What does the ClassLoader do?

**Answer:** It loads classes into the JVM at runtime. The main ones are Bootstrap (core classes), Platform/Extension, and Application (your classpath). They follow **parent delegation**: a loader first asks its parent, and only loads the class itself if the parent can't.

## Q4. Explain JVM memory areas.

**Answer:**
- **Heap:** all objects, shared across threads, managed by the GC. Split into Young (Eden, Survivor) and Old generations.
- **Stack:** one per thread, holding frames with local variables and method calls.
- **Metaspace:** class metadata (replaced PermGen in Java 8).
- **PC register and native method stack:** per-thread execution state.

## Q5. How does garbage collection work?

**Answer:** The GC finds objects that are no longer reachable from GC roots (thread stacks, static fields) and reclaims them. New objects start in Young. Survivors of minor GCs get promoted to Old, which is collected by a major or full GC. Common collectors: G1 (default in modern Java), ZGC and Shenandoah (low pause), Parallel.

## Q6. Can you force garbage collection?

**Answer:** No. `System.gc()` is only a hint, and the JVM may ignore it.

## Q7. What is a memory leak in Java and how can it happen?

**Answer:** Objects that are still referenced but no longer needed can't be collected. Typical causes: static collections that keep growing, unclosed resources, listeners that are never removed, and `ThreadLocal` values that are never cleaned up.

## Q8. StackOverflowError vs OutOfMemoryError?

**Answer:** `StackOverflowError` means a thread's stack is exhausted, usually from infinite recursion. `OutOfMemoryError` means the heap or metaspace is exhausted.

## Q9. What is JIT compilation?

**Answer:** The JIT compiler converts frequently executed ("hot") bytecode into optimized native code at runtime, so long-running apps get faster.

## Q10. Stack vs heap?

**Answer:** The stack holds primitives and references in per-thread frames and is fast and automatically freed. The heap holds objects, is shared, and is cleaned by the GC.
