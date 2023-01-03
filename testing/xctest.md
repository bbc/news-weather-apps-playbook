# XCTest

1. [Unit Test Strategy](#Unit-Test-Strategy))
1. [Using `final` for `XCTestCase`](#Using-final-for-XCTestCase) 
1. [setUp, tearDown and member variables](#setUp-tearDown-and-member-variables)
1. [Dummys, Fakes, Stubs, Spies and Mocks](#Dummys-Fakes-Stubs-Spies-and-Mocks)

## Unit Test Strategy
When working on a codebase with a team of any size, the modern convention is to unit test as much as possible. If you're in any doubt whether you should write a unit test ask yourself: if my code changes were to be accidentally deleted by a merge conflict resolution, would the test suites fail? If you're making a change to UI Layout then snapshot tests can act as a red flag if someone changes your layout by accident further down the line.

It is rare that something can not or should not be unit tested, but if you stumble across one of those situations try to ensure that if your code is removed or altered erroneously, either the compiler will refuse to compile or there is a UI/Integration tests somewhere that will fail.  Test coverage tools can usually identify un-tested code but try not to lean on them. Good unit testing helps to achieve well structured, [SOLID](https://en.wikipedia.org/wiki/SOLID) principle-following code.

> **_The Beyoncé Rule_** from the [Software Engineering at Google book](https://abseil.io/resources/swe-book/html/toc.html). **"If you liked it, then you shoulda put a test on it."**.
> _We are often asked, when coaching new hires, which behaviors or properties actually need to be tested?   The straightforward answer is: test everything that you don’t want to break. In other words, if you want to be confident that a system exhibits a particular behavior, the only way to be sure it will is to write an automated test for it. This includes all of the usual suspects like testing performance, behavioral correctness, accessibility, and security. It also includes less obvious properties like testing how a system handles failure._
> _We have a name for this general philosophy: we call it the Beyoncé Rule. Succinctly, it can be stated as follows: “If you liked it, then you shoulda put a test on it.” The Beyoncé Rule is often invoked by infrastructure teams that are responsible for making changes across the entire codebase. If unrelated infrastructure changes pass all of your tests but still break your team’s product, you are on the hook for fixing it and adding the additional tests._

## Using `final` for `XCTestCase`
Adding the `final` keyword to your class is an indicator to the reader that this class is not meant to be extended. This makes a lot of sense for `XCTestCase`. There are only a few situations where you would actually want to extend your `XCTestCase` class, but usually if you are doing this then it is probably a code smell that you're doing something wrong.

Using `final` also has [performance implications](https://developer.apple.com/swift/blog/?id=27).

## setUp, tearDown and member variables
Because of the way XCTestCase manages member variables we have to instantiate and then deallocate them in the `setUp` and `tearDown` fuctions.

For more info on this see [this](https://qualitycoding.org/xctestcase-teardown/)

In light of this, the current best practice is to delcare any members as implicitly unwrapped types, instantiate them in the `setUp` and then set them to nil in the `tearDown`.


## Dummys, Fakes, Stubs, Spies and Mocks
In an attempt to encourage consistency and readability in our tests, we have chosen to follow the vocabulary described in the article [Test Doubles](https://martinfowler.com/bliki/TestDouble.html) when describing the purposes of different objects created for use in tests. A short summary from this article:
 
> - **Dummy** objects are passed around but never actually used. Usually they are just used to fill parameter lists.
> - **Fake** objects actually have working implementations, but usually take some shortcut which makes them not suitable for production (an [InMemoryTestDatabase](https://martinfowler.com/bliki/InMemoryTestDatabase.html) is a good example).
> - **Stubs** provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test.
> - **Spies** are stubs that also record some information based on how they were called. One form of this might be an email service that records how many messages it was sent.
> - **Mocks** are pre-programmed with expectations which form a specification of the calls they are expected to receive. They can throw an exception if they receive a call they don't expect and are checked during verification to ensure they got all the calls they were expecting.

A more thorough discussion of these can be found in [Mocks Aren't Stubs](https://martinfowler.com/articles/mocksArentStubs.html).
 
 There are a number of similar articles online, which we're sure will have various nuances in their explanations and preferences. We valued choosing and documenting one over the specific preferences of any given article.
