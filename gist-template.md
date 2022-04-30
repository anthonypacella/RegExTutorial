# Regex Tutorial - Time

## Regular Expressions

Regular Expressions (Regex) are sequences of characters that will define a certain pattern to search through text strings to identify. These patterns are matched against a string of text to determine if the pattern combination is found in the string specified. There are many different ways to search a string amd many different patterns to identify. In this tutorial, you will learn about one specific regular expression. 

## Summary

Sometimes when writing a computer program, you may find yourself creating schedules, setting appointments, creating events, etc. on your application. If so, you may find it useful to have the users enter in time values for these appointments/events/etc. When time values are entered, it would be useful to made sure these values are uniform across your application. You can do so using regular expressions. 

A regular expression for time values in 24-hr time format is:

/^(0?[1-9]|1[0-9]|2[0-3]):[0-5][0-9]$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [The OR Operator](#the-or-operator)
- [Bracket Expressions](#bracket-expressions)

## Regex Components

### Anchors
Anchors are features of a regular expression that indicate whether an input string begins or ends with a certain charater (or both begins and ends). Below are examples of RegEx anchors:

Feature | Syntax | Description
---             | ---       | ---
String anchor   | ^ (caret)	| Matches at the start of the string the regex pattern is applied to.
String anchor   |$ (dollar)	| Matches at the end of the string the regex pattern is applied to.

In our regular expression,

<mark>/^</mark>(0?[1-9]|1[0-9]|2[0-3]):[0-5][0-9]<mark>$/</mark>

you can see that both of these anchors exist. The combination of the ^ anchor at the beginning and the $ anchor at the end of our regular expression means that the entered string needs to match exactly to our regular expression. This will allow every single time value entered into the application be completely uniform. 

### Quantifiers
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. Below are examples of RegEx quantifiers:

Quantifier | Description
---  | ---
\*	|   Match zero or more times.
\+	|   Match one or more times.
?   |   Match zero or one time.
{ n } | Match exactly n times.
{ n , } | Match at least n times.
{ n , m } | Match from n to m times.

In our regular expression,

/^(0<mark>?</mark>[1-9]|1[0-9]|2[0-3]):[0-5][0-9]$/

you can see one instance of the ? quantifier. This means that the string can have the "0" character at the beginning of the strong one or zero times. This is esentially allowing the user the option to start their time value with a zero or not (i.e. 09:00 or 9:00).

### The OR Operator
In regular expressions, the OR operator is notated by the '|' symbol. This operator allows for several matching criteria to be matched at once. In our regular expression, the OR operator is highlighted below:

/^(0?[1-9]<mark>|</mark>1[0-9]<mark>|</mark>2[0-3]):[0-5][0-9]$/

These OR operators in this example allow for the matching criteria to match one of the three character and bracket expressions (see below) before and after the operator - [1-9], 1[0-9], 2[0-3].

### Bracket Expressions
Bracket expressions are expressions that declare a certain set of characters that should match in a specific part of the string. All bracket expressions should begin with '[' and end with ']'.

In our regular expression,

/^(0?<mark>[1-9]</mark>|1<mark>[0-9]</mark>|2<mark>[0-3]</mark>):<mark>[0-5][0-9]</mark>$/

the highlighted sections above are bracket expressions. The first bracket expression <mark>[1-9]</mark> matches the second (or first if the zero is omitted - **see quantifier section**) character as being a number from 1 to 9.

The OR operator comes before our next bracket expression <mark>[0-9]</mark>. Since this bracket expression is preceeded by a 1, this bracket expression allows to possibility of the second character following the '1' character to be a number from 0 to 9. This handles the case when the hour is between 10:00 and 19:59 and the first character is a 1 and the second character should match a number from 1 to 9.

The last OR operator comes before our next bracket expreesion <mark>[0-3]</mark>, which is preceeeded by the '2' character. This handles the case when the hour is between 20:00 and 23:59 and the first character is a 2 and the second character should match a number from 0 to 3.

Our last two bracket expressions, <mark>[0-5][0-9]</mark>, are written to match the minute component of our time string. Since our minute component of our time string should only be a minute value from 00 to 59, the <mark>[0-5][0-9]</mark> bracket expression matches the first character to being a number from 0 to 5 and the second character from being a number from 0 to 9. 

The last piece of the regular expressions to note is the match for the ':' character, which is shown here:

/^(0?[1-9]|1[0-9]|2[0-3])<mark>:</mark>[0-5][0-9]$/


## Author

Anthony Pacella is an aspiring web developer living in Ohio. Check out his GitHub profile [here](https://github.com/anthonypacella).
