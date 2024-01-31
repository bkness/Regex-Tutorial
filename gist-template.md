# Regex Tutorial for Emails

"Hello World! Today, we're diving into the world of regular expressions. These little gems are powerful tools for pattern matching and text manipulation, used by programmers, data analysts, and anyone eager to enhance their text-searching skills. With regex, we can describe intricate patterns in strings, making it a breeze to match, find, or replace specific sequences of characters. Throughout this tutorial, we'll disect those confusing symbols and characters, breaking them down into easily digestible concepts. By the end, you'll have all the knowledge you need to seamlessly incorporate regex into your projects."

## Summary

This tutorial will explore a regular expression designed to validate email addresses. This regex ensures that an email follows a basic structure, checking for valid characters in the username, the domain, and the top-level domain. This pattern allows for flexibility and maintains the essential constraints. We'll break down the regex and explain each component, giving you the tools needed to modify your own regex expression based on your specific requirements. 

Email Regex Code: ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$



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

## Anchors

Anchors are special characters that assert a position in a string. Instead of matching characters, they define specific points in the text. Anchors are useful for recognizing patterns in certain positions within the string.

### 1. Caret(^) - Start of Line Anchor:

<p><li>The caret asserts that the following pattern must occur at the beginning of a line.</li></p>

    Example: `^john.doe@example\.com` matches an email address starting with "john.doe@example.com."

### 2. Dollar Sign ($) - End of Line Anchor:

<p><li>The dollar sign asserts that the preceding pattern must occur at the end of a line.</li></p>

    Example: `gmail\.com$` matches an email address ending with "@gmail.com."

### 3. Word Boundary (\b) - Word Boundary Anchor:

<p><li>The word boundary asserts that the pattern must occur at the beginning or end of a word.</li></p>

    Example: `\buser123\b` matches the exact word "user123" within an email.

### 4. Non-Word Boundary (\B) - Non-Word Boundary Anchor:

<p><li>The non-word boundary asserts that the pattern must not occur at a word boundary.</li></p>

    Example: `\B@example\.com\B` matches "@example.com" within a larger string but not in the middle of words.

### Here are some additional points about anchors:

<p><li>Multiline Mode:</li></p>
 
 <li style="margin-left: 20px;">In multiline mode, ^ and $ also match the start and end of each line within the string.</li>

## Quantifiers

Quantifiers specify the number of occurrences a character or group should have in a pattern.

### 1. Asterisk (*) - Zero or More Quantifier:

<p><li>The asterisk (*) quantifier matches zero or more occurrences of the preceding character or group.</li></p>

    Example: `user.*@example\.com` matches "user@example.com," "user123@example.com," and "user.admin@example.com."

### 2. Plus (+) - One or More Quantifier:

<p><li>The plus (+) quantifier matches one or more occurrences of the preceding character or group.</li></p>

    Example: `^[a-zA-Z0-9_]+@gmail\.com$` matches valid Gmail usernames followed by "@gmail.com."

### 3. Question Mark (?) - Zero or One Quantifier:

<p><li>The question mark (?) quantifier matches zero or one occurrence of the preceding character or group.</li></p>

    Example: `admin(-\d{2})?@example\.com` matches both "admin@example.com" and "admin-01@example.com."

### 4. Curly Braces ({n, m}) - Custom Range Quantifier:

<p><li>The curly braces ({n, m}) quantifier matches at least n and at most m occurrences of the preceding character or group.</li></p>

    Examples:
    - `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$` matches a standard email address.
    - `.{8,12}` matches strings with a length between 8 and 12 characters.

### 5. Lazy Quantifiers:

<p><li>Quantifiers are greedy by default, matching as much as possible. Adding a ? after a quantifier makes it lazy, matching as little as possible.


## Characters and Character Classes

Characters and character classes allow you to define specific sets of characters within a regular expression.

### 1. Single Character:

<p><li>A single character in a regular expression matches itself.</li></p>

    Example: `a` matches the character "a" in a string.

