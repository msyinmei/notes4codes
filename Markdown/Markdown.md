Markdown
========
Markdown is a plain text formatting syntax designed to convert into HTML and many other formats, using a free software tool written in Perl called "Markdown" that converts the plain text formatting written in the Markdown syntax into HTML.

This document is a simple cheatsheet for my own reference created using the Markdown syntax. Some of the descriptions/explanations are actually from the following resources below, which you can visit directly. I take no credit for this as this is only a reference created for myself.

Official Sources & Links (really great references):
------
Syntax:
http://daringfireball.net/projects/markdown/basics

Syntax in Markdown: http://daringfireball.net/projects/markdown/basics.text

Practice via Dingus:
http://daringfireball.net/projects/markdown/dingus

[Github Flavored Markdown](https://github.com/msyinmei/notes4codes/blob/master/Markdown/Markdown.md#github-flavored-markdown-aka-gfm): https://help.github.com/articles/github-flavored-markdown/

Guidelines/Tips & Tricks to Writing on Github: https://help.github.com/articles/writing-on-github/

EXAMPLES AND EXPLANATIONS:
---------------
Escaping:
P.S. I can escape individual characters with the backtick '`' signs.
There are other ways to escape as well

##Basic Examples##
Alright, time for some basics!


####Setext-style headers####
Setext-style headers for `<h1>` and `<h2>` are created by underlining with (any number of) equal signs (`=`) and hyphens (`-`) respectively by typing it in the following line (row of text).

```
First Level setext-style header with equal signs
==========================================
```

First Level setext-style header with equal signs
==========================================

```
Second Level setext-style header with hyphens
-------------------------------------
```

Second Level setext-style header with hyphens
-------------------------------------

####Atx-style headers####
Atx-style headers are created by putting 1-6 hashmarks (`#`) at the beginning of the line (row of text). The number of the hashes equals the resulting HTML header level

```
#First Level Atx-style Header

## Second Level Atx-style Header

### Third Level Atx-style Header

#### Fourth Level Atx-style Header

##### Fifth Level Atx-style Header

###### Sixth Level Atx-style Header
```

#First Level Atx-style Header

## Second Level Atx-style Header

### Third Level Atx-style Header

#### Fourth Level Atx-style Header

##### Fifth Level Atx-style Header

###### Sixth Level Atx-style Header



####Blockquotes####

```
> This is a blockquote. Create a blockquote by using email-style '`>`' angle brackets.
>
> You can create paragraphs in the blockquote. This is the second paragraph.
>
> ## This is a h2 header in the blockquote
```

> This is a blockquote. Create a blockquote by using email-style '`>`' angle brackets.
>
> You can create paragraphs in the blockquote. This is the second paragraph.
>
> ## This is a h2 header in the blockquote

####Paragraphs####
This is just a regular paragraph, which is basically one or more consecutive lines of text separated by one or more blank lines. A blank line is a horizontal line of input that contains nothing but spaces or tabs. Normal paragraphs should not be indented with any spaces or tabs.

####Phrase Emphasis####
Using asterisks (`*`) to create `<em></em>`:

```
The last word is *emphasized*. The last words of this sentence are **strongly emphasized
with two asterisks**.
```

The last word is *emphasized*. The last words of this sentence are **strongly emphasized
with two asterisks**.

Using underscores (`_`) to create `<strong> </strong>`:

```
The last words is _emphasized_.
The last words of this sentence are __strongly emphasized with two underscores__.
```

The last words is _emphasized_.
The last words of this sentence are __strongly emphasized with two underscores__.

NOTE: However if you're using Markdown on Github, please note that while Markdown transforms underscores into italics, the Github Flavored Markdown aka GFM ignores underscores in words to allow codes and names with multiple underscores to render properly.


####Lists####
Unordered bulleted lists use asterisks, pluses and hyphens as list markers.

```
Asterix list:
* Love
* Life
* Happiness

Plus sign list:
+ Love
+ Life
+ Happiness

Hyphen list:
- Love
- Life
- Happiness
```
All will create the following output:

```
<ul>
<li>Love</li>
<li>Life</li>
<li>Happiness</li>
</ul>
```

Asterix list:
* Love
* Life
* Happiness

Plus sign list:
+ Love
+ Life
+ Happiness

Hyphen list:
- Love
- Life
- Happiness



Ordered (numbered) lists use regular numbers followed by periods as list markers (be sure to have a blank line
beforehand):

1.   First
2.   Second
3.   Third

Output:
```
<ol>
<li>Red</li>
<li>Green</li>
<li>Blue</li>
</ol>
```

###Github Flavored Markdown aka GFM###
I'd also like to highlight the Github exceptions since ultimately much of the markdown I write will be for Readmes on github. I will refer to them as GFM.

####URL autolinking (GFM)####
Github will autolink standard URLs (such as the ones I've shared) instead of needing to set link text.

####Strikethrough (GFM)####
GFM adds syntax for strikethrough text, which is missing from standard Markdown. Use a set of tilde symbols (`~`) twice: `~~`Mistaken text.`~~` becomes:
~~Mistaken text.~~

###Fenced code blocks###
Standard Markdown converts text with four spaces at the beginning of each line into a code block; GFM also supports fenced blocks. Just wrap your code in ``` (as shown below) and you won't need to indent it by four spaces. Note that although fenced code blocks don't have to be preceded by a blank line—unlike indented code blocks—we recommend placing a blank line before them to make the raw Markdown easier to read.

```
Example:
function test(){
  console.log("this is a test using '```'")
}
```

    Example 2:
    function test2(){
      console.log("This is a test using four spaces '    '")
    }

Within lists, you must indent non-fenced code blocks *eight* spaces to render properly.

####Syntax highlighting (GFM)####
GFM uses Linguist (https://github.com/github/linguist) to perform language detection and syntax highlighting.

For keywords please visit https://github.com/github/linguist/blob/master/lib/linguist/languages.yml

Code blocks can be taken a step further by adding syntax highlighting. In your fenced block, add an optional language identifier and we'll run it through syntax highlighting. For example, to syntax highlight Ruby code:

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

####Tables (GFM)####
You can create tables by assembling a list of words and dividing them with hyphens (`-`) for the first row. Then to create columns, separate each column with a pipe (`|`).

The extra pipes on the ends are not necessary, and dashes at the top don't need to match the length of the header exactly.

```
|Column 1 Header | Column 2 Header|
|--------------- | ---------------|
|This is so      |  Manual        |
|Content Cell    |  Content Cell  |
|Discontent | Cell that refuses to match    |
|Here is a cell with |inline Markdown ~~strikethrough~~|
```

#####Here is what you get#####

|Column 1 Header | Column 2 Header|
|--------------- | ---------------|
|This is so      |  Manual        |
|Content Cell    |  Content Cell  |
|Discontent | Cell that refuses to match    |
|Here is a cell with |inline Markdown ~~strikethrough~~|


You can also align the text of the header row left, right or center by adding colons (`:`):
```
| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
```

Here is how that looks:

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |



