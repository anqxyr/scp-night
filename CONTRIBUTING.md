#### Current contributors:

  - [LurkD](http://www.wikidot.com/user:info/lurkd)
  - [anqxyr](http://www.wikidot.com/user:info/anqxyr)
  - [Crayne](http://www.wikidot.com/user:info/crayne)
  - [MechaLynx](http://www.wikidot.com/user:info/mechalynx)
  - [Scorpion451](http://www.wikidot.com/user:info/scorpion451)

Contribution guidelines
=======================

  - Try to keep the code style consistent. Pull requests may be modified and turned into joined commits with style adjustments.
  - Try to avoid hardcoding values that don't need to be hardcoded. Examples would be url matching and element sizes.
  - If you want to make major changes to the base theme it is recommended to open up an issue about it first, to avoid wasting time in changes that may not be merged. If you've already made the changes, go ahead and make a pull request anyway if you want.
  - Don't commit unrelated changes as a single pull request if at all avoidable. Break the changes into separate pull requests (this applies to cases where you have multiple page-specific fixes, for example). On GitHub, each pull request corresponds to a branch, not a commit, so you'll have to make a branch on your fork for each change, then make a pull request for each of the branches separately.
  - Add exclusions to pages by using the main `document` header regexp. "Osanshouo" was the first exclusion - if there aren't any others yet, just put parenthesis around it and separate each exclusion with `|` within the parenthesis.
  - Generally, if a wiki page has its own unique style, it's a good idea to just add it to the exclusions instead of trying to override special styles which can be thematically important to the article or story anyway.
  - For wikidot/scp-wiki widget inclusions (those that have a relevant url) copy the regexp that's already used, modifying the relevant parts. The SCP wiki can be reached both through `www.scp-wiki.net` and `scp-wiki.wikidot.com`, so keep that in mind.

_If you need help testing and debugging regular expressions to see if they match the URLs properly, you can use [RegExr](http://regexr.com/) or [regex101](https://regex101.com/)._

## Style guide

_This is meant as a reference in case the style of the CSS is unclear._
_When in doubt, favor consistency with the rest of the file and clarity._

  - Section separators are like this:

        /* ------------------------------------------------------------- */

    - it is a CSS comment with 60 dashes contained and spaces at both ends
    - if you need to add descriptive text, replace the dashes
      - spaces within text are ok, dashes are also ok
    - always have 3 dashes from the start
    - if more than 54 characters are needed for text, make a new line with the same style
    - for lengthy descriptions, use C-style comment blocks instead

  - Section headers are like this:

        /* ------------------------------------------------------------- */
        /* -----------------------RATING-WIDGET------------------------- */
        /* ------------------------------------------------------------- */

    - unlike separators, all characters must be capitalized
    - don't use spaces, only dashes

  - Fix wrappers start with a section separator and are optionally terminated by:

        /* --- */

    - fixes to existing styles do not need to be enclosed
    - page-specific fixes, as well as fixes for widgets and the like, must be enclosed
    - fix headers can be terminated by the header of another fix

The general rule is, whatever is semantically part of the main theme is not enclosed, whatever is there to fix the look is enclosed.

  - Separators and headers always have a blank line before and after

  - Indentation uses 2 spaces, no tabs
  - Rules have empty lines between them

[css-beautify](https://github.com/beautify-web/js-beautify) has been used to format the stylesheet. It currently has a [bug](https://github.com/beautify-web/js-beautify/issues/609) that causes it to gobble up blank lines that should normally be left alone and add new blank lines where it shouldn't. If you happen to accidentally mess up the code style while working on the theme, use `css-beautify` and then make sure to add the blank lines around headers.

## Test targets

### WARNING: SPOILERS AHEAD

The following pages should be used to test theme features. If you make a change and want to make sure it doesn't break something obscure that is already known, try all these links with your modified style active.

**Feature**|**Test pages**|**Status**
:-----:|:-----:|:-----:
Invisible text|[SCP-000](http://www.scp-wiki.net/scp-000)|works
Search widget| |works
Time widget| |works
Forum tables| |works
Main page panels| |works
Hub pages| |works
Heritage rating widget|[SCP-173](http://www.scp-wiki.net/scp-173)|works

## How to fix certain issues

If you're not experienced with CSS, the following information may be useful to you in certain cases.

  - Images that depend on the default theme

    There are images which expect the background to be white, the text to be black etc. These can be fixed by applying an [`invert`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter#invert%28%29_2) filter to the image. This is done using the [`filter`](http://caniuse.com/#feat=css-filters) CSS property.

    A partial inversion is possible, allowing us to easily and quickly match the image with the rest of the theme in most cases. Just be sure to select the specific image so that you don't accidentally apply the rule more generally than needed:

    ```css
    img[alt="nameofimage.png"] {
      filter: invert(87.5%);
    }
    ```

    Most black on white images can match a low-contrast, white-on-black theme (like this one) by using this amount of inversion. Adjust until it is as seamless as you can get it (or rather matches how seamless the original was intended to be, as best you can tell).

    `img` tags generally don't have CSS ids within articles, but you can use their alt text instead. Using the `src` can also work, as can other attributes, but the alt text is almost always present and is the cleanest to match, as well as semantically appropriate (the image URL might change because it's getting sourced from elsewhere, while the image remains the same - matching the alt text allows the theme to keep working properly).

    Note that this generally works best for grayscale images. Color images will end up looking funky, but in some cases (such as images that have nothing but colored text and the color of the text doesn't matter), that's acceptable. Use your own best judgment.

    _This will not work with images set as the background of an element. Instead try the next fix._

  - Background images that depend on the default theme

    This is trickier. Filters can't be applied to background images separately, so if you were to attempt it, you'd notice it inverts the entire element (which for an article means everything within the container who's background you want to invert).

    I'll draw from an existing page where this is fixed, the March Madness Hub page:

    ```css
    #page-content>div:before {
      content: " ";
      position: absolute;
      left: 0px;
      top: 0px;
      z-index: -1;
      display: block;
      background: inherit;
      width: 100%;
      height: 100%;
      filter: invert(91.5%);
    }
    #page-content>div {
      z-index: 0;
      position: relative;
    }
    ```

    The fix uses a pseudoelement that inherits the background image, inverts it, then overlays it on top of the old background but under all other content on its parent.

  - Part of a page seems to ignore all styles

    You're probably dealing with an iframe embed. Examples of these are the timer and search widgets. To match them, you need to create a new `@-moz-document` rule and add their url to it. See the styles for the timer widget and search widget fix for examples.

    One way to get the url is to Shift + Right Click on the offending part of the page and "Inspect Element". This should open the developer tools. Try to find the parent `iframe` element and check its URL. Test it by pathing to it using the browser - if you get the same widget, you've found it. Make sure the rule you place in the CSS matches the _final_ URL, the one your browser shows when you get there. Redirects and server-side URL rewriting can confuse the matter (though generally this is not the case on wikidot).
