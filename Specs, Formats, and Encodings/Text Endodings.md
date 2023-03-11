---
aliases: [ ASCII, UTF-8, ISO-Latin-1, CRLF, LF ]
---

## Encoding Schemes

### UTF-8
An encoding scheme which can represent Unicode with characters of more than 8 bits but uses mostly 8-bit characters so is relatively compatible with ASCII.

### ISO-8859-x
The ISO-8859-* codepages that represent 8-bit characters for different languages. 

English and many other Western languages typically use the "ISO-8859-1" character set also known as "ISO-Latin-1", which contains the first 256 characters of Unicode.

### ASCII
#### US-ASCII
7-bit character set (0-127) representing the original [[ASCII]] code. 

#### Extended ASCII
8-bit character set including standard US [[ASCII]] plus extended characters.

## Line Break Formats
Different operating systems use different characters to denote the end of a line in text documents.

### Characters
|Name|Abbreviation|ASCII Hex|ASCII Decimal|Escape|Control Character|
|--|--|--|--|--|--|
|Carriage Return|CR|13|0x0d|`\r`|`^M`|
|Linefeed|LF|10|0x0a|`\n`|`^J`|

### UNIX-Style
On UNIX and UNIX-like operating systems, line breaks in text documents are stored as a single LF.

### CRLF (Windows) Style
Windows systems store line breaks as a combination of two characters, CR and LF, (`\r\n`) in that order.

### Conversion
- In Linux, `unix2dos` and `dos2unix`  are often available for this purpose.
- `vim file.txt -c "set ff=unix" -c ":wq"`
- `tr -d '\015' <DOS-file >UNIX-file`
- `awk '{ sub("\r$", ""); print }' dos.txt > unix.txt`
- `sed -i.bak --expression='s/\r\n/\n/g' <file_path>`
