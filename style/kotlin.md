# Kotlin style guide

This document details our house style for writing Kotlin code.

You can install code style settings for Android Studio by following the instructions [here](https://github.com/bbc/News-And-Weather-Android-Code-style).

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

### Return statements

In general, prefer explicit return statements over expression bodies when writing functions.

Functions can be written with an expression body when:
- the body of the function fits neatly on a single line
- the function is simple enough that an explicit return type can be omitted

_We do this_
```kotlin
fun getItemCount() = items.size
```

_We don't do this_
```kotlin
fun getItemCount() =
    items.filterIsInstance<TextItem>()
        .filter { item -> item.hasLink }
        .size + if (isLoading) 1 else 0

```

Avoid mixing functions that use an expression body with functions that use a return statement in the same class or file. If you do decide to mix the different styles, then they should be properly grouped together.