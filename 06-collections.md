# 6. Collections Framework

[Back to index](README.md)

## Q44. What is the Collections hierarchy?

**Answer:** `Iterable → Collection → List / Set / Queue`. `Map` is separate and doesn't extend `Collection`.

## Q45. ArrayList vs LinkedList?

**Answer:** ArrayList is backed by an array: O(1) random access, slow insert/delete in the middle. LinkedList is a doubly linked list: O(1) insert/delete at a known node, but O(n) access. ArrayList is the better default.

## Q46. ArrayList vs Vector?

**Answer:** Vector is synchronized and legacy. ArrayList is not synchronized and faster, and it grows by about 50% instead of doubling.

## Q47. How does HashMap work internally?

**Answer:** It uses an array of buckets. For a key, `hash(key)` gives an index. Colliding entries are chained in a linked list, and since Java 8 a bucket converts to a red-black tree when it holds 8 or more entries (and the table has at least 64 slots), which makes the worst case O(log n). `get` finds the bucket, then uses `equals` to find the exact key. Default capacity is 16 with load factor 0.75, and it resizes (doubles) when it exceeds capacity × load factor.

## Q48. HashMap vs Hashtable vs ConcurrentHashMap?

**Answer:**
- **HashMap:** not thread-safe, allows one null key and null values.
- **Hashtable:** synchronized on every method, no nulls, legacy.
- **ConcurrentHashMap:** thread-safe with fine-grained locking and CAS, no nulls, much better concurrency.

## Q49. HashMap vs LinkedHashMap vs TreeMap?

**Answer:** HashMap has no order. LinkedHashMap keeps insertion (or access) order. TreeMap keeps sorted order by key, with O(log n) operations and no null keys.

## Q50. HashSet vs LinkedHashSet vs TreeSet?

**Answer:** Same idea. A HashSet is backed by a HashMap, so it has no order. LinkedHashSet keeps insertion order, and TreeSet is sorted.

## Q51. Comparable vs Comparator?

**Answer:** `Comparable` defines the natural order inside the class (`compareTo`). `Comparator` defines an external or custom order (`compare`), so you can have many orderings.

```java
list.sort(Comparator.comparing(Person::getAge).thenComparing(Person::getName));
```

## Q52. Fail-fast vs fail-safe iterators?

**Answer:** Fail-fast iterators (ArrayList, HashMap) throw `ConcurrentModificationException` if the collection is structurally modified during iteration (they check `modCount`). Fail-safe or weakly consistent iterators (CopyOnWriteArrayList, ConcurrentHashMap) work on a snapshot or tolerate concurrent changes.

## Q53. How do you remove elements safely while iterating?

**Answer:** Use `Iterator.remove()` or `removeIf(...)`.

## Q54. What are the `Arrays.asList()` pitfalls?

**Answer:** It returns a fixed-size list backed by the array, so `add` and `remove` throw `UnsupportedOperationException`. `List.of()` is truly immutable and disallows nulls.

## Q55. PriorityQueue basics?

**Answer:** A min-heap by default (or ordered by a comparator): O(log n) insert and remove, O(1) peek. Iteration order is not sorted.

## Q56. How do you make a collection thread-safe?

**Answer:** Use `Collections.synchronizedList(...)`, or better, concurrent classes: `ConcurrentHashMap`, `CopyOnWriteArrayList`, `ConcurrentLinkedQueue`, `BlockingQueue`.

## Q57. Time complexity cheat-sheet?

**Answer:**
- ArrayList: get O(1), add at end O(1) amortized, insert in the middle O(n).
- HashMap/HashSet: O(1) average.
- TreeMap/TreeSet: O(log n).
- LinkedList: get O(n), add/remove at the ends O(1).

## Q58. What are IdentityHashMap, WeakHashMap, and EnumMap?

**Answer:** IdentityHashMap compares keys with `==`. WeakHashMap lets keys be garbage-collected when they are no longer referenced elsewhere, which suits caches. EnumMap is a fast array-backed map for enum keys.
