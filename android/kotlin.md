# Kotlin style guide

This document details our house style for writing Kotlin code.

### Conditionals

In Kotlin, `if..else` syntax can be used for both statements and expressions.

When writing conditional statements, always use curly braces.

_We do this:_
```kotlin
if (condition) {
    doSomething()
} else {
    doOtherThing()
}
```

_We don't do this:_
```kotlin
if (condition) doSomething() else doOtherThing()
```

The same rule applies to conditional expressions, but it can be relaxed for simple expressions that fit on a single line:
```kotlin
return if (isVisible) VISIBLE else GONE
```

### Returns

Functions with only a single expression can omit the braces and return statement

If the function is simple, short and can fit in one line then the return should be written as an expression.

_Do_

```Kotlin
fun getIsFooEnabled(fooId : String) : Boolean = fooProvider.getIsFooEnabledById(fooId)
```

_Don't_

```Kotlin
fun getIsFooEnabled(fooId : String) : Boolean {
  return fooProvider.getIsFooEnabledById(fooId)
}
```
