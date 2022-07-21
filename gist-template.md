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
    - [Grouping and Capturing](#grouping-and-capturing)
    - [Character Classes and Character Sets](#character-classes-and-character-sets)
    - [Greedy and Lazy Match](#greedy-and-lazy-match)
    - [Boundaries](#boundaries)
    - [Back-references](#back-references)
    - [Look-ahead and Look-behind](#look-ahead-and-look-behind)
  - [Author](#author)

## Regex Components

### Anchors

In a RegEx, Anchors are used to match a position within a string, not a character to be matched itself. There are a handful of Anchors that can be used, but we are using two of the most common in this email address RegEx. They are ^ and $.

The ^ is used to match a certain character or any character at the beginning of a string. The $ is used to match a certain character or any character at the end of a string.

Let's look at our RegEx: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Do you see the ^ that follows the first / and the $ that precedes the closing /? This tells us that our RegEx is looking for a certain set of characters, `([a-z0-9_\.-]+)`, to match at the beginning of the string and a certain set of characters, `([a-z\.]{2,6})` to match at the end of the string.

Now we know we are our string must begin and end with certain characters to pass our email test.

For example, example@regex.com would pass our anchor test because it starts and ends with characters that meet the specified criteria. However, @example@regex.com would fail because we have an unallowed @ in the beginning of our email address.

### Grouping and Capturing

Grouping and capturing refers to creating a substring (or a backreference) in a particular RegEx by enclosing a set of characters together within a pair of parentheses ().

If we look at our RegEx once more, `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, we can see we are creating 3 separate substrings within our overall RegEx.

Substring 1 precedes the @ symbol and is: `([a-z0-9_\.-]+)`

Substring 2 follows the @ symbol and is: `([\da-z\.-]+)`

Substring 3 follows the \. and is: `([a-z\.]{2,6})`

Do you see how we created 3 references and how this might be useful to us? Let's apply the above to our example email address: example@regex.com

Following our logic from our Groups - example would be our substring 1, regex would be our substring 2, and com would be our substring 3.

### Character Classes and Character Sets

A Character Set is used to define a set of characters to match. Within our 3 substring groups defined above, we also have 3 distinct Character Sets.

Within substring 1, we have: `[a-z0-9_\.-]`

Within the Character Set, there are a few things going on:

We are looking for any lowercase letter from a-z with the a-z
We are looking for any numeric character from 0-9 with the 0-9
We are looking for underscores with the _
We are looking for periods with the \..
Finally, we are looking for hyphens with the -
Within substring 2, we have: `[\da-z\.-]`

Much like substring 1, we are looking for lowercase letters, numbers, a period, or a hyphen. Notice we are excluding the underscore this time.
Wait a minute - how do we know we are searching for numbers in this Character Set? We don't see 0-9 this time.
Well you're right we don't see 0-9 explicitly stated, but the \d is a special statement within RegEx called a Character Class. \d is equivalent to writing [0-9] which is what we wrote in substring 1.
Character Classes are handy shorthand to match common sets of characters in RegEx.


### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

Cameron Cole is a student in the Univeristy of Minnesota Coding Bootcamp who is an aspiring to begin a career in software development. You can check out their github here: https://github.com/cam-cole

