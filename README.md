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
##### While the two forward slash characters "/" are used to denote the boundaries of a regular expression, the "^" and "$" are the two anchors that signal the begin and the end of that regex.
##### There are also other two anchors "\b"  and "\B":

* \b Matches a word boundary position between a word character and non-word character or position (start / end of string). See the word character class (w) for more info.

* \B Matches any position that is not a word boundary. This matches a position, not a character.
    See Boundaries for more detailed Information
##### Examples:
```
^Hello          matches any string starting with `Hello`
World$          matches any string ending with `World`
^Hello World$   matches exact string
goodbye         matches any string that has the exact text `goodbye` in it
```

### Quantifiers
##### Quantifiers indicate that the preceding token must be matched a certain number of times. A quantifire can be greedy or lazy that is explained below.
##### Examples:

``` 
a*a+a? -0 or more, 1 or more, 0 or 1
"+" Matches 1 or more of the preceding token.
"*" Matches 0 or more of the preceding token.
"?" Matches 0 or 1 of the preceding token, effectively making it optional.
"?" Makes the preceding quantifier lazy, causing it to match as few characters as possible. By default, quantifiers are greedy, and will match as many characters as possible.
a{5}a{2,} -Looks for exactly five, two or more
{2,6} -forces the input of characters between two & six characters long.
a+?a{2,}? -match as few as possible
ab|cd -match ab or cd
```

### OR Operator
##### The "or" operator within a regular expression is defined using the "|" element. The or operator indicates that it could either of the components that we are separating with the "|"
##### Examples: 
``` /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
For this regular expression we have ([a-f0-9]{6}|[a-f0-9]{3}). 
The or operator separating these 2 components. 
This means that our regular expression values could either be 6 characters [a-f0-9]{6} or 3 characters [a-f0-9]{3}.
```
### Character Classes
##### Character classes tells us what type of characters to expect.
##### Examples: 
```
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
In this example character classes are confined within brackets []. 
The 2 character classes: [a-f0-9] and [a-f0-9] whish search for the same values. 
a-f searches for letters a-f and 0-9 searches for digits 0-9.
```
### Flags
##### Flags are also called modifiers because they modify the output of a regular expression. These flags can be used in any order or combination, and are an integral part of the RegExp.
##### Examples of Flags are as follows:
* `g` - Global, does not return after the first match, which restarted any subsequest searches from the end of the previous match (Makes the expression search for all occurences)
* `m` - Multi-line, when enabled the Anchors (^ $) will match the start and end of a line, rather than the whole string
* `i` - Insensitive, makes the entire expression case-insensitive
##### Examples:
```
/Hello/g   matches all `Hello` in the test
/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself
/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```

### Grouping and Capturing
##### Grouping unifies a pattern or string so that it is matched in a complete block
##### Examples:
* `()` - parentheses creates a capture group
* `(?:)` - using `?:` disables the capturing group
* `(?<>)` - using `?<>` puts a name to the group
* Examples:
```
x(yz)           parentheses create a capturing group with value yz
x(?:yz)*        using ?: we disable the capturing group
x(?<bar>yz)     using ?<bar> we put a name to the group
```

### Bracket Expressions
##### Bracket expressions signify the beginning of a character class or quantifier statement. In our example we use parenthesis to define our bracket expressions.
##### Examples: 
```
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
The parenthesis defines bracket expressions.
```

### Greedy and Lazy Match
##### A greedy match tries to match an element as many times as possible. Whereas, a lazy match tries to match an element as few times as possible. 
##### Examples: 
```
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
In this example we have ? which signifies lazy quantifier. 
This is referred to a lazy quantifier because it causes the regular expression engine to match as few occurances as possible. 
We can simply turn this lazy match into a greedy one by adding a ?.
```

### Boundaries
##### Boundaries are the places between characters. A Boundary should be considered as a wall between any adjacent characters. There are two types of Boundaries, **Word** and ***Non-Word**, each denoted by a specific character.
##### Examples:
* `\b` - A position that bounds a word, or where a word starts or ends. It denotes a place between a word and non-word character, at the start and end of a string.
* `\B` - Exact opposite of a word boundary, the negation of `\b` and will match **any position a word boundary doesnt.** *
* `*`Will match between a word and word character, as well as between a non-word and non-word character.
##### Examples:
```
`Hello World` has 12 total Boundaries with 8 Word Boundaries as seen below:
|H|e|l|l|o| |W|o|r|l|d|
^ ^ ^ ^ ^ ^ ^ ^ ^ ^ ^ ^
N W W W W N N W W W W N  -  N = Nonword Boundary \ W = Word Boundary
\bxyz\b     matches a "whole words only search" for the string `xyz`
\Bxyz\B     matches only if the pattern is fully surrounded by word characters `txyzt` 
it would match the string `xyz` because it only has word boundaries
```

### Back-references
##### Backreferencing is the name given to the action of using these matches. Backreferencing is the reference of a captured match, save in memory, by a captured group
##### Examples:
```
([xyz])\1              using \1 it matches the same text that was matched by the first capturing group
([uwx])([yz])\2\1      we can use \2 (\3, \4, etc.) to identify the same text that was matched by the second (third, 
fourth, etc.) capturing group
(?<bar>[xzy])\k<bar>   we put the name bar to the group and we reference it later (\k<foo>). 
The result is the same of the first regex
```

### Look-ahead and Look-behind
##### Look-ahead and Look-behind (lookaround) are `start and end` zero-length assertions [Anchors](#anchors) but they actually match characters, then ends the match, returning only the result: **Match or No Match**. They do not cosume characters in the string, but only assert wether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.
##### Examples:
```
h(?=t)       matches a h only if is followed by t, but t will not be part of the match
(?<=t)h      matches a h only if is preceded by an t, but t will not be part of the match
```

## Author

Khanh Tran

Khanh Tran is a Medical Technician. He is attending and finishing Fullstack Developer at UC Berkeley.

GitHub: [KhanhTran](https://github.com/Khanh-T-Tran)
