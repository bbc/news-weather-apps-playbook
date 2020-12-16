# Writing unit tests


### Frameworks

We use [AssertJ](https://assertj.github.io/doc/#assertj-overview) for fluent assertions, and [Mockito Kotlin](https://github.com/nhaarman/mockito-kotlin) for working with mocks.

### Variable names
We write `sut` to name the "system/subject under test" -  the class or function being tested.

We write `expected` to name the variable that represents what we expect a function to return - the value we want to assert against.

We write `actual` to name the actual result returned by  the function that's being tested.


### Formatting

Group the test code into three distinct sections, following the AAA (Arrange-Act-Assert) pattern.

_We do this:_
```kotlin
val name = "Joe Bloggs"
val greeting = "Hello, Joe Bloggs!"
val sut = Greeter(name)

val result = sut.greeting()

assertThat(result).isEqualTo(greeting)
```

_We don't do this:_
```kotlin
val name = "Joe Bloggs"
val sut = Greeter(name)
assertThat(sut.greeting()).isEqualTo("Hello, Joe Bloggs!")
```