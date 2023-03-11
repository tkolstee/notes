## Command Line Invocation

`sed COMMAND [INFILE...]`
`sed -e COMMAND [INFILE...]`
`sed -f SCRIPTFILE [INFILE...]`

Multiple `-e` or `-f` switches may be used.
If no `-e` or `-f` switch is used, first non-dashed argument is treated as the script.

one or more INFILEs may be given. If none is given, default is `-` which is STDIN.

### Sed Interpreter Script
Save as file and make executable. `#!` line will run whole script
```bash
#!/bin/sed -f
s/a/A/g
a/e/E/g
s/i/I/g
s/o/O/g
s/u/U/g
```

### Arguments and Quoting
```bash
#!/bin/sh
sed -n '/'"$1"'/p'
```

### Heredoc
```bash
#!/bin/bash
echo -n 'what is the value? '
read value
sed 's/XYZ/'$value'/' << EOF
The value is XYZ
EOF
```

### Optional Switches

| OSX/BSD     | GNU       | Description                                                                       |
| ----------- | --------- | --------------------------------------------------------------------------------- |
| `-E`        | `-r`      | Enable extended regex syntax                                                      |
| `-a`        |           | Delay opening (truncating) 'w' files until written to                             |
| `-I [ext]`  | `-i[EXT]` | Edit files in-place, treat as one long buffer, write backup with `ext` extension. |
| `-i [ext]`  |           | Edit files in-place, treat as separate buffers, write backup with `ext` extension |
| `-l` / `-u` |  `--unbuffered`         | Output is line buffered / unbuffered                                              |
| `-n`        | `-n`      | Do not print lines by default after processing                                    |
|             | `-s`      | Consider files as separate buffers (as with OSX/BSD `-i`)                         |

#### GNU-only Switches
| Switch              | Description                               |
| ------------------- | ----------------------------------------- |
| `--debug`           | Annotate program execution                |
| `--follow-symlinks` | Follow symlinks when processing in-place  |
| `-l N`              | Desired line-wrap length for `l` command. |
| `--posix`           | Disable GNU extensions                    |
| `--sandbox`         | Disable e/r/w comamands                   |
| `-z`                | Separate lines with NUL characters                                          |

### Exit Status
| Exit Status | Meaning                                               |
| ----------- | ----------------------------------------------------- |
| 0           | Success                                               |
| 1           | Invalid command/syntax/regex                          |
| 2           | Problem opening an input file, continuing with others |
| 4           | I/O error or serious processing error, aborted        |

## Addressing

| Address     | Meaning                                                         |
| ----------- | --------------------------------------------------------------- |
| integer     | Literal line number                                             |
| regexp      | Line matching regexp                                            |
| `$`         | Last line of buffer (file if using `-s`)                        |
| `addr,addr` | Range from first address to last, inclusive                     |
| `0,addr`    | Range where first line can contain the ENDING line in the range |
| `addr,+N`   | Matching address and next `N` lines                             |
| `addr,~N`   | Matching address and all lines up to a multiple of N                                                                |
| `addr~num`  | Start at addr and operate on each `num`th line afterward        |
| `addr!`     | Invert matching lines                                           |


## Script Commands
General commands are of the form `[addr]X[options]`, where:

`X` is a single-letter sed command
`[addr]` is an optional line address
`[options]` are command-specific

| command         | Addressing  | Description                                                                                                                 |
| --------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------- |
| `# text`        | None        | Comment                                                                                                                     |
| `{`             | 0, 1, Range | Begin block, ends with `}`                                                                                                  |
| `a \`<br>`text` | 0, 1        | Append text with embedded newline                                                                                           |
| `i \`<br>`text` | 0, 1        | Insert text with embedded newline                                                                                           |
| `c \`<br>`text` | 0, 1, Range | Replace selected lines with text                                                                                            |
| `q exitcode`    | 0, 1        | Quit, printing pattern space.                                                                                               |
| `Q exitcode`    | 0, 1        | Quit, not printing pattern space                                                                                            |
| `r filename`    | 0, 1        | Append text from filename                                                                                                   |
| `R filename`    | 0, 1        | Append ONE line from filename (GNU)                                                                                         |
| `d`             | 0, 1, Range | Delete pattern space, start next cycle                                                                                      |
| `D`             | 0, 1, Range | If no newline in pattern space, act like `d`.<br>If newline, delete text to newline and restart with current pattern space. |
| `h` or `H`      | 0, 1, range | Copy/append pattern to hold space                                                                                           |
| `g` or `G`      | 0, 1, range | Copy/append hold space to pattern space                                                                                     |
| `l`             | 0, 1, range | List line in 'visually unambiguous' form                                                                                    |
| `l width`       | 0, 1, range | Like `l` but break at `width` chars (GNU)                                                                                   |
| `n` or `N`      | 0, 1, range | Read/append next line of input into pattern space                                                                           |
| `p`             | 0, 1, range | Print current pattern space                                                                                                 |
| `P`             | 0, 1, range | Print up to first newline of pattern space                                                                                  |
| `s/regex/repl/` | 0, 1, range | Substitute regex matches for replacement string                                                                             |
| `w filename`    | 0, 1, range | Write pattern space to filename                                                                                             |
| `W filename`    | 0, 1, range | Write first line of pattern space to filename (GNU)                                                                         |
| `x`             | 0, 1, range | Exchange pattern/hold spaces                                                                                                |
| `y/src/dest/`   | 0, 1, range | Transliterate chars in src to dest (like UNIX `tr`)                                                                         |
| `: label`       |             | Label for `b`, `t`, and `T` commands                                                                                        |
| `t label`       |             | If `s///` has substituted successfully since last line read or last `t` command, branch to label                            |
| `T label`       |             | If `s///` has NOT substituted successfully since last line read or last `T` command, branch to label (GNU)                  |
| `b label`       |             | Branch to label unconditionally                                                                                                                            |


## Regular Expressions

### Backreferences
| Backreference    | Interpretation                                                               |
| ---------------- | ---------------------------------------------------------------------------- |
| `&`              | Entire matched string                                                        |
| `\1`, `\2`, etc. | Matched portion of pattern (can be used in same regex, not just replacement) |

### Suffixes
| Suffix     | Meaning                                   |
| ---------- | ----------------------------------------- |
|            |                                           |
| g          | Global, match all occurrences             |
| I          | Ignore case                               |
| M          | Multiline match^[`^` and `$` represent beg/end of line, \` and `'` beg/end buffer]                           |
| 1, 2, etc. | Match only nth occurrence of that pattern |

----
# Sources
[sed, a stream editor](https://www.gnu.org/software/sed/manual/sed.html)
[Grymoire.com - Sed](https://www.grymoire.com/Unix/Sed.html)
[sed cheat sheet](https://www.grymoire.com/Unix/SedChart.pdf)


