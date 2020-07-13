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
class AndroidDispatchers : Dispatchers {
  fun io() = Dispatchers.IO
  fun ui() = Dispatchers.Main
}
```

_Don't_

```Kotlin
class AndroidDispatchers : Dispatchers {

  fun io(): CoroutineDispatcher {
      return Dispatchers.IO
  }

  fun ui(): CoroutineDispatcher {
      return Dispatchers.Main
  }
}
```

Use an explicit return statement if the function is  complex or consists of multiple lines; for example if the function argument is manipulated into a different type via extension functions/mapping functions or when there is a conditional logic like returning the result of a `when` block.

_Do_

```kotlin

fun TheDataModel.toEntity(): TheDomainModel {
  return when (this) {
    is SimpleDataModel -> toEntity()
    is AnotherSimpleDataModel -> toEntity()
    is ComplexDataModel -> toEntity()
    else -> UnsupportedDataModel
  }
}
```

Functions where the return type is unclear are more readable with a multiline, explicit return function.

_Do_
```kotlin
fun foo() : Pair<<Class<Int>, Long> {
  return mapOf(Int::class.java to 100L).map { it.toPair() }
}
```

_Don't_
```kotlin
fun foo() = mapOf(Int::class.java to 100L).map { it.toPair() }
```

There might be situations where single expression functions and return block functions are contained in the same class or file. These should be properly grouped.

_Do_
```kotlin


class Foo {

  fun SimpleDataModel.toEntity() = SimpleDomainModel

  fun foo() = Foo()

  fun TheDataModel.toEntity(): TheDomainModel {
    return when (this) {
      is SimpleDataModel -> toEntity()
      is AnotherSimpleDataModel -> toEntity()
      is ComplexDataModel -> toEntity()
      else -> UnsupportedDataModel
    }
  }

  fun ComplexDataModel.toEntity(): ComplexDomainModel {
    val subComponent = SubComponent(renderers[0])
    val component = Component(engines.map { engine -> engine.apply( renderer = subComponent) })
    return ComplexDomainModel(
        isEnabled,
        component
    )
  }
}
```
