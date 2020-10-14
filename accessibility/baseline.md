# Baseline

This document details our baseline commitment for creating accessibile apps. Any accessibility features not included here should be considered [outside the scope](#out-of-scope) of our minimum requirements.

### Screen reader support

:white_check_mark: *Every logical user interface element, or group of elements, can be described by a screen reader*

To better support our visually impaired users, it's important that our applications can be navigated using audio cues. This means we need to use *accessibility identififers* in our iOS applications to support [VoiceOver](https://support.apple.com/en-gb/guide/iphone/iph3e2e415f/ios), and *content descriptions* in our Android applications to support [TalkBack](https://support.google.com/accessibility/android/answer/6283677?hl=en-GB).

### Clear descriptions

:white_check_mark: *The text that describes each user interface element is clear, concise, and meaningful*

For example, we can indicate a button for sharing an article with the description "share button". A description like this clearly communicates what kind of element has been selected (a button), how to interact with it (press), and the result of the interaction (share).

We should avoid descriptions that provide too much detail, extraneous information, or promotional calls to action. For example, it would *not* be appropriate to describe a share button as "button to share this article on Boris Johnson with your friends and family".


### Variable font size

:white_check_mark: *Text is displayed according to the user's preferred font size*

Both iOS and Android operating systems allow users to set a font size that best suits them. We should create user interfaces that respect a range of different font sizes for all textual elements.

*Note: There are some elements - e.g. navigation bar titles, tab bar titles, and the like - where this may not be possible.*


### Colour contrast

:white_check_mark: *Text is always legible against its background*

This is particularly important when displaying text over image backgrounds. For example, an image caption that uses white text could be completely illegible if the story is about [Snowmageddon](https://www.bbc.co.uk/bbcthree/article/f64389be-21fd-44ca-b135-d1e9f12624ee).

We should always consider accessible colour contrast for both light and dark modes.

### Out of scope

:no_good: The following features have been agreed as explicitly out of scope for our baseline:

* Bold Text (iOS)
* Motion Reduction (iOS)
* Increase Contrast (iOS)


### Further reading

[BBC Mobile Accessibility Guidelines](https://www.bbc.co.uk/accessibility/forproducts/guides/mobile/)

[Android Accessibility Developer Guidelines](https://developer.android.com/guide/topics/ui/accessibility/)

[iOS Accessibility Developer Guidelines](https://developer.apple.com/accessibility/ios/)