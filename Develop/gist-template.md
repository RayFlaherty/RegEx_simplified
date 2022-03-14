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

    A quick table of contents for letters for reference later in the material. Don't worry if you don't understand them completely now, it will make since later. But here is a list of Meta Characters and what they do.

        Character List:
            \d  -  references all digits, 0-9
            \w  -  references all word characters, A-Z, a-z, and 0-9,
            \s  -  references all whitespace (areas with no value or character set)
            .   -  references any character what-so-ever
            \W  -  references anything NOT a word character.
            \S  -  references anything NOT whitespace. 

### Anchors 
    The first component I would like to cover has very little to do with text at all. An ANCHOR refers to the position of a character, in this case either the beginning or end of a line. The meta characters that govern these requests are the caret(^), indicating the beginning of a line, and the dollar sign ($), indicating the end of a line.  

    Examples of using anchors.

    Search:  ^abc, this result will return every line that begins with the literals, abc at the beginning. 
             abc$, will match every line who’s last three characters are abc. 

    You’re probably thinking to yourself, this isn't too convenient? Why would I need to search for a line beginning or ending with a literal word? This seems pretty narrow. We haven't discussed it yet. However, you can combine different aspects of Meta characters to find patterns. You'll see prime examples in the following components. But here are some more examples.

    Search: ^\d\d\d, will return any line whose first three characters are digits 0-9. The \d referring to a digit.
            \w\w\w$, will return any line who’s last three characters, letter or digit who ends a line. 
 

### Quantifiers
    Quantifiers specify how many instances of a character, group, or character class mush be present in the input for a match to be found. Quantifiers are further broken down into "Lazy and Greedy" quantifiers. We will look more into those later. But for now, lets go over the basic strokes. 

    As stated, the quantifier basically points out how MANY of the Meta Characters in a string you want to search. But what do they look like?
    Examples of quantifiers:
        * - looks for zero or more characters in a string;
            Example: \w* returns all words that contain more than zero characters in it. 

        + - looks for one or more characters in a string;
            Example: \d looks for all digits that contain one or more numbers.

        ? - returns 0 or 1, being the character is "optional".
            Example: a? looks for any word where the "a" is optional.

        {x,y} - allows you to search by giving a min and max number of characters to search for.
            Example: {3, 5} searches for all strings who's lengths are between 3 and five.

        {n} - looks for an exact number, were n is represented by a number. 
            Example: \w{5} searches for all five letter words.


### OR Operator

    The OR Operator is exactly how it sounds. It gives the search and option. This is notated by the use of a open and close parenthesis, (). Anything inside the parenthesis is searched. 
        For example: th(aiu)nk  will return think, thank, and thunk. 

    You are searching with options in regards to the literal characters inside the parenthesis. The following few sections will get into some more depth. 

### Character Classes

    Character Classes extend and use the same syntax as Bracket Expressions. However, they are e set number of commands listed in brackets and colons. Refer to the following list. 

    [:alnum:]  - alphanumberic characters [a-zA-Z0-9]
    [:alpha:] -  alphabetic characters [a-zA-Z]
    [:ascii:] -  ASCII characters
    [:blank:] -  Space and tabs
    [:cntrl:] - control characters

    Just to name a few. For a complete list, please checkout 
    
#### [List of Character Classes](https://www.regular-expressions.info/posixbrackets.html) . 


### Flags

    There are six types of Flags in REGEX, they are as follows:

        i: searches are case-INsenstive. No difference between A or a.

        g: looks for all matches.

        m: searches for multiline modes of anchors. 

        s: enables "dotall" mode. That allows a dot (.) to match newline character \n.

        u: enables full Unicode Support. It allows correct processing of surrogate paris.

        y: "Sitcky" mode. Searching at the exact position in the text.

