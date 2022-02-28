# Regex Tutorial for URL matching.

A regular expression ( regex or regexp; also referred to as rational expression)) is a sequence of characters that specifies a search pattern in text. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. It is a technique developed in theoretical computer science and formal language theory.

## Example:
The following regex can be used to validate a URL and has been broken down in this tutorial by its components (anchor, quantifies, grouping constructs, bracket expressions, character classes, and character escapes). Each section describes the symbol, a description, and where the code is found within the regex.

```regexp
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/ 
```

**Explanation:**

-`/` Begins Regex
-`^` This is always at the begining of the string, to position the anchors.
-`(` Groups together multiple "tokens" to create a capture group. This can be used to retrieve a substring or backreference.
-`https` This indicates a sub-expression string that should be matched. "s"
- `?` This is a Greedy quantifier, which is basically denoting 0 or 1 occurrence of previous character (s) either http or https
^^ not 100% on this, pretty sure it takes a way the 's' from http
- `\/\/` This is an escaped character 
- `)` This Ends the capture grouped.
- `?` Greedy quaintifier indicating the entire previous section wrapped in () is optional. You can have it or not.
- `(` Begins captured group.
- `[` Begins bracket list.
- `/d` Is a metacharacter indicating any one digit character (0-9)
- `a-z` Indicates lower case letters between a-z.
- `\.` Escape sequence denoting the character `.`
- `-` Indicates `-` character
- `]` Ends bracket list.
- `+` Because its outside the brackets the Greedy quantifier is denoting that the previous bracket list characters, may occur one or more times.
- `)` Ends captured group.
- `\.` Escape sequence denoting the character `.`
- `(` Begins captured group.
- `[` Begins bracket list.
- `a-z.` Indicates lower case letters between a-z.
- `]` Ends bracket list.
`{2,6}` Occurence indicator denoting the previous bracket list characters may occur from 2 to 6 times.
- `)` Ends captured group.
- `(` Begins captured group.
- `[` Begins bracket list.
- `/` Escapes regex to match the character `/`
- `\w` Is a character class indicating any dingle Word Characters. Those are any characters including a-z, A-Z, 0-9, and _.
- `.` Escape sequence denoting the character `.`
- `-` Indicates `-` character
- `]` Ends bracket list.
- `*` The Greedy quantifier denoting that the previous bracket list characters may occur zero or more times
- `)` Ends captured group.
- `*` Greedy quantifier indicating that the entire previous captured group may occur zero or more times.
- `/` Escapes regex to denote a regular `/` character
- `?` Greedy quantifier indicating previous `/` character may have 0 or 1 occurrences.
- `$` Position acnhoring that ends the string.
- `/` Ends Regex.


## Regex Components

### Anchors

Anchors belong to the family of regex tokens that don't match any characters, but that assert something about the string or the matching process. Anchors assert that the engine's current position in the string matches a well-determined location: for instance, the beginning of the string, or the end of a line.

```text
^               Matches any string that starts with
$               Matches a string that ends with 
```


### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. 

- `* and *? `           Matches Zero or more times. 
- `+ and +? `           Matches One or more times.
- `? and ?? `           Matches Zero or One times.
- `{n} and {n}? `       Matches exactly n times.
- `{n,} and {n,}?  `    Matches atleast n times.
- `{n,m} and {n,m}? `   Matches from n to m times.

Examples include:

```text
https?          Because of the `?` Matches 'https', 'http'. 
[\da-z\.-]+     Because of the `+` it matches a single digit, group of letters (a-z), dot (.) or hyphen (-) 1 or more times
[a-z\.]{2,6}    Because of the `{2,6}` it matches 2 to 6 copies of the sequence [a-z\.]
[\/\w \.-]*     Because of the `*` it matches '/', '.', '-', 'www', '//'
```

### Character Classes

Character Classes ensure that a smaller series of characters matches a bigger series of characters. 


```text
[a-z]          Matches lowercase alphabetic characters between a and z
\w             Matches a single word
\d             Matches a single character that is a digit 0-9
.              Matches any character
```

### Grouping and Capturing


By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together. This allows you to apply a quantifier to the entire group or to restrict alternation to part of the regex. Only parentheses can be used for grouping.

```text
(https?:\/\/)     This group is basically saying it allows the URL code to being with "http://", "https://" or none of them.
([\da-z\.-]+)     This group which is the domain name. It matches 1 or more numbers, letters, dots or hypens. Ending it with a "+" linking it to the following line.
([a-z\.]{2,6})    Withe the + connecting this group together, this matches 2-6 copies of the sequences "[a-z\.]"
([\/\w \.-]*)     This group is is being matched as many times as they want because of the "*" at the end. Basicallly acting like multiple directories. (refer back to Group project 2).

```

### Bracket Expressions

Bracket expressions are expressions between square brackets "[]". In the example below, we have the following Bracket Expressions.

```text
[\da-z\.-]
[a-z\.]
[\/\w \.-]
```

### Greedy and Lazy Match

Greedy quantifiers try to match the longest text that matches a given pattern. Greedy quantifiers work by first reading the entire string before trying any match. If the whole text doesn't match, remove the last character and try again, repeating the process until a match is found.

The lazy mode of quantifiers is an opposite to the greedy mode. It means: “repeat minimal number of times”.

```text
([\da-z\.-]+)       The "+" operator is greedy as it allows character matching from one to an infinite amount of times.
```


## Author

Kamyar Assadipour
https://github.com/assadipourk/Regex-Tutorial
Email: Assadipourk@gmail.com

## User Story

```text
AS A web development student
I WANT a tutorial explaining a specific regex
SO THAT I can understand the search pattern the regex defines
```

## Acceptance Criteria

```text
GIVEN a regex tutorial

WHEN I open the tutorial.
THEN I see a descriptive title and introductory paragraph explaining the purpose of the tutorial, a summary describing the regex featured in the tutorial, 
a table of contents linking to different sections that break down each component of the regex and explain what it does, and a section about the author with a link to the author’s GitHub profile.

WHEN I click on the links in the table of contents.
THEN I am taken to the corresponding sections of the tutorial.

WHEN I read through each section of the tutorial.
THEN I find a detailed explanation of what a specific component of the regex does.

WHEN I reach the end of the tutorial.
THEN I find a section about the author and a link to the author’s GitHub profile.
```

## Table of Contents:

- [Anchors](#Anchors)
- [Quantifiers](#Quantifiers)
- [Character Classes](#Character-Classes)
- [Grouping and Capturing](#Grouping-and-Capturing)
- [Bracket Expressions](#Bracket-Expressions)
- [Greedy and Lazy Match](#Greedy-and-Lazy-Match)
- [Author](#Author)
- [User Story](#User-Story)
- [Acceptance Criteria](#Acceptance-Criteria)