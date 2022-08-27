# Regex Tutorial

#### As a web developer, this tutorial was made in order to understand how Regular Expressions or Regex work to define a search pattern.

## Summary

#### A Regex or regular expression is a sequence of characters that define a search pattern, which are used by string-searching algorithms for "find" or "find and replace" operations on strings, also looks for input validation. This technique usualy developed in theoretical computer science.
#### Example of an Regex:
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

#### Follow the content below to understand each part of the example

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
#### While the two forward slash characters "/" are used to denote the boundaries of a regular expression, the "^" and "$" are the two anchors that signal the begin and the end of that regex.

#### There are also other two anchors "\b"  and "\B":

    \b Matches a word boundary position between a word character and non-word character or position (start / end of string). See the word character class (w) for more info.

    \B Matches any position that is not a word boundary. This matches a position, not a character.
    See Boundaries for more detailed Information

### Quantifiers

#### Quantifiers indicate that the preceding token must be matched a certain number of times. A quantifire can be greedy or lazy that is explained below.

a*a+a? -0 or more, 1 or more, 0 or 1

"+" Matches 1 or more of the preceding token.
"*" Matches 0 or more of the preceding token.
"?" Matches 0 or 1 of the preceding token, effectively making it optional.
"?" Makes the preceding quantifier lazy, causing it to match as few characters as possible. By default, quantifiers are greedy, and will match as many characters as possible.
a{5}a{2,} -Looks for exactly five, two or more

{2,6} -forces the input of characters between two & six characters long.

a+?a{2,}? -match as few as possible

ab|cd -match ab or cd

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