### Grouping and Capturing

    Something you may not have noticed when we discussed Character Classes in a previous chapter, when you first enter in a search no matter how broad, it is automatically grouped and labeled as Group 0. Furthermore, any interior groupings will be labeled as Group 1, Group 2, ect. The further you go. Let's explore this with the phone number example. 
        Example : \d{3}-\d{3}-\d{4} , this entire expression is considered Group 0

                Take Group 0 and break it down into more groups.

                \d{3}-(\d{3})-(\d{4}) , groups and labels the expressions  (\d{3}) and (\d{4}) as Group 1 and Group 2 respectively. 

    Why is this important? It is very powerful because it gives you the ability to reference the groups by using the expression $1 or \1. The $ signifying a replace command and the \ is when you simply want to refer to the indicated group. Now how could you use this?
        Example : lets continue to use the phone number example. Say you want to keep the area code, however redact or change the other groups inside the string. Use parenthesis to capture the groups. 

        (\d{3})-(\d{3})-(\d{4}) : captures the first group of digits. 

        Using the expression

        $1-XXX-XXXX : this command will capture the first set of digits from the original group, the any string of three digits, and the $ will replace every instance of those groupings of numbers with X's following the captured group one expression. 

    Deeper Dive- playing with this method can be very exciting and powerful. Say you have a group of data that contains thousands of lines of names in the format of last_name, first_name. And you want to switch the format to first_name, last_name. You could spend weeks of time going line by line and copy and pasting. But lets use REGEX to give us an edge. 

            From what we discussed, searching for Flaherty, Raymond would look a lot like \w+,\s+\w+  . Being, any length of word (\w+) followed by a comma (,), followed by any length of whitespace (\w+), followed by any length of word. (\w+). Now lets capture some groups to move. Use parenthesis to capture the word groups.   (\w+),\s+(\w+), captured! And replace with $2 $1. Run this function and watch the magic happen. You just saved an extremely time consuming and monotonous process by using REGEX!
                 

### Bracket Expressions

      Bracket Expressions work similarly to the OR Operator, however there is some more depth to it. These items appear between square brackets ( [] ) and you are looking for any character within. 
        Example: [ abc ] will return any search containing an a OR b OR c.
            R[au]n with return any result that matches Ran OR Run. 

    Also can be very useful when searching for phone numbers who's number groups are separated by a dash, dot, or space.
        Example: \d{3}[-. ]\d{3}[-. ]\d{4} returns any string of numbers that matches these patterns; ddd-ddd-dddd OR ddd.ddd.dddd OR ddd ddd dddd.

    Deeper dive- How can you search for a phone number in this format? (615)555-2345 ?
        Easy Peasy-  Here, you would start the expression with the optional quantifier in the previous example. \(?\d{3}[-. )]\d{3}[-. ]\d{4}

    It also should be noted, any character inside the square brackets which is now noted  as a character class, becomes the literal version of the character. 
        Example, reference the above characters and expressions in the previous sections of this tutorial. If you enter a ? in a square bracket, it looks for the literal ? and not make the previous character optional as the normal usage of that Meta Character would. However, if you use a dash between letters and digits (i.e. [a-z]) it will return any literal character between the alphabetic letters of a to z. If the dash comes first, it will look for a literal dash. 

### Greedy and Lazy Match

### Boundaries

WORD BOUNDARIES \b, REFER TO ANCHORS IN VIDEO 2 

### Back-references

    In the grouping and capturing module, we discussed using the $ to capture and replace a group. Now, how would you simply reference the group without change. Use the backslash (\). This function will be essential in findIng any double words used in a sentence. For example, this this, that that, help help. Sometimes, typos get by and doubles come through. How could you do this?
        Example : use the expression, \b(\w+)\s+\1\b. Now, what did we write, we searched for and  any word of any length and grouped it as group 1 ( (\w+)), followed by any amount of white space, followed by the group one expression. And BOOM! You can now see if there is any repeating words in your work. However, notice we had to wrap the expression in a word boundary with a set of \b. This just means your're looking for actual words and not simply patterns. Patterns can sometime be vague. 

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
