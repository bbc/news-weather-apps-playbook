# BBC News Apps Team: A Clean Code Guide

## Why do we need this guide?
Like so much of software engineering, there are many great ideas about what clean code looks like (probably as many as there are JSON parsing frameworks, at least). So, the question is not “what is clean code” but “what do we, the team, think of as clean code”.

### Okay, but why do we need that?

The simple answer is that if we have a guide then we all know what is expected of us, and if we have a reference we all know against what our code will be measured at review.
Who will maintain it? What if I don’t agree?
This is a living document, meaning it is never finished. If you wish to change something, simply submit the change you want to see by opening a pull request and asking the team to comment.

# Our Clean Code Guide

## SOLID
It is often said that there are no new ideas under the sun, and when it comes to mobile software engineering it seems even more true. Many of the ideas that we consider ‘modern’ or ‘innovative’ had their birthplace in technologies of years or even decades past.

MVVM? That was Microsoft in the early 2000’s! https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel

Promises and Futures? That’s from the 1970’s! https://en.wikipedia.org/wiki/Futures_and_promises

I digress. So, SOLID was from the turn of the century and (mostly) still has a lot to offer. https://scotch.io/bar-talk/s-o-l-i-d-the-first-five-principles-of-object-oriented-design

## Single Responsibility Principle
Consider carefully how much your classes, and methods, are doing with each line you write. Does your new code match theme of the old? Is there a new class, struct, enumeration, or static method struggling to be get out?

However, also remember that if things get too small, they become very hard to comprehend as a whole later. Jon Reid has a good article about this. https://qualitycoding.org/single-responsibility-principle/

## Open/Closed Principle
Or, to put it into simpler terms, strive to write code that anticipates being in existence for years to come without trying to anticipate how it will be in existence in years to come. Good habits to build here include

Make the public API as small as possible
Make the code as simple as possible, to achieve what needs to be done right now
Make the code as readable as possible
Avoid mutability and state
Provide good test coverage

## Liskov Substitution Principle
A great way to think of this is in terms of testing. Can you, when unit testing a class, stub or mock out the other classes around it, such that you are only testing a single “unit” and have complete control of all others that it interfaces with and the state/interactions that they provide.

If we look at the classic quote for what this means - "objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program." - then we can see that it has object-oriented programming in mind, but it applies equally in protocol-oriented programming where we could rewrite the quote as "objects in a program should be replaceable with other, conforming objects, without altering the correctness of that program."
https://en.wikipedia.org/wiki/Protocol_(object-oriented_programming)

## Interface Segregation Principle
"many client-specific interfaces are better than one general-purpose interface."

In short, much as your classes and methods should be small and focused, so should the interfaces.

## Dependency Inversion Principle
"depend upon abstractions, [not] concretions."

Again, looking to protocols can really help here, making your code much more malleable, open to re-use and simpler to stub or mock.

## Immutability By Default
Be lazy and make it immutable by default. Why? Because anything that cannot change does not need to be tested (as much).

Not only do you get to write less tests but you make it easier to reason about your code. This has all sorts of great side effects, including making it easier to debug issues. Imagine looking at a mechanical motor and trying to spot the issue...the less things that move/are moving the simpler it will be to see the problem.

## Unidirection Data Flow By Default
A unidirectional flow of data works well in isolation and even better in concert with other ideas, like immutability by default and MVVM.

This is often achieved by the use of frameworks like, for example, Rx. However, the principle is not dependent on the technology.

https://academy.realm.io/posts/eric-maxwell-uni-directional-architecture-android-using-realm/

## Headers
The file header should convey only that information which cannot otherwise be conveyed in the file otherwise. For example, a copyright is a common legal requirement for many companies.

Recommended Style:

```
/**
* Copyright (c) $today.year BBC. All rights reserved.
*/
```

Your name is all up in the git history so you really don’t need the fame of having it elsewhere.

## Comments
Like headers, the best comments are noticeable by their absence. A great comment adds context which cannot otherwise be conveyed by the code. Examples that are often cited here are oddities of some API that you have to work around/with, details of why you shipped what follows it and/or what the next steps are to improve what follows.

If you one day get a Slack message from a colleague that says “I just had to work on the FuClass and loved your comment about that weird barMethod. It saved me ages” then you know you did good.

Swift Comment Format: http://nshipster.com/swift-documentation/

Kotlin Comment Format: https://kotlinlang.org/docs/reference/kotlin-doc.html

## Logging
Logging is so useful it will probably still be with us for the first AI that writes “destroy the humans” to stderr. In the meantime, let’s make our logging as useful as it can be with these simple habits
Only log what you need. Don’t fill the console with log messages or you will struggle to find signal in the noise.
Only log while you need. Remove the log statements when you are done.
Only log in context. What else could you add to your log message to make it useful to someone who is not you? Line Number? Class Name? Method Name? Timestamp? ID?

