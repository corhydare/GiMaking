# GiMaking

Creating gists should be easy and simple.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

Anchors match position around characters.

```javascript
let line = "Lines";
console.log(/^L/.test(line));
```

this (^) will match beggining of the line because it starts with L, anything else will not match.

```javascript
let line = "Lines";
console.log(/$s/.test(line));
```

this ($) will match from the end only is the last character matches 's'.

### Quantifiers

```C#
string pattern = @"\b91*9*\b";
string input = "99 95 919 929 9119 9219 999 9919 91119";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);
```

- quantifier matches the preceding element zero or more times.
  in this code the match is found when "9" is followed by zero or more "1".

```text
  '99', '919', '9119', '999', etc,.
```

### Grouping Constructs

By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together.

This is often done to break sections of a string up, within parentheses.

```javascript
const imageDescription = "This image has a resolution of 1440×900 pixels.";
const regexpSize = /([0-9]+)×([0-9]+)/;
const match = imageDescription.match(regexpSize);
console.log(`Width: ${match[1]} / Height: ${match[2]}.`);
```

Expected output would be: "Width: 1440 / Height: 900."

/([0-9]+) checks for the numbers with "x" separator.

### Bracket Expressions

Anything inside a set of square brackets ([]) represents a range of characters that should be matched.
They outline the characters we want to include.

For example, [abc] will look for a string that includes a or b or c, regardless of the length of the string.
So all of the following examples would match: "aaa", "bin" "court", etc,.
To shorten the expression one can use a hyphen, "-", between the first and last characters in a sequence.

```javascript
"court".match(/[a-d]/);
```

court matches because in the range of a-d there is "c"

### Character Classes

When looking for matches, character classes are a set of characters, any one of which can occur in an input string.

```javascript
"stones".match(/[.]/);
/// matches any character except the newline character (\n)
```

```javascript
"potatoes".match(/[\d]/);
/// equivalent to [0-9]
```

```javascript
"boats".match(/[\w]/);
/// matches any alphanumeric character, even underscore [A-Za-z0-9_]
```

```javascript
"and hoes".match(/[\s]/);
/// will match a single whitespace character. in order to find duplicate spaces in a string use [\s]+[\s]
```

### The OR Operator

Using the OR operator (|), the expression [asdf] could be written as (a|s|d|f).

```javascript
^I like (dogs|penguins), but not (lions|tigers).$
```

will math dogs with lions or tigers, or the other way around with lions matching dogs or penguins.

For example:

```javascript
import static org.junit.Assert.assertFalse;
import static org.junit.Assert.assertTrue;

import org.junit.Test;

public class RegexTest
{
   @Test
   public void testRegex()
   {
      assertTrue(stringMatches("I like dogs, but not lions."));
      assertTrue(stringMatches("I like penguins, but not lions."));
      assertFalse(stringMatches("I like lions, but not penguins."));
   }

   private boolean stringMatches(String string)
   {
      return (string.matches("like dogs") || string.matches("like penguins"))
          && (string.matches("not lions") || string.matches("not tigers"));
   }

}
```

### Flags

Regular expressions have optional flags that allow for functionality like global searching and case-insensitive searching, which can be used separately or together.

Generating indices: RegExp.prototype.hasIndices => d
Global search: RegExp.prototype.global => g
Case-sensitive search: RegExp.prototype.ignoreCase => i
Multi-line search: RegExp.prototype.multiline => m
Allows . to match newline characters: RegExp.prototype.dotAll => s

```javascript
const re = new RegExp("pattern", "flags");
```

```javascript
const re = /\w+\s/g;
const str = "fee fi fo fum";
const myArray = str.match(re);
console.log(myArray);

// ["fee ", "fi ", "fo "]
```

### Character Escapes

If you need to use any of the special characters literally (actually searching for a "\*", for instance), you must escape it by putting a backslash in front of it.

```javascript
function escapeRegExp(string) {
  return string.replace(/[.*+?^${}()|[\]\\]/g, "\\$&");
  // $& means the whole matched string
}
```

or

To match 'a' followed by `*`, you must turn `*` into a literal search by using backslash:

```javascript
/a\*b/;
```

## Author

Danila Popov (https://github.com/corhydare)
