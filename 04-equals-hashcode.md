# 4. equals(), hashCode() and Object Methods

[Back to index](README.md)

## Q32. What is the `equals`/`hashCode` contract?

**Answer:**
- If `a.equals(b)` is true, then `a.hashCode() == b.hashCode()` must be true.
- Equal hash codes don't imply equal objects.
- `equals` must be reflexive, symmetric, transitive, and consistent.

If you override one, override the other, or `HashMap` and `HashSet` will misbehave.

## Q33. What happens if you use a mutable object as a HashMap key and change it?

**Answer:** Its hash code changes, so you can no longer find it in the bucket where it was stored. That is effectively a leak, so prefer immutable keys.

## Q34. What are the methods of `Object`?

**Answer:** `equals`, `hashCode`, `toString`, `clone`, `getClass`, `wait`, `notify`, `notifyAll`, `finalize`.

## Q35. What is `clone()` and the Cloneable interface?

**Answer:** `clone()` does a shallow copy and needs `Cloneable`, otherwise it throws `CloneNotSupportedException`. Many teams prefer a copy constructor instead.
