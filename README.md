SCP Wiki Night Mode
===================

This is the repository for the [SCP Wiki Night Mode](https://userstyles.org/styles/118617/scp-wiki-night-mode) userstyle. It is a dark, low-contrast theme for the SCP Wiki, intended to make it easier to read in the dark.

Original by [LurkD](http://www.wikidot.com/user:info/lurkd), [anqxyr](http://www.wikidot.com/user:info/anqxyr) and [Crayne](http://www.wikidot.com/user:info/crayne).

Original thread is [here](http://www.scp-wiki.net/forum/t-1353913/help-wanted) on the SCP Wiki.

The complete list of contributors is in [`CONTRIBUTING.md`](CONTRIBUTING.md).

Installing
----------

The supported way to install the theme is to use [Stylish](https://userstyles.org/), which is available for [Firefox](https://addons.mozilla.org/en-US/firefox/addon/stylish/), [Chrome](https://chrome.google.com/webstore/detail/stylish-custom-themes-for/fjnbnpbmkenffdnngjfgmeleoegfcffe), [Opera](https://addons.opera.com/en-gb/extensions/details/stylish/) and [Baidu](https://chajian.baidu.com/2015/#search/stylish/fjnbnpbmkenffdnngjfgmeleoegfcffe).

_If you use a different browser, you're on your own. However, if you have already figured out how to support a different browser and you think something can be done about it without too much work, feel free to open an issue and make your suggestions._

The recommended way to install the theme is from the [above link on `userstyles.org`](https://userstyles.org/styles/118617/scp-wiki-night-mode). Please use `userstyles.org` to install the main theme - it allows metadata, possible future customization and is easier for everyone.

This repo also has separate CSS files with optional font changes and fixes for SCP Wiki-related userscripts that can be used separately by manually importing them to Stylish. There are in the `css` directory. To install those:
  - Visit the link on the table that corresponds to the file you want
  - From your Stylish toolbar button drop-down, select "Install File..."
  - Stylish will tell you which URLs the style affects and ask you for a name for the style. Give it a meaningful one. You can also preview the changes before you install the style.

**Style addon**|**Link**|**Description**
:-----:|:-----:|:-----:
Fonts|[RawGit](https://rawgit.com/anqxyr/scp-night/master/css/fonts.css)|A different set of fonts for the wiki
Fonts (with exclusions)|[RawGit](https://rawgit.com/anqxyr/scp-night/master/css/fonts-with-exclusions.css)|The custom fonts but not applied to pages using custom themes

Userscript-related fixes:

**Userscript**|**Link**|**Fixes**
:-----:|:-----:|:-----:
[Real Rating Info](http://www.scp-wiki.net/usertools#toc13)|[RawGit](https://rawgit.com/anqxyr/scp-night/master/css/userscript-real-rating-info-fixes.css)|Heritage rating widget layout

Doing it through Stylish's menu allows automatic updates for those files. If that's _not_ what you want, then just download the repo and copy-paste the files into Stylish manually. For instructions on how to create a style that way, check Stylish's help. To download the repo, use the button on the top right.

These links use [RawGit](https://rawgit.com/) and as such there are no uptime guarantees. If they don't work, just try again later.

Contributing
------------

If you want to add a fix or add to the theme in general, read [`CONTRIBUTING.md`](CONTRIBUTING.md) first.

Reporting bugs and making suggestions
-------------------------------------

  - Opening an issue in this repo is the preferred way to report bugs. If you don't have and don't want to make a GitHub account, use the original forum thread instead.
  - The same applies to suggestions.
  - If an issue is related to a specific page or SCP document, prefix the issue with "Page bug: ". There is no need to add the title, but feel free to do so if it's short. Use a descriptive name for the issue please (especially if there's a lot of open issues already).
