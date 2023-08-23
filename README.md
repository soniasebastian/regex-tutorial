# Regex-Tutorial
A tutorial explaining how a specific regular expression (regex) functions by breaking down each part of the expression and describing its functionality.

## Matching an Email Address
This tutorial explains how a specific regualr expression , or regex, functions by breaking down each part of the expression.A regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate inpu

## Summary
In this tutorial, we will explore the intricacies of regular expressions (regex) by dissecting the regex /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/. This regex is tailored to match and validate email addresses. We'll break down each component of the expression and provide detailed explanations along with examples to demonstrate its functionality.

## Regex
/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

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

## Regex
^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$

## Anchors
The anchors used in this regex expression for matching an email are ^ , which indicates the beginning of the string and $ to indicate the ending of the string. (m) , or multiline is not enabled, so the regex will end at $. Anchors in regular expressions are special characters or constructs that define specific positions within the input text where a match must occur. They do not represent actual characters, but rather positions relative to characters in the input string. Anchors are used to ensure that a certain part of the pattern is located at a specific position in the text. There are two main types of anchors:

## Quantifiers
Quantifiers define how many times a specific character or group should occur. For instance, + indicates that the preceding element should occur one or more times.A Quantifier specifies how many instances of the previous element (which can be a character, a group, or a character class) must be present in the input string for a match to occur. They also determine whether a regex will attempt a Greedy match or a Lazy match.They control the repetition of the preceding pattern.

## The OR Operator
The | symbol functions as an OR operator, allowing you to match either of the expressions separated by it. In the regex, it is used to match either a 6-character or 3-character domain.

## Character Classes
Character classes like \d and \w represent shorthand for certain character sets. \d matches digits (0-9), while \w matches word characters (letters, digits, or underscores).

Character classes are specific notation to denote matches of symbols in a certain group. [a-z] a-z A single character between a and z that is case sensitive. [0-9] 0-9 A single character between 0-9.

## Grouping Constructs
Parentheses ( and ) are used to create groups. In the regex, groups are used to capture and remember certain patterns for later use.Grouping constructs are sub-expressions of a regular expression. ([a-z0-9_.-]+)

First capturing group - a-z A single character between a and z that is case sensitive. 0-9 A single character between 0-9. _ Indicates that it must match the character and is case sensitive. . Must match the character and is case sensitive. - The character must match and is case sensitive. + It is a greedy match, so the character is repeated as many times possible. It is also case sensitive.

([\da-z.-]+) Second capturing group - \d Indicates the character matches a digit the same as [0-9]. a-z A single character between a and z that is case sensitive. . Must match the character and is case sensitive. - The character must match and is case sensitive. + It is a greedy match, so the character is repeated as many times possible. It is also case sensitive.

([a-z.]{2,6}) Third capturing group - a-z A single character between a and z that is case sensitive. . Must match the character and is case sensitive. {2,6} The bound that is a greedy match, matching 2 (min) and 6 times (max).

## Bracket Expressions
Bracket expressions, denoted by [ ], define a character set from which a single character should match. For example, [a-z0-9_.-] matches lowercase letters, digits, underscores, dots, and hyphens.

Bracket expression show what set of of characters need to be matched. [a-z0-9_.-] a-z A single character between a and z that is case sensitive. 0-9 A single character between 0-9. _ Indicates that it must match the character and is case sensitive. . Must match the character and is case sensitive. - The character must match and is case sensitive.

[\da-z.-] \d Indicates the character matches a digit the same as [0-9]. a-z A single character between a and z that is case sensitive. . Must match the character and is case sensitive. - The character must match and is case sensitive.

[a-z.] a-z A single character between a and z that is case sensitive. . Must match the character and is case sensitive.

## Greedy-and-lazy-match
the terms "greedy" and "lazy" are more commonly associated with quantifiers like * (greedy) and *? (lazy), which control the repetition of preceding elements

## Boundaries
Instead of anchoring the regex match to the start and end of the subject, you have to specify that the start of the local part and the top-level domain cannot be part of longer words. This is easily done with a pair of word boundaries. Replace both ‹ ^ › and ‹ $ › with ‹ \b ›. For instance, ‹ ^[A-Z0-9+_.

## Back-references
We can use backreferences in a regular expression to ensure that the same value appears multiple times in a pattern. In the context of an email address, you might want to ensure that the domain name's last part (the top-level domain) matches the first part (the domain name) by using a backreference. \b[A-Za-z0-9._%+-]+@([A-Za-z0-9.-]+).\1\b

In this regex: \b[A-Za-z0-9._%+-]+@: Matches the username and "@" symbol. ([A-Za-z0-9.-]+): This is a capturing group that matches the domain name. The capturing group ( ) allows you to refer back to this matched value using a backreference \1. .\1: Matches a period (.) followed by the same value that was captured in the first capturing group. This ensures that the TLD matches the domain name. \b: Word boundaries to ensure the email address is matched as a whole word.

## look-ahead-and-look-behind
We can use lookaheads and lookbehinds in a regular expression to add more sophisticated matching conditions without actually consuming characters. Here's how you could modify the regex to include a positive lookahead to ensure that the TLD is the same as the domain name: \b[A-Za-z0-9._%+-]+@([A-Za-z0-9.-]+).(?=\1)[A-Za-z]{2,}\b

In this regex:

\b[A-Za-z0-9._%+-]+@: Matches the username and "@" symbol. ([A-Za-z0-9.-]+): This is a capturing group that matches the domain name. .: Matches a period (.) that separates the domain name from the TLD. (?=\1): This is a positive lookahead assertion. It checks that the following part matches the same value as captured in the first capturing group, ensuring that the TLD matches the domain name. [A-Za-z]{2,}: Matches the TLD (at least two letters). \b: Word boundaries to ensure the email address is matched as a whole word. Please note that using lookaheads and lookbehinds can make your regular expressions more powerful, but they can also add complexity and reduce readability.

## Character Escapes
Backslashes \ are used as escape characters to match literal characters that would otherwise have special meanings in regex. For example, . matches a literal dot.

## Author
This tutorial was crafted by Sonia Sebastian M, a curious web development student. You can connect with me on GitHub(https://github.com/settings/profile).
