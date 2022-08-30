# RegEx

## Characters

| Characters     | Legend                                                               | Example   | Sample Match           |
| -------------- | -------------------------------------------------------------------- | --------- | ---------------------- |
| [abc], [a-c]   | Match the given characters/range of characters                       | abc[abc]  | abca, abcb, abcc       |
| [^abc], [^a-c] | Negate and match the given characters/range of characters            | abc[^abc] | abcd, abce, abc1, ...  |
| .              | Any character except line break                                      | bc.       | bca, bcd, bc1, b., ... |
| \d             | Any numeric character (equivalent to [0-9])                          | c\d       | c1, c2, c3 ...         |
| \D             | Any non-numeric character (equivalent to [^0-9])                     | c\D       | ca, c., c\* ...        |
| \w             | Any alphanumeric character (equivalent to [A-Za-z0-9_])              | a\w       | aa, a1, a\* ...        |
| \W             | Any non-alphanumeric character (equivalent to [A-Za-z0-9*])          | a\W       | a), a$, a? ...         |
| \s             | Usually used for white space, but can be used for new line, tab, etc | a\s       | a                      |
| \S             | Not a white space or equivalent like new line, tab, etc              | a\S       | aa                     |
| \t             | Matches a horizontal tab                                             | T\tab     | T ab                   |
| \r             | Matches a carriage return                                            | AB\r\nCD  | AB<br>CD               |
| \n             | Matches a linefeed                                                   | AB\r\nCD  | AB<br>CD               |
| \              | Escapes special characters                                           | \d        | 0, 1, ...              |
| x\|y           | Matches either "x" or "y"                                            | a\|b      | a, b                   |

## Assertions

| Characters | Legend                                                                        | Example    | Sample Match            |
| ---------- | ----------------------------------------------------------------------------- | ---------- | ----------------------- |
| ^          | Start of string or start of line depending on multiline mode                  | ^abc.\*    | abc, abd, abcd, ...     |
| $          | End of string or start of line depending on multiline mode                    | .\*xyz$    | xyz, wxyz, abcdxyz, ... |
| \b         | Matches a word character is not followed by another word-character            | My.\_\bpie | My apple pie, ...       |
| \B         | Matches a non-word boundary                                                   | c.\_\Bcat  | copycat, ...            |
| x(?=y)     | Lookahead assertion: Matches "x" only if "x" is followed by "y"               | \d+(?=€)   | $1 = 0.98€, ...         |
| x(?!y)     | Negative Lookahead assertion: Matches "x" only if "x" is followed not by "y"  | \d+\b(?!€) | $1 = 0.98€ , ...        |
| (?<=y)x    | Lookbehind assertion: Matches "x" only if "x" is preceded by "y"              | (?<=\d)\d  | $1 = 0.9\*8\*€, ...     |
| (?<!y)x    | Negative Lookbehind assertion: Matches "x" only if "x" is not preceded by "y" | (?<!\d)\d  | $1 = 0.98€, ...         |

## Quantifiers

| Characters | Legend                                                                  | Example  | Sample Match             |
| ---------- | ----------------------------------------------------------------------- | -------- | ------------------------ |
| x\*        | Matches the preceding item "x" 0 or more times                          | a\*      | a, aa, aaa, ...          |
| x+         | Matches the preceding item "x" 1 or more times, equivalent to {1,}      | a+       | aa, aaa, aaaa, ...       |
| x?         | Matches the preceding item "x" 0 or 1 time                              | ab?      | a, ab                    |
| x{n}       | Matches the preceding item "x" n times (n = positive integer)           | ab{5}c   | abbbbbc                  |
| x{n,}      | Matches the preceding item "x" at least n times (n = positive integer)  | ab{2,}c  | abbc, abbbc, abbbbc, ... |
| x{n,m}     | Matches the preceding item "x" at least n times & at most m times (n<m) | ab{2,3}c | abbc, abbbc              |

By default quantifiers are greedy (they try to match as much of the string as possible). The `?` character after the quantifier makes the quantifier non-greedy (it will stop as soon as it finds a match).

For Example: `\d+?` for a test string `12345` will match only `1`, but `\d+` will match the entire string `12345`.

## Flags

Flags are put at the end of the regular expression. They are used to modify how the regular expression behaves.

For Example: `/a/` for a test string `a` will match `a` only, but adding the flag `i` (`/a/i`) would match both `a` and `A`

| Characters | Legend                                                                                     |
| ---------- | ------------------------------------------------------------------------------------------ |
| d          | Generate indices for substring matches                                                     |
| g          | Global search                                                                              |
| i          | Case-insensitive search                                                                    |
| m          | Multi-line search                                                                          |
| s          | Allows . to match newline characters                                                       |
| u          | Treats a pattern as a sequence of Unicode code points                                      |
| y          | Perform a sticky search that matches starting at the current position in the target string |

## Thanks

Thanks to Tapajyoti for his [blog article](https://dev.to/ruppysuppy/the-regular-expression-regex-cheat-sheet-you-always-wanted-1c8h) from which all this information are coming from.
