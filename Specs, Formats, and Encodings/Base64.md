
## Summary
Represents binary data in text-only channels (7-bit clean).
8-bit data is reinterpreted as 6-bit groupings (3x8bit becomes 4x6bit).
Each possible 6-bit value is assigned a character.
Last group is padded to a 4-character boundary with '='.

## Encoding

Each 3 bytes of 8-bit binary data is regrouped as 4 6-bit values (0-63).
Each 6-bit value has an associated character to represent each sextet.

|Dec|Bin|Represenation|
|---:|---|---|
|0-25|`000000` - `011001`|`A`-`Z`|
|26-51|`011010` - `110011`|`a`-`z`|
|52-61|`110100` - `111101`|`0`-`9`|
|62|`111110`|`+`|
|63|`111111`|`/`|

The last sextet is padded with trailing zeroes if necessary.
The textual representation is then padded with '=' to a 4-character boundary.

## Example

|Step|Value|
|---|---|
|Original Text|`Hello`|
|ASCII Hex|`48 65 6c 6c 6f`|
|Binary (8-bit)|`01001000 01100101 01101100 01101100 01101111`|
|Rearranged as 6-bit|`010010 000110 010101 101100 011011 000110 1111`|
|Last sextet padded with zeros|`010010 000110 010101 101100 011011 000110 111100`|
|Converted to characters|`SGVsbG8`|
|Padded to 4-character boundary|`SGVsbG8=`|

## Variants
Some standards use different values for characters 62 and 63, or different padding rules.

---
# Source
[Base64 - Wikipedia](https://en.wikipedia.org/wiki/Base64)

# See Also:
- [Base64 - Wikipedia](https://en.wikipedia.org/wiki/Base64)
- [Base64 Decode and Encode - Online](https://www.base64decode.org)
- [RFC 4648 - The Base16, Base32, and Base64 Data Encodings](https://datatracker.ietf.org/doc/html/rfc4648#section-4)
