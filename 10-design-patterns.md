# 10. Design Patterns

[Back to index](README.md)

## Q101. Which design patterns should you know?

**Answer:**
- **Singleton:** one instance.
- **Factory / Abstract Factory:** object creation without exposing the logic.
- **Builder:** step-by-step construction of complex objects.
- **Strategy:** swappable algorithms.
- **Observer:** publish/subscribe notifications.
- **Decorator:** add behavior without subclassing.
- **Adapter:** make incompatible interfaces work together.

## Q102. How do you make a class immutable?

**Answer:** Make the class `final`, make fields `private final`, provide no setters, initialize through the constructor, and defensively copy any mutable fields on the way in and out.

```java
public final class Money {
    private final long amount;
    private final List<String> tags;

    public Money(long amount, List<String> tags) {
        this.amount = amount;
        this.tags = List.copyOf(tags);   // defensive copy
    }
    public long getAmount() { return amount; }
    public List<String> getTags() { return tags; }
}
```
