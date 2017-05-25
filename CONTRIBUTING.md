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
  - For wikidot/scp-wiki widget inclusions (those that have a relevant url) copy the regexp that's already used, modifying the relevant parts. The SCP wiki can be reached both through `www.scp-wiki.net` and `scp-wiki.wikidot.com`, so keep that in mind.

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

[css-beautify](https://github.com/beautify-web/js-beautify) has been used to format the stylesheet. It currently has a [bug](https://github.com/beautify-web/js-beautify/issues/609) that causes it to gobble up blank lines that should normally be left alone. If you happen to accidentally mess up the code style while working on the theme, use `css-beautify` and then make sure to add the blank lines around headers.

## Test targets

**SPOILERS AHEAD**

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
