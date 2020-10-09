# Accessibility - Our Baseline Commitment

## Talk Back / Voice Over

It is important that we always support navigation using audio cues on both platforms, to support our visually impaired users. The level of fidelity, however, must be determined by the fidelity of the feature at the time.

This means, for a new experimental feature that we want to test with our users, it should be usable via Talk Back and/or Voice Over.

So, if, for example, a Promo needs every element swiping through in order to have it read out, that is likely okay at this stage.

However, if the feature is matured, or as it matures (and we become confident that it is working), then we must revisit this and commit more time to improving it.

Continuing the example above, we might then improve the read out to group the elements of the Promo into one sentence and swipe.

## Dynamic Type

Text within the apps must correspond to the users preferred text size, at the operating system level.

There are, of course, exceptions to this, such as navigation bar titles, tab bar titles, and the like, where the operating system does not permit such changes.

## Accessibility Identifiers
*(not to be confused with traits or labels)*

Every logical user interface element, or grouping, must have an accessibility identifier. These identifiers power many “out of the box” accessibility features, as well as our user interface tests, and so must be a part of every piece of work we do.

## Further Considerations

### On Traits and Labels

The labels you choose need to be clear and usable _as an accessibility user_.

For example, just reading out ‘button’ is unlikely to be helpful, whereas ‘share button’ explains clearly what the element is (a button), how to interact with it (press), and what will happen when that is done (share). Equally, be aware of not giving too much detail, extraneous information, or promotional call to action...e.g. ‘button to share this article on Boris Johnson with your friends and family’ - they can get the details from the context and certainly don't need to be pitched to use it.

## On Colour Contrast

Consider whether text is readable on any background (coloured or otherwise) in both light and dark modes.

For example, take a look at the captions that overlay the article images - they could easily be completely unreadable if the text is white and the story is about [Snowmageddon](https://www.bbc.co.uk/bbcthree/article/f64389be-21fd-44ca-b135-d1e9f12624ee).

## References:

https://www.bbc.co.uk/accessibility/forproducts/guides/mobile/