### 2. Character Class (Square Brackets []):

<p><li>Character classes define a set of characters. Use square brackets (`[]`) to match any one of the characters within the brackets.</li></p>

    Example: `[aeiou]` matches any vowel.

### 3. Range in Character Class:

<p><li>In a character class, you can specify a range of characters using a hyphen (-).</li></p>

    Example: `[0-9]` matches any digit.

### 4. Negation in Character Class:

<p><li>To negate a character class, use a caret (^) at the beginning.</li></p>

    Example: `[^aeiou]` matches any consonant.

### 5. Escape Special Characters:

<p><li>Use a backslash (\) to escape special characters within a character class.</li></p>

    Example: `[\$%^]` matches any of the characters "$," "%," or "^."

### Here are some additional points about characters and character classes:

<p><li>Shorthand Character Classes:</li></p>

<li style="margin-left: 20px;">Shorthand notations like `\d` (digits), `\w` (word characters), and `\s` (whitespace) represent common character classes.</li>

## Flags in Regular Expressions

Flags modify the behavior of regular expressions, providing additional options for matching patterns.

### 1. Global Flag (g):

<p><li>The global flag (`g`) performs a global search, matching all occurrences of the pattern in a string.</li></p>

    Example: `/pattern/g` matches all occurrences of "pattern" in a string.

### 2. Case-Insensitive Flag (i):

<p><li>The case-insensitive flag (`i`) makes the pattern matching case-insensitive.</li></p>

    Example: `/word/i` matches "Word," "WORD," or "word."

### 3. Multiline Flag (m):

<p><li>The multiline flag (`m`) enables matching the start (^) and end ($) of each line within a multiline string.</li></p>

    Example: `/^start/m` matches "start" at the beginning of any line in a multiline string.

### 4. Sticky Flag (y):

<p><li>The sticky flag (`y`) matches only at the start of the string and indicates that the next match should start at the end of the previous match.</li></p>

    Example: `/pattern/y` matches "pattern" only at the start of the string.

### 5. Unicode Flag (u):

<p><li>The Unicode flag (`u`) enables full Unicode matching, including support for Unicode escape sequences.</li></p>

    Example: `/[\u{1F600}-\u{1F64F}]/u` matches emojis.

### Here are some additional points about flags:

<p><li>Combining Flags:</li></p>

<li style="margin-left: 20px;">You can combine multiple flags in a regular expression, such as `/pattern/gi` for a global, case-insensitive search.</li>

### Grouping and Capturing in Regular Expressions

Grouping and capturing allow you to treat multiple characters as a single unit and extract matched portions of a string.

## 1. Grouping with Parentheses:

<p><li>Use parentheses `()` to create a group, treating the enclosed characters as a single unit.</li></p>

    Example: `(abc)+` matches "abc," "abcabc," and so on.

### 2. Capturing Groups:

<p><li>Capturing groups `( ... )` not only group characters but also capture the matched portion for later use.</li></p>

    Example: `(\d{2})-(\d{2})-(\d{4})` captures day, month, and year in a date pattern.

### 3. Non-Capturing Groups:

<p><li>Non-capturing groups `(?: ... )` group characters without capturing them.</li></p>

    Example: `(?:abc)+` matches "abc," "abcabc," but only captures the entire group.

### 4. Backreferences:

<p><li>Use backreferences (`\1`, `\2`, etc.) to refer to the captured content within the same regular expression.</li></p>

    Example: `(\w+)\s\1` matches repeated words.

### 5. Named Capturing Groups:

<p><li>Provide names to capturing groups for easier reference.</li></p>

    Example: `(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})` captures day, month, and year with named groups.

### Here are some additional points about grouping and capturing:

<p><li>Greedy vs. Lazy Capturing:</li></p>

<li style="margin-left: 20px;">Capturing groups are greedy by default, matching as much as possible. Adding a `?` after a group makes it lazy, matching as little as possible.</li>


### Bracket Expressions

Bracket expressions, also known as character classes, allow you to define specific sets of characters within a regular expression.

