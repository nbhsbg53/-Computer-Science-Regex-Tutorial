# Tutorial: Regex - Matching a Hex Value 
Welcome to a breif tutorial about regex, specifically for matching hex values with regex! 
The purpose of this tutorial is to provide an fundemental understanding of how regaurlar expressions work. 
Regular expressions, more commanly known as "regex" are a series of specical characers that define a search pattern. 
Regex is beneficial as it allows a user to easily match, locate, and manage text. 
A regular expressoin (regex) is considered a literal, so the pattern must always be warpped in slash characters (/). 


## Summary
This tuorial will specifically be looking at how a regex can match a hex value. 
The first thing that needs to be explained is, what is a hex value? 

A hex value is a Hexadecimal code. A hexadecimal code is a sysyem by which any specific colour can be described accurately and consistently to a computer. This is important as it ensures the color disaply is rendered the same each time the same code is used. 
A hexadecimal color value is a six{6}-digit or three{3}-digit code preceded by a # sign; it defines a color that is used witin a website or a computer program; for example #000000 represents the colour black, wheras #ff0 is the colour yellow. 

For the purpose of this tutorial we will be using the following regex hex value: 
`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

It is important to note that all regex must be wrapped in slash characters `/`. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [The OR Operator](#the-or-operator)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Conclusion](#conclusion) 

## Regex Components

### Anchors
/`^`#?([a-f0-9]{6}|[a-f0-9]{3})`$`/

Anchors are used at both ends of a regex. Despite appearing random and out of place the use and position of `^` and `$` characters are deliberate.
-The `^` after the initial `/` indicates the beginning of the string.  
-The `$` before the closing `/` indicates the end of the string. 

For our example the hex value begins after the `^` and ends after the `$`


### Quantifiers
/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/

Quantifiers are used to specify the numbers of characters that are expected to be found.

Quantifiers take up the following forms in regex and each has a unique meaning. 
- `+` indicates that the element may be repreated one (1) or more times. 
- `*` indicates that the element may be repeated 0 or more times. 
- `?` indicates that the element may be present in the regex 0 or one (1) time. 
- `{}` can provide 3 different ways to set limits for a match:
  1) `{n}`  indicates the exact nuumber of times it must be present in the regex.
  2) `{n,}` indicates the number must be present at least 'n' number of times in the regex.
  3) `{n, x}` indicates the number must be present a minimum number 'n' of times to a maximum number 'x' of times in the regex.  

Quantifiers are located to the right of the expression / characters in question. In our example we have 3 quantifiers. <br> 
/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/ 

Quantifier 1: 
Is found to the right of the `#`, due to the use of the `?`. 
This means the # may be used or may not be used (it is optional), i.e. a hex value of AA1122 is the same as #AA1122 and both would be matches. 

Quantifier 2:
Is found inside the first `{}`, due to the use of the `{6}`. This is indicating the hex value must be exactly 6 characters long. For example #BB33AA would be a valid match. Interestingly, a six-digit (6) hexadecimal number is called a "Hex Triplet". For example, #ffcc00 is the colour dark-yellow. 

Quantifier 3:
Is similar to quantifier 2, but is found inside the second `{}`. due to the use of the `{3}`. This is indicating the hex value must be exactly 3 characters long. Interestinly, a three(3)-digit hexadecimal number is  called "shorthand hex notation" as it abbrevites six-digit hex codes. Using the same example from quantifier 2; #fc0 represents the colour dark-yellow. 

### Grouping Constructs
/^#?`([a-f0-9]{6}|[a-f0-9]{3})`$/
The primary way that characters in a regex are captured is by using parentheses `( )` to group them. You can have a single set of parentheses (as we do in our example) or you can have multiple sets of parentheses. For example (abc):(lmn). When multiple parentheses are used in a regex they are called 'subexpressions'. 

For our example all the characters are within a single set of parentheses and are therefore looking for a single hex value, either six(6) or thee(3) characters long. 

### The OR Operator
/^#?([a-f0-9]{6}`|`[a-f0-9]{3})$/
The OR operator is a realatively straight forward concept, and literaly means OR within the regex. It is illustrated by using the character `|` which highlights to the user that the regrex can be X or Y. 

We have one `|` operator being used, indicating that our pattern of can either be 6 or 3 characters in length as long as they consist of alphanumber values between a-f and 0-9. 

For example as a hex value of #aa1122 or #a12


### Bracket Expressions
/^#?(`[a-f0-9]`{6}|`[a-f0-9]`{3})$/
Bracket expressions are classified by the characters inside the square brackets `[ ]`.
For our example we have [a-f0-9], indicating that the hex value will match with alphanumeric values between a-f and 0-9. 

For example: Hex vales of #def356, #112233, #1c1c1c, #222, #ccc, #1d2 would all be valid matches. 


Interestingly, bracket expressions are also know as a 'positive character group' as they define the characters we wish to have included. Conversely, a bracket expression can be turned into a 'negative character group' buy adding a ^ symbol to the beginning of the expression inside the brackets. An example would be matching a string that does not include any vowels. The pattern [^aeiouAEIOU] would find any string that do not include lowercase or uppercase vowels. 

### Character Classes
/^#?([`a-f0-9`]{6}|[`a-f0-9`]{3})$/
Characters classes are elements within our regex that indiciate what types of characters to expect. 
For our example our characters are contained within 2 sets of `[ ], therefore 2 character classes are present. However, for our example both characters classes are identical. 
It is expected that valid characters will be alphabetical letters between `a-f` as well as numeric values between `0-9`. 

### Conclusion
We have reached the end of the tutorial now lets examine the example as a regex!

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

- The regex is between the beginning and closing `/`
- Anchors `^` and `$` signify the start and end of the string respectively. 
- The `?`means the character that precedes it can be present 0 or 1 time, which can be interuprted as being optional. 
- We have a single grouping construct as all the characters are inside 1 set of parentheses `( )`.
- We have 2 indentical bracket experssions as indicated by /^#?(`[a-f0-9]`{6}|`[a-f0-9]`{3})$/ 
- The expected characters are letters betwen a-f and numbers between 0-9. 
- The hex value must be `{6}`  "OR"`|` `{3}` characters in length, as indicated by /^#?([a-f0-9]`{6}` `|`[a-f0-9]`{3}`)`$/

Finally, based on the example we can deduce that your hex value is a single group of characters between 3 or 6 characters long, made up of a combination of letters from a-f and numbers 0-9 and may begin with a # (however this is optional). If all these elements are established then you have a valid hexadecimal color value. 

Valid examples could be #a2b4c6, #000000, b6e7f8, c22 or many other possibilites. 


## Author
Thanks for taking the time and reading the tutorial! I hope you now have a firm grasp of regex and hex (hexadecimal) values. <br>
My name isBrandon Grady and I'm an aspiring full-stack developer. 
Check out my GitHub to see a bunch of other work ive finished or currently working on. 
GitHub: [nbhsbg53](https://github.com/nbhsbg53)