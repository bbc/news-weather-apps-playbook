# Writing unit tests

### Contents
- [Frameworks](#frameworks)
- [Variable names](#variable-names)
- [Formatting](#formatting)

----
### Frameworks

Use [AssertJ](https://assertj.github.io/doc/#assertj-overview) for fluent assertions, and [Mockito Kotlin](https://github.com/nhaarman/mockito-kotlin) for working with mocks.

### Variable names
Write `sut` to name the "system/subject under test" -  the class or function being tested.

Write `expected` to name the variable that represents what we expect a function to return - the value we want to assert against.

Write `actual` to name the actual result returned by  the function that's being tested.


### Formatting

Group the test code into three distinct sections, following the AAA (Arrange-Act-Assert) pattern.

_We do this:_
```kotlin
val name = "Joe Bloggs"
val expected = "Hello, Joe Bloggs!"
val sut = Greeter(name)

val actual = sut.greeting()

assertThat(actual).isEqualTo(expected)
```

_We don't do this:_
```kotlin
val name = "Joe Bloggs"
val sut = Greeter(name)
assertThat(sut.greeting()).isEqualTo("Hello, Joe Bloggs!")
```

### Naming Tests

Don't use "should". A test name is a definitive statement
_Don't do this:_
```kotlin
@Test
fun `getTotal should return 5`() {}
```

_Instead do this:_
```kotlin
@Test
fun `getTotal returns 5`() {}
```

Don't use "correct" or "returns correct value". Be clear in what's expected. This also helps reveal gaps in unit tests
_Don't do this:_
```kotlin
@Test
fun `hasSeenDialog returns correct value`() {}
```

_Instead do this:_
```kotlin
@Test
fun `hasSeenDialog returns true when user has seen dialog`() {}
fun `hasSeenDialog returns false when user has not seen dialog`() {}
```
