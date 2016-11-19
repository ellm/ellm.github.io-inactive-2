---
layout: page
title: Tooling
permalink: /notes/tooling
---

# TextEditors / Tooling

# Sublime Text

### Packages:
- SublimeCodeIntel
- SublimeLinter
- PlainTasks
- MarkdownEditing
- JavascriptNext - ES6 Syntax
- GitStatusBar
- GitGutter
- Gist
- DocBlockr
- Color Highlighter
*below work together for SCSS highlighting and autocomplete*
- Syntax Highlighting for Sass
- Sass for TextMate/Sublime Text 2 & 3

# iTerm / Terminal
- Oh My Zsh
- Hub (for github)
- Homebrew

# Atom

1.  Growing community and development of Atom
2.  The linter in Atom has a great UI
3.  Atom is built with HTML/CSS and JS which makes for a great Front-end text editor.
4.  Atom has great Intellisense and autocomplete. Much more comprehensive and robust than Sublime text.
5.  Atom has IDE like features such as autocomplete for user defined variables, mixins when writing in syntax such as SCSS.
6.  Atom has Github and VC features status monitoring built-into the UI.

### Packages

1.  [atom-beautify](https://atom.io/packages/atom-beautify) - reformats your code automatically using [JSBeautifier](https://github.com/beautify-web/js-beautify)
2.  [linter-jshint](https://atom.io/packages/linter-jshint) - linter using JShint
3.  [linter-jscs](https://atom.io/packages/linter-jscs) - Js code style checker
4.  [emmet](https://atom.io/packages/emmet) - tool to expand shorthand coding
5.  [pigments](https://atom.io/packages/pigments) - A package to display colors in project and files
6.  [wordpress-api](https://atom.io/packages/wordpress-api) - Autocomplete and snippets for WordPress development
7.  [linter-phpcs](https://atom.io/packages/linter-phpcs) - Php code linting (also see: [Install PHP CodeSniffer with Composer](https://tommcfarlin.com/php-codesniffer-with-composer/ "Install PHP CodeSniffer with Composer") and [Configure Php CodeSniffer for Mac OSX](http://viastudio.com/configure-php-codesniffer-for-mac-os-x/))

### Open Sublime from the commandline

Find Path
`echo "$PATH"`

Should return default Path in OSX
`/usr/local/bin/`

Creates A Symlink to Sublime script
`ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl`

# Link
http://olivierlacan.com/posts/launch-sublime-text-3-from-the-command-line/