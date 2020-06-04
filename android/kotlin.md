# Kotlin style guide

This document details our house style for writing Kotlin code.

## Braces

Use curly braces for single-line `if..else` statements.

**Do this**
```kotlin
if (condition) {
  foo = 1
} else {
  foo = 0
}
```

**Don't do this**
```kotlin
if (condition)
  foo = 1
else
  foo = 0
```
