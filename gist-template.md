# Email Regex Tutorial

Hello, everyone! My name is Cameron and today we are going to learn about regular expressions a.k.a regex.

## Summary

The regular expression we are covering today is matching an email - 

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

In this tutorial, we will break down each component of the regex above and explain how this expression allows us to search for all email addresses in a body of text.

## Table of Contents

- [Email Regex Tutorial](#email-regex-tutorial)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
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
  - [Author](#author)

## Regex Components

### Anchors

In a RegEx, Anchors are used to match a position within a string, not a character to be matched itself. There are a handful of Anchors that can be used, but we are using two of the most common in this email address RegEx. They are ^ and $.

The ^ is used to match a certain character or any character at the beginning of a string. The $ is used to match a certain character or any character at the end of a string.

Let's look at our RegEx: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Do you see the ^ that follows the first / and the $ that precedes the closing /? This tells us that our RegEx is looking for a certain set of characters, ([a-z0-9_\.-]+), to match at the beginning of the string and a certain set of characters, ([a-z\.]{2,6}) to match at the end of the string.

Now we know we are our string must begin and end with certain characters to pass our email test.

For example, example@regex.com would pass our anchor test because it starts and ends with characters that meet the specified criteria. However, @example@regex.com would fail because we have an unallowed @ in the beginning of our email address.

### Quantifiers

abc* -- matches a string that has ab followed by zero or more c  
abc+ -- matches a string that has ab followed by one or more c

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

Cameron Cole is a student in the Univeristy of Minnesota Coding Bootcamp who is an aspiring to begin a career in software development. You can check out their github here: https://github.com/cam-cole

