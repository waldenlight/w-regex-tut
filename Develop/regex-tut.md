# The Regex Cinematic Universe

If you've ever used regular expressions before, you probably know how these character strings are a whole world of their own. It's almost as if they are Marvel or Star Wars characters with this whole cinematic universe built around them. Now they may seem a little daunting, but maybe by the end of this you'll see how these guys are just as deserving of a Hollywood premier as Spider-Man or any one of the Skywalkers.

Here, I'll break down one of the most common regex's: the email id. By analyzing this specific regualr expression, we'll better understand them as a whole.

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

The `@` in the middle is nothing special. It's a literal character as it isn't within brackets or anything. This means that there must be an `@` symbol between the username and the domain name, aligning our search with the structure of all email addresses.

Finally, the backslash `\` is to escape the `.` immediately after it. Otherwise, this `.` would be interpreted as a regex operation rather than a literal character. Just like the `@`, there is a `.` in every email address, so we put it in there literally.

There are more complex regex components incorporated here, and we'll get into them now.

### Anchors

Like many regular expressions, this one incorporates anchors. Anchors are not characters to be searched for. Instead, they give other information about the string, usually about it's structure.

The `^` anchor at the beginning of the regex requires that the search results should start with the characters following the `^`.

The other anchor we see is the `$` at the end that tells the computer to search for any string that ends with the characters that precede it. So it's essentially saying search for anything that matches all this.

These anchors are also boundaries, which we get into below.

### Quantifiers

A quantifier, in the regex cinematic universe, sets a limit on the string. Here are some of the quantifiers we see in this regular expression:

After the username and domain of the email, there is a `+`. This little guy explains that anything matching the username/domain specifications one or more times must be searched for.

After the top level domain, there is `{2,6}`. This means the amount of characters in this section must be 2 to 6 characters. Pretty cool, eh?

There is also an asterisk `*` after the subexpression to inform us that we are searching for anything that matches the pattern zero or more times.

### OR Operator

A common gadget at the disposal of these super hero expressions (am I forcing the metaphor now?) is the OR `|` operator. We don't see it used here, but it will be used in a regex to say "this or this is accepted". For example, if we wanted to incorporate an OR operator, we can list out every single alphanumerical character in the username bracket and put the `|` between them. This would be saying that "A can be included, and so can B, and so can C..." but this is impractical and we don't need to use it. So we'll just tuck this one in the trunk of the batmobile (I know, that's DC, whatever).

### Character Classes

Character classes are also not used in here, but they're good to know. So basically, they define a set of characters that will be searched for. Remember when I said that the backslash `\` had to be put before the period `.` to negate it and make it a literal character? Well, if that backslash wasn't there, the `.` would be saying "Find any and all characters, I don't care which." Then our regex would implode like the Death Star. The `.` is a character class.

Here are some other character classes:

* `\d` matches any Arabic numeral digit

* `\w` - Matches any alphanumeric character from the basic Latin alphabet

* `\s` - Matches a single whitespace character, including tabs and line breaks

### Flags

So this is kinda awkward...there's not flags in this regex either. But I'll teach you anyway, young padawan. A flag is placed after the second slash to define extra functionality. We could append the `g` flag which searches globally and tests all matched strings against the regex. But this is already happening, so we can forget about it.

Here are some other flags:

* `i` - For case sensitive searches (Which we can also put in but this, too, is accounted for)

* `m` - For multiline searches

### Grouping and Capturing

Grouping/capturing is another common regex technique, and the only instance of it in here is the parenthesis `()` which denote a subexpression. Subexpressions look for an exact match unless told to do otherwise. Just another one of the superpowers regular expressions have.

### Bracket Expressions

Anything inside the brackets `[]` represent a range of characters that we want to match. Since there are multiple sets of brackets, let's explain what each one does:

* The first set of brackets is for the username of the email address. `a-zA-Z0-9` tells us that any alphanumeric characters can exist in this part of the string. The special characters `._%-` are also acceptable.

* The second set of brackets is for the domain of the email address. Again, all alphanumeric characters are acceptable, but only `.` and `-` can be the special characters.

* The third set of brackets is for the top level domain of the domain name (the .com, .net, .org, etc). This can only be alphabetical characters due to the `a-zA-Z`.

### Greedy and Lazy Match

The concept of greedy and lazy matching in regular expressions is kinda like the force. There is a dark side and a light side (I hope you are taking notes). Except when you are working with matching, you don't need to lift an X-wing out of a swamp with a little green alien strapped to your back (in my experience this is not a requirement).

All quantifiers are naturally greedy, meaning they'll find as many instances of something as possible. However, to negate this, or make it lazy, we add a question mark `?` after the quantifier. Then, you will get as little results as possible.

### Boundaries

Just like your love-life, you need to have boundaries. Yeah, no superhero or Star Wars reference, we're getting serious now. A boundary kinda does what it sounds like, sets the limits of the search results.

The `^` at the beginning anchors the search to the start of a string, and `$` does the same for the end of the string.

### Back-references

We don't have back-references here, but if I must tell you, they refer to a previously matched subexpression. [Insert corny Star Wars or Marvel reference here]. 

Say I wanted to find two emails back to back. I would add a \1 to the end:

```
/^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6})*\1$/
```

This \1 references the first (and only) subexpression. Now we will be searching for two emails that are back to back.

### Look-ahead and Look-behind

Another regex component not incorporated in here are lookarounds. These are used to check what surrounds a certain phrase. For example, if we wanted them in this example, we can follow the subexpression with `(?=John)` to see if the name John comes after the email.

Here are some other look arounds:

* `(?<=John)` to check if John comes before the email

* Replace the equal sign with an exclamation point to make it a negative lookaround `(?!John)` `(?<!John)`

### Conclusion

And there you have it. We just learned a little more about regular expressions by dissecting one. Now it may not be Spider-Man fighting the Green Goblin or a lightsaber fight on a Star Destroyer, but these little guys give us much more capabilities in our dev journeys. Is that worthy of the big screen? I think so. Your move Hollywood!

## Author

Hello, my name is Walden Light, and I am a web developer from Boulder, Colorado. I love to code and be outdoors.

Check out my [GitHub](github.com/waldenlight)
