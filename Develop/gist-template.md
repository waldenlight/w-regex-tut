# Dissecting an Email Regex

If you've ever used regular expressions before, you probably know how these character strings are a whole world of their own. It's almost as if they are Marvel or Star Wars characters with this whole cinematic universe built around them. Now they may seem a little daunting, but maybe by the end of this you'll see how these guys are just as deserving of the big screen as Spider-Man or any one of the Skywalkers.

Here, I'll break down one of the most common regex's: the common email id. By analyzing this specific regualr expression, we'll better understand them as a whole.

## Summary

First, let's talk about what a regex really is. A regular expression, simply put, is a string of characters that allow us as developers to search for more general patterns in our files. In this example, we will be looking at a regex that will search for any instance of an email address. 

With out further ado, here is the regex we will be looking at:

```
/^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6})*$/
```

Beautiful, isn't it?

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

Let's analyze the specific components of this regex:

The `/` at the beginning and end denotes that this is indeed a regex. When you enter a regex into a search and replace bar in a text editor (depending on which one you use), for example, you may need to insert these slashes to show that you are using a regex.

The parenthesis `()` denote a subexpression. These look for an exact match unless told to do otherwise. Just another one of the superpowers regular expressions have.

Anything inside the brackets `[]` represent a range of characters that we want to match. Since there are multiple sets of brackets, let's explain what each one does:

* The first set of brackets is for the username of the email address. `a-zA-Z0-9` tells us that any alphanumeric characters can exist in this part of the string. The special characters `._%-` are also included.

* The second set of brackets is for the domain name of the email address. Again, all alphanumeric characters are acceptable, but only `.` and `-` can be the special characters.

* The third set of brackets is for the top level domain of the domain name (the .com, .net, .org, etc). This can only be alphabetical characters due to the `a-zA-Z`.

The `@` in the middle is nothing special. It's a literal character as it isn't within any brackets. This means that there must be an `@` symbol between the username and the domain name, aligning our search with the structure of all email addresses.

Finally, the backslash `\` is to escape the `.` immediately after it. Otherwise, this `.` would be interpreted as a regex operation rather than a literal character. Just like the `@`, there is a `.` in every email address, so we put it in there literally.

### Anchors

Like many regular expressions, this one incorporates anchors. Anchors are not characters to be searched for. Instead, they give other information about the string, usually about it's structure.

The `^` anchor at the beginning of the regex requires that the search results should start with the characters following the `^`.

The other anchor we see is the `$` at the end that tells the computer to search for any string that ends with the characters that precede it. So it's essentially saying search for anything that matches all this.

### Quantifiers

A quantifier, in the regex cinematic universe, sets a limit on the string. Here are some of the quantifiers we see in this regular expression:

After the username and domain of the email, there is a `+`. This little guy explains that anything matching the username specifications one or more times must be searched for.

After the top level domain, there is `{2,6}`. This means the amount of characters in this section must be 2 to 6 characters. Pretty cool, eh?

There is also an asterisk `*` after the subexpression to inform us that we are searching for anything that matches the pattern zero or more times.

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
