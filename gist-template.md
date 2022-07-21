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
    - [Quantifiers](#quantifiers)
    - [Components Put Together](#components-put-together)
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

Following our logic from our substrings - example would be our substring 1, regex would be our substring 2, and com would be our substring 3.

### Character Classes and Character Sets

A Character Set is used to define a set of characters to match. Within our 3 substrings defined above, we also have 3 distinct Character Sets.

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


### Quantifiers

Quantifiers in a RegEx are a way for us to tell the RegEx search pattern how many matches we would like for a particular set of characters. There are a few different quantifiers that could be used and we'll addresss the ones specific to our chosen RegEx.

Our RegEx contains 2 different quantifiers used 3 total times.

The first quantifier we use is present in substrings 1 and 2 from our grouping section. It is the + character.

Let's look at substrings 1 and 2 from above: `([a-z0-9_\.-]+)` and `([\da-z\.-]+)`.

Basically, in substring 1, the RegEx engine is looking to match any number of any character specified in the Character Set that precedes the @ symbol. This makes sense because we don't know what characters our users' email addresses will contain before the @, but we do know they will contain some combination of letters, numbers, periods, hyphens, and underscores.

The same logic can be applied to substring 2.

In substring 3, we forgo the + for two numbers within a set of curly braces. Let's take a look: `([a-z\.]{2,6})`

{2,6} follows our Character Set defined in substring 3. Like the + this is telling the RegEx engine to look for a certain number of the preceeding Character Set characters but, this time, we are explicitly telling it the number of characters it is allowed to match.

We want substring 3 to contain a minimum of 2 characters and a maximum of 6 characters. Any number between and inclusive of these two numbers is also allowed. Yet again, our illustrative email - example@regex.com fits these criteria.

### Components Put Together

Let's look at our RegEx once last time: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

After reviewing the sections above, we should understand the following:

* `^([a-z0-9_\.-]+)` is looking to ensure that our email address starts with (indicated by the `^`) any combination (and number) of lowercsae letters, numbers, underscores, hyphens, or periods and that this combination occurs before an `@`. 
* `([\da-z\.-]+)` is looking to ensure that our email address contains any combination (and number) of lowercase letters, numbers, hyphens, or periods between the `@` and the period `\.`.
* `([a-z\.]{2,6})$` is looking to ensure that our email address ends with (indicated by the `$`) any combination of lowercase letters or periods so long as the combination is between 2 and 6 characters.

Look at the following email addresses:
* `example@regex.com`
  * This email address would pass all the specified tests of the RegEx since it does not contain any dissallowed characters and the different character groups, especially substring 3, meet the length criteria. 
* `@example@regularexpressions.com`
  * This email addresss would fail because the first substring contains a disallowed character, the `@`.
* `bob@test.programmingisfun`
  * This email address would fail because the domain extension exceeds the 2-6 character limit imposed by the quantifier `{2,6}` in substring 3. 

## Author

Cameron Cole is a student in the Univeristy of Minnesota Coding Bootcamp who is an aspiring to begin a career in software development. You can check out their github here: https://github.com/cam-cole

