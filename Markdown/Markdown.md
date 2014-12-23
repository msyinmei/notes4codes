Markdown
========
Markdown is a plain text formatting syntax designed to convert into HTML and many other formats, using a free software tool written in Perl called "Markdown" that converts the plain text formatting written in the Markdown syntax into HTML.

This document is a simple cheatsheet for my own reference created using the Markdown syntax.

Official Sources & Links (really great references):
------
Syntax:
http://daringfireball.net/projects/markdown/basics

Syntax in Markdown: http://daringfireball.net/projects/markdown/basics.text

Practice via Dingus:
http://daringfireball.net/projects/markdown/dingus

Github Flavored Markdown: https://help.github.com/articles/github-flavored-markdown/

SYNTAX EXAMPLES:
================
Setext-style headers for `<h1>` and `<h2>` are created by underlining with (any number of) equal signs (`=`) and hyphens (`-`) respectively by typing it in the following line (row of text).

Atx-style headers are created by putting 1-6 hashmarks (`#`) at the beginning of the line (row of text). The number of the hashes equals the resulting HTML header level

Escaping:
P.S. I am able to type the hashtags and code above by escaping individual characters with the backtick '`' signs.
There are also many other ways of escaping.


##Github Flavored Markdown aka GFM##
Before we go forward with any Markdown syntax basics, I'd like to highlight the Github exceptions since ultimately much of the markdown I write will be for Readmes on github.

###URL autolinking (GFM)###
Github will autolink standard URLs (such as the ones above under links) instead of needing to set link text.

###Strikethrough (GFM)###
GFM adds syntax for strikethrough text, which is missing from standard Markdown. Use '~': '~'Mistaken text.'~' becomes:
~Mistaken text.~


##Basic Examples##

First Level Setext-style Header with equal signs
==========================================

Second Level Setext-style Header with hyphens
-------------------------------------

#First Level Atx-style Header

## Second Level Atx-style Header

### Third Level Atx-style Header

#### Fourth Level Atx-style Header

##### Fifth Level Atx-style Header

###### Sixth Level Atx-style Header

> This is a blockquote. Create a blockquote by using email-style '`>`' angle brackets.
>
> You can create paragraphs in the blockquote. This is the second paragraph.
>
> ## This is a h2 header in the blockquote

This is a regular paragraph, which is basically one or more consecutive lines of text separated by one or more blank lines. A blank line is a horizontal line of input that contains nothing but spaces or tabs. Normal paragraphs should not be indented with any spaces or tabs.


###Phrase Emphasis###
Using asterisks (`*`) to create `<em></em>`:
The last word is *emphasized*. The last words of this sentence are **strongly emphasized
with two asterisks**.

Using underscores (`_`) to create `<strong> </strong>`:
The last words is _emphasized_.
The last words of this sentence are __strongly emphasized with two underscores__.

However if you're using GFM (github flavored markdown), please note that while Markdown transforms underscores into italics, GFM ignores underscores in words to allow codes and names with multiple underscores to render properly.

###Lists###







