# Regular Expressions

## Summary

    A regular expression is a sequence of characters that defines a search pattern for text. When you go to google, or a search bar, how do you look for information? You type exactly what you are looking for and strike the execute key. Then you browse through the resulting data looking for what you need. If you don't find what you are looking for, what do you do? You adjust the phrasing or characters and try again. This type of search refers to the use of Literal Characters. Meaning, what is returned to you is LITERALLY what you put in. What if there is another way? A way to search for patterns. Well, if you can guess where I am going with this, there is. Meta Characters
    
    Meta Characters refer to the use of patterns instead of actual letters. Say you want to find a three letter word? A phone number that you don't exactly remember the actual digits?
    Or maybe you want to make sure all your spacing is the same in a document? All these functions and so much more are possible through the use of Meta Characters.  The following document will show you the use and possibilities of using REGEX for your next project as well as in your day to day coding. Enjoy!

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
    The first component I would like to cover has very little to do with text at all. An ANCHOR refers to the position of a character, in this case either the beginning or end of a line. The meta characters that govern these requests are the caret(^), indicating the beginning of a line, and the dollar sign ($), indicating the end of a line.  

    Examples of using anchors.

    Search:  ^abc, this result will return every line that begins with the literals, abc at the beginning. 
             abc$, will match every line who’s last three characters are abc. 

    You’re probably thinking to yourself, this isn't too convenient? Why would I need to search for a line beginning or ending with a literal word? This seems pretty narrow. We haven't discussed it yet. However, you can combine different aspects of Meta characters to find patterns. You'll see prime examples in the following components. But here are some more examples.

    Search: ^\d\d\d, will return any line whose first three characters are digits 0-9. The \d referring to a digit.
            \w\w\w$, will return any line who’s last three characters, letter or digit who ends a line. 
 

### Quantifiers
    Quantifiers specify how many instances of a character, group, or character class mush be present in the input for a match to be foun    d. 

### OR Operator

### Character Classes
Literal Character- very specific pattern
Meta Character- more general pattern

phone number example, literal will search for specific numbers, ie 615-123-4567. A Meta will search for the pattern, ie \d\d\d-\d\d\d-\d\d\d\d where \d represents any number (digit) 0-9.
### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

WORD BOUNDARIES \b, REFER TO ANCHORS IN VIDEO 2 

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
