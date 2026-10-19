# 7. Multithreading and Concurrency

[Back to index](README.md)

## Q59. What are the ways to create a thread?

**Answer:** Extend `Thread`, implement `Runnable`, implement `Callable` (returns a result and can throw) via an `ExecutorService`, or use `CompletableFuture`. Prefer executors over manually creating threads.

## Q60. `start()` vs `run()`?

**Answer:** `start()` creates a new thread and runs `run()` in it. Calling `run()` directly just executes it in the current thread.

## Q61. What is the thread lifecycle?

**Answer:** NEW → RUNNABLE → (BLOCKED / WAITING / TIMED_WAITING) → TERMINATED.

## Q62. What does the `synchronized` keyword do?

**Answer:** It gives mutual exclusion and visibility. On an instance method it locks `this`, on a static method the Class object, and a synchronized block locks the object you specify. Keep blocks small.

## Q63. What is `volatile`?

**Answer:** It guarantees visibility of writes across threads and prevents certain reordering, but it does **not** make compound operations like `count++` atomic. Use `AtomicInteger` or locks for that.

## Q64. `wait()` vs `sleep()`?

**Answer:** `wait()` (on `Object`) releases the monitor and must be called inside synchronized code. It resumes on `notify`/`notifyAll`. `sleep()` (on `Thread`) pauses without releasing any lock.

## Q65. What is a deadlock and how do you prevent it?

**Answer:** Two or more threads each hold a lock the other needs, so none can proceed. Prevent it by acquiring locks in a consistent global order, using `tryLock` with a timeout, and keeping lock scope small.

## Q66. What are race conditions, livelock, and starvation?

**Answer:** A race condition is a bug where the result depends on thread timing. In livelock, threads keep reacting to each other without progress. In starvation, a thread never gets CPU or a lock.

## Q67. `ReentrantLock` vs `synchronized`?

**Answer:** `ReentrantLock` adds `tryLock`, timed and interruptible locking, fairness options, and multiple `Condition`s. You must unlock it in `finally`.

## Q68. What is the Executor framework and what are the thread pool types?

**Answer:** `ExecutorService` separates task submission from execution. Common factories: `newFixedThreadPool`, `newCachedThreadPool`, `newSingleThreadExecutor`, `newScheduledThreadPool`. For production, prefer constructing `ThreadPoolExecutor` directly so you control queue size and rejection policy.

## Q69. `Runnable` vs `Callable`; what is `Future`?

**Answer:** `Callable` returns a value and can throw checked exceptions. `Future.get()` retrieves the result, blocking until it is ready.

## Q70. What is `CompletableFuture`?

**Answer:** It chains asynchronous steps without blocking.

```java
CompletableFuture.supplyAsync(() -> fetchUser())
    .thenApply(User::getName)
    .exceptionally(ex -> "unknown");
```

## Q71. What are atomic classes and CAS?

**Answer:** `AtomicInteger`, `AtomicReference`, etc. use compare-and-swap hardware instructions for lock-free thread safety.

## Q72. CountDownLatch, CyclicBarrier, Semaphore?

**Answer:**
- **CountDownLatch:** one or more threads wait until a count reaches zero (one-time use).
- **CyclicBarrier:** a group of threads wait for each other, and it is reusable.
- **Semaphore:** limits the number of threads accessing a resource.

## Q73. What is `ThreadLocal`?

**Answer:** It gives each thread its own copy of a variable. Call `remove()` in pooled threads to avoid leaks.

## Q74. What is a daemon thread?

**Answer:** A background thread that doesn't stop the JVM from exiting (e.g. the GC thread).

## Q75. How do you write a thread-safe singleton?

**Answer:** Use an enum singleton, a static holder class, or double-checked locking with a `volatile` instance.

```java
public class Singleton {
    private static volatile Singleton instance;
    private Singleton() {}
    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) instance = new Singleton();
            }
        }
        return instance;
    }
}
```

## Q76. What is the Java Memory Model (happens-before)?

**Answer:** It defines when one thread's writes are guaranteed visible to another, through rules like unlock-before-lock, volatile write-before-read, and `Thread.start()`/`join()`.

## Q77. What are virtual threads (Java 21+)?

**Answer:** Lightweight threads managed by the JVM rather than the OS. They let you write simple blocking code that scales to very large numbers of concurrent tasks, e.g. `Executors.newVirtualThreadPerTaskExecutor()`.
