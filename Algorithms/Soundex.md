

Soundex is a hashing algorithm applied to a textual word to generate a hash code which is supposed to represent the way the word sounds.

It's often used in geneaology or vital records to consolidate the various ways the spelling of a name can change over time.

The first four characters of Florida drivers' license numbers are a Soundex derived from the holder's last name.

## Steps

1.  Remove H and W
2.  Convert letters to digits
| Letters         | Digit |
| --------------- | ----- |
| A E I O U Y     | 0     |
| B F P V         | 1     |
| C G J K Q S X Z | 2     |
| D T             | 3     |
| L               | 4     |
| M N             | 5     |
| T               | 6     |

3.  Remove adjacent repeating digits (reduce to 1 digit)
4.  Cross out first digit unless 1st letter was H or W
5.  Cross out zeroes
6. Add back first letter of original string
7.  Trim to letter + 3 digits. Pad with trailing zeros if < 3 digits

## Example
`````ad-example

| Step | KOLSTEE | HASSELHOFF | THOMPSON | JACKSON |
|--|--|--|--|--|
| 1 - Remove H/W | KOLSTEE |  ASSELOFF | TOMPSON | JACKSON |
| 2 - Convert letters | 2042300 | 02204011 | 6051205 | 2022205 |
| 3 - Remove repeats | 204230 | 020401 | 6051205 | 20205 |
| 4- Remove first | 04230 | 020401 | 051205 | 0205 |
| 5 - Remove zeroes | 423 | 241 | 5125 | 25 |
| 6 - Add 1st letter | K423 | H241 | T5125 | J25 |
| 7 - Trim or Pad|K423|H241|T512|J250|
`````

