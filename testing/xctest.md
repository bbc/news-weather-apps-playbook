# XCTest

1. [Unit Test Strategy](#Unit-Test-Strategy))
1. [Using `final` for `XCTestCase`](#Using-final-for-XCTestCase) 
1. [setUp, tearDown and member variables](#setUp-tearDown-and-member-variables)
1. [Dummys, Fakes, Stubs, Spies and Mocks](#Dummys-Fakes-Stubs-Spies-and-Mocks)

## Unit Test Strategy
When working on a codebase with a team of any size, the modern convention is to unit test as much as possible. If you're in any doubt about whether you should write a unit test ask yourself: if my code changes were to be accidentally deleted by a merge conflict resolution or such like, would the test suits fail? If you're making a change to UI Layout then snapshot tests can act as a red flag if someone is to change your layout by accident later on.

It is rare that something cannot or should not be unit tested, but if you stumble across one of those situations, try to ensure that if your code is removed or altered erroneously, either the compiler will refuse to compile or there is a UI/Integration tests somewhere that will fail.  Test coverage tools can usually identify un-tested code but try not to lean on them. Good unit testing helps lead to well structured, [SOLID](https://en.wikipedia.org/wiki/SOLID) principle-following code.

## Using `final` for `XCTestCase`
Adding the `final` keyword to your class is an indicator to the reader that this class is not meant to be extended. This makes a lot of sense for `XCTestCase`. There are only a few situations where you would actually want to extend your `XCTestCase` class, but usually if you are doing this then it is probably a code smell that you're doing something wrong.

`final` also has performance implications. This means you want to try and make as many of your classes `final` as possible.  Google will tell you more about this. __Note: it's possible to achieve the same performance gains by making all member variables private__

## setUp, tearDown and member variables
Because of the way XCTestCase manages member variables we have to instantiate and then deallocate them in the `setUp` and `tearDown` fuctions.

For more info on this see [this](https://qualitycoding.org/xctestcase-teardown/)

In light of this, the current best practice is to delcare any members as implicitly unwrapped types, instantiate them in the `setUp` and then set them to nil in the `tearDown`.


## Dummys, Fakes, Stubs, Spies and Mocks
- *Dummy* objects are passed around but never actually used. Usually they are just used to fill parameter lists.
- *Fake* objects actually have working implementations, but usually take some shortcut which makes them not suitable for production (an in memory database is a good example).
- *Stubs* provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test.
- *Spies* are stubs that also record some information based on how they were called. One form of this might be an email service that records how many messages it was sent.
- *Mocks* are what we are talking about here: objects pre-programmed with expectations which form a specification of the calls they are expected to receive.

references:
- https://martinfowler.com/articles/mocksArentStubs.html
- https://martinfowler.com/bliki/TestDouble.html
- https://qualitycoding.org/xctestcase-teardown/