## Stringly Typed Is Not Strongly Typed / Avoid Primitive Obsession
Everytime you decide to represent something as a string, as yourself: “Is this actually string”? Is there JSON inside that string? XML? Is there a numerical ID inside there? A datestamp? A time interval?

If the string is simply there until it is parsed/re-interpreted, consider making that change at the edge of the app (probably near the API layer), or even asking for a different format from the API. The rest of your code will very likely be simpler, more readable, more type safe and more autocomplete friendly.
Helpers, Utilities and Manager Classes
We all make them, and don’t think very hard about them, but all too often they are just a bag of methods we don’t know what else to do with (or they become it). This is a code smell as, whilst it helps with the DRY principle, it typically flies in the face of SRP. It’s even worse if they have state!

If you’ve managed to create an immutable class of static methods that all share a logical, common theme, then congratulations!

## Naming
Naming is hard, so let’s follow Uncle Bob’s lead:

Classes should be nouns
Methods should be verbs
Functional Programming?
TBC: something about FP, POP and OO?

## Accessibility
The BBC is for everyone and so we embrace accessibility by default - it is not an afterthought, a later addition, or optional. We consider it at design, during implementation and in quality assurance.
If you work on a ticket that does not have accessibility considerations, ask yourself if it should and, if so, in what way, and ask the question. Remember our mission statement :
"To act in the public interest, serving all audiences with impartial, high-quality and distinctive media content and services that inform, educate and entertain."

We cannot serve all audiences if not all of them can access the news.

More information: https://confluence.dev.bbc.co.uk/pages/viewpage.action?pageId=154783891

## Security & Privacy
Our users, the public, have the right to expect that we will treat their privacy and security with the level of seriousness that it deserves. Whilst this is a nice aspirational statement in a country like the UK, it could impact someones liberty or life in others, where reading habits may be monitored and acted upon.

"To act in the public interest…”

http://www.bbc.co.uk/news/world-middle-east-35492065

https://twitter.com/vixentael/status/968788222619869184?ref_src=twcamp%5Eshare%7Ctwsrc%5Eios%7Ctwgr%5Eemail%7Ctwcon%5E7100%7Ctwterm%5E3

It is often the case in BBC apps that aspects of data collection can be opted out by users. Please consider if that is the case if you are implementing a new data collection feature.

## Size Matters
Keep your classes small and your methods much much smaller. A large class is likely a sign that there is some sort of abstraction class hiding inside. Find it, and set it free!

Similarly, large methods are telling you the same thing - find the pieces and cut that into simpler, and smaller ones.

An interesting side effect of this is that often a small method also means less room for complexity, most especially branching logic. You will often find nice things such as the branching logic ending up being the only thing in the public method, and the branches themselves being separate private functions.

This can often be the case if you have large conditional logic - often, breaking down the component parts of a conditional into methods for example can help avoid large ‘if’ conditions and provide a clearer sense of code intent in the method name.

This all makes readability, reasonability, and testability much easier. Future you will thank you.


## Backend For Frontend (AKA our new best friend, forever)
We are currently pitching to have a middle layer service between the new API’s from the CMS (Optimo and Ares) and the apps themselves. We believe this is necessary because the output from these services is necessarily generic and, thus, unsuitable for a mobile app. To adopt these API’s as they are would require us to write a lot of business logic and data transform code on each client (web, ios and android) and to waste users bandwidth and time with noisy data transmission that is expensive to receive and parse.

By ensuring that this new layer returns view model data that is simply parsed and drawn to the UI, we can create more predictable, flexible and reliable client apps.

Additionally, with such a layer in place, we believe we will be able to respond to change much faster, sometimes without even having to release a new version of the app.

https://samnewman.io/patterns/architectural/bff/

## Ideas for future sections (feel free to add)
How to contribute to a three amigos session
Responsibility for your code - from idea to build to measure and learn
Communication etiquette
????
Good Team Practices

## See Also:

### iOS
[BBC News Apps Team: iOS/Swift Style Guide](https://docs.google.com/document/d/1jXrss9JX3Cih42upizLPGDcPbjvoCObRhL8-oBhzZXU/edit)

### Android
[BBC News Apps Team: Java/Kotlin Style Guide](https://github.com/bbc/news-app-android/blob/develop/AndroidCodingGuide.md)
[BBC News Apps Team: Android Studio Code Style Settings](https://github.com/bbc/news-app-android/blob/develop/Config/README.md)
[BBC News Apps Team: Android Code Analysis Tools](https://github.com/bbc/news-app-android/blob/develop/Project/config/README.md)

### References:
https://codeburst.io/6-lazy-programming-mistakes-and-how-to-avoid-them-a251c656a177
https://medium.com/@amlcurran/avoiding-primitive-obsession-in-swift-5325b65d521e