### 1. Single Character:

<p><li>A single character in a regular expression matches itself.</li></p>

    Example: `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$` matches a standard email address.

### 2. Character Class (Square Brackets []):

<p><li>Character classes define a set of characters. Use square brackets (`[]`) to match any one of the characters within the brackets.</li></p>

    Example: `[aeiou]` matches any vowel in a string.

### 3. Range in Character Class:

<p><li>In a character class, you can specify a range of characters using a hyphen (-).</li></p>

    Example: `[0-9]` matches any digit in a string.

### 4. Negation in Character Class:

<p><li>To negate a character class, use a caret (^) at the beginning.</li></p>

    Example: `[^aeiou]` matches any consonant in a string.

### 5. Escape Special Characters:

<p><li>Use a backslash (\) to escape special characters within a character class.</li></p>

    Example: `[\$%^]` matches any of the characters "$," "%," or "^" in a string.

### Here are some additional points about characters and character classes:

<p><li>Shorthand Character Classes:</li></p>

<li style="margin-left: 20px;">Shorthand notations like `\d` (digits), `\w` (word characters), and `\s` (whitespace) represent common character classes.</li>

### Greedy and Lazy Match

Greedy and lazy quantifiers affect how much a pattern matches within a string.

### 1. Greedy Match:

<p><li>Greedy quantifiers (default behavior) match as much as possible.</li></p>

    Example: `.+@example\.com` matches the longest string ending with "@example.com" within a larger text.

### 2. Lazy Match:

<p><li>Adding a ? after a quantifier makes it lazy, matching as little as possible.</li></p>

    Example: `.+?@example\.com` matches the shortest string ending with "@example.com" within a larger text.

### Boundaries

Boundaries in regular expressions help define specific positions in a string.

### 1. Word Boundary (\b) - Word Boundary Anchor:

<p><li>The word boundary asserts that the pattern must occur at the beginning or end of a word.</li></p>

    Example: `\badmin\b` matches "admin" as a whole word but not within other words.

### 2. Non-Word Boundary (\B) - Non-Word Boundary Anchor:

<p><li>The non-word boundary asserts that the pattern must not occur at a word boundary.</li></p>

    Example: `\Buser\B` matches "user" within a word but not as a standalone word.

### Back-references

Back-references refer to previously captured groups in a regular expression.

### 1. Backreferences:

<p><li>Use backreferences (`\1`, `\2`, etc.) to refer to the captured content within the same regular expression.</li></p>

    Example: `(\w+)\s\1` matches repeated words in a string.

### Look-ahead and Look-behind

Look-ahead and look-behind assertions allow you to match a group only if it is (or is not) followed or preceded by another group.

### 1. Positive Look-ahead:

<p><li>Positive look-ahead asserts that a certain pattern must be present after the main pattern.</li></p>

    Example: `user(?=@)` matches "user" only if it is followed by "@" but does not include "@" in the match.

### 2. Negative Look-ahead:

<p><li>Negative look-ahead asserts that a certain pattern must not be present after the main pattern.</li></p>

    Example: `admin(?!@)` matches "admin" only if it is not followed by "@".

### 3. Positive Look-behind:

<p><li>Positive look-behind asserts that a certain pattern must be present before the main pattern.</li></p>

    Example: `(?<=@)user` matches "user" only if it is preceded by "@" but does not include "@" in the match.

### 4. Negative Look-behind:

<p><li>Negative look-behind asserts that a certain pattern must not be present before the main pattern.</li></p>

    Example: `(?<!@)admin` matches "admin" only if it is not preceded by "@".


## Author

In conclusion, regex is a powerful tool that can help you master analyzing and manipulating text. I have defined the core concepts along with some useful examples for practical use. As you embark on your regex journey make sure to re-visit documentaion! More regex concepts can be seen [here](https://www.w3schools.com/jsref/jsref_obj_regexp.asp).

 My name is bkness, and you can reach me [here](https://www.github.com/bkness). 
 
 Happy coding!