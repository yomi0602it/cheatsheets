# Regular Expressions Cheat Sheet

## Anchors

Anchors do not match any characters; rather, they match a position before, after, or between characters.

| Sequence | Description       |
| :------- | :---------------- |
| `^`      | Start of string   |
| `$`      | End of string     |
| `\b`     | Word boundary     |
| `\B`     | Not word boundary |
| `\<`     | Start of word     |
| `\>`     | End of word       |

## Quantifiers

Quantifiers dictate how many times the preceding element should be matched.

| Sequence | Description |
| :------- | :---------- |
| `*`      | 0 or more   |
| `+`      | 1 or more   |
| `?`      | 0 or 1      |
| `{3}`    | Exactly 3   |
| `{3,}`   | 3 or more   |
| `{3,5}`  | 3, 4 or 5   |

## Quantifier Modifiers

| Sequence | Description                                                 |
| :------- | :---------------------------------------------------------- |
| `x?`     | Ungreedy version of "x" (where "x" represents a quantifier) |

## Groups and Ranges

Groups allow you to tie multiple characters together, while ranges allow you to define a set of target characters. Note: Ranges are inclusive.

| Sequence  | Description                       |
| :-------- | :-------------------------------- |
| `(a\|b)`  | a or b                            |
| `(...)`   | Group                             |
| `(?:...)` | Passive Group                     |
| `[abc]`   | Range (a or b or c)               |
| `[^abc]`  | Not a or b or c                   |
| `[a-q]`   | Letter between a and q            |
| `[A-Q]`   | Upper case letter between A and Q |
| `[0-7]`   | Digit between 0 and 7             |

## Character Classes

| Sequence | Description          |
| :------- | :------------------- |
| `\n`     | nth group/subpattern |
| `\c`     | Control character    |
| `\s`     | White space          |
| `\S`     | Not white space      |
| `\d`     | Digit                |
| `\D`     | Not digit            |
| `\w`     | Word                 |
| `\W`     | Not word             |
| `\x`     | Hexadecimal digit    |
| `\O`     | Octal digit          |

## Escape Character

| Sequence | Description      |
| :------- | :--------------- |
| `\`      | Escape Character |

## Pattern Modifiers

| Sequence | Description                               |
| :------- | :---------------------------------------- |
| `g`      | Global match                              |
| `i`      | Case-insensitive                          |
| `m`      | Multiple lines                            |
| `s`      | Treat string as single line               |
| `x`      | Allow comments and white space in pattern |
| `e`      | Evaluate replacement                      |
| `U`      | Ungreedy pattern                          |

## Metacharacters

The following are metacharacters and must be escaped:
`^`, `[`, `$`, `{`, `*`, `(`, `\`, `+`, `)`, `?`, `<`, `>`

## POSIX

| Sequence     | Description                    |
| :----------- | :----------------------------- |
| `[:upper:]`  | Upper case letters             |
| `[:lower:]`  | Lower case letters             |
| `[:alpha:]`  | All letters                    |
| `[:alnum:]`  | Digits and letters             |
| `[:digit:]`  | Digits                         |
| `[:xdigit:]` | Hexadecimal digits             |
| `[:punct:]`  | Punctuation                    |
| `[:blank:]`  | Space and tab                  |
| `[:space:]`  | Blank characters               |
| `[:cntrl:]`  | Control characters             |
| `[:graph:]`  | Printed characters             |
| `[:print:]`  | Printed characters and spaces  |
| `[:word:]`   | Digits, letters and underscore |

## Special Characters

| Sequence | Description         |
| :------- | :------------------ |
| `\n`     | New line            |
| `\r`     | Carriage return     |
| `\t`     | Tab                 |
| `\v`     | Vertical tab        |
| `\f`     | Form feed           |
| `\xxx`   | Octal character xxx |
| `\xhh`   | Hex character hh    |

## String Replacement (Backreferences)

| Sequence | Description                 |
| :------- | :-------------------------- |
| `$n`     | nth non-passive group       |
| `$2`     | "xyz" in `/^(abc(xyz))$/`   |
| `$1`     | "xyz" in `/^(?:abc)(xyz)$/` |
| `` $` `` | Before matched string       |
| `$'`     | After matched string        |
| `$+`     | Last matched string         |
| `$&`     | Entire matched string       |

## Assertions

| Sequence       | Description              |
| :------------- | :----------------------- |
| `?=`           | Lookahead assertion      |
| `?!`           | Negative lookahead       |
| `?<=`          | Lookbehind assertion     |
| `?!=` or `?<!` | Negative lookbehind      |
| `?>`           | Once-only Subexpression  |
| `?()`          | Condition [if then]      |
| `?()\|`        | Condition [if then else] |
| `?#`           | Comment                  |

## Sample Patterns

| Pattern                                   | Description                       |
| :---------------------------------------- | :-------------------------------- |
| `^[A-Za-z0-9-]+$`                         | Letters, numbers and hyphens      |
| `^(\d{1,2}\/\d{1,2}\/\d{4})$`             | Date (e.g. 21/3/2006)             |
| `([^\s]+(?=\.(jpg\|gif\|png))\.\2)`       | jpg, gif or png image             |
| `^([1-9]{1}$\|^[1-4]{1}[0-9]{1}$\|^50$)`  | Any number from 1 to 50 inclusive |
| `^#?([A-Fa-f0-9]{3}(([A-Fa-f0-9]{3})?)$`  | Valid hexadecimal colour code     |
| `^(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,15}$` | Password Validation               |
| `\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,6}`          | Email addresses                   |
| `<(/?[^>]+)>`                             | HTML Tags                         |
