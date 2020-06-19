# Kotlin style guide

This document details our house style for writing Kotlin code.

### Conditional expressions

Use curly braces for complex `if..else` expressions.

We do this:
```kotlin
return if (hours > 0) {
    String.format("%s:%s:%s", hours, minutes, seconds)
} else {
    String.format("%s:%s", minutes, seconds)
}
```

We don't do this:
```kotlin
return if (hours > 0) String.format("%s:%s:%s", hours, minutes, seconds)
else String.format("%s:%s", minutes, seconds)
```

For simple expressions that fit on a single line, braces can be omitted:

```kotlin
return if (isVisible) VISIBLE else GONE
```
