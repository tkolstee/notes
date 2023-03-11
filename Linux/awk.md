
## Command Line Options

| Option            | Meaning                      |
| ----------------- | ---------------------------- |
| `-f program-file` | Read AWK program from file   |
| `-F ifs`          | Use `ifs` as field separator |
|                   |                              |


## Commands
| Command                  | Action                      |
| ------------------------ | --------------------------- |
| `awk '{ print }'`        | Print all whole input lines |
| `awk '/regex/ { print }` | Print lines matching regexp |
| `awk '{ print $1,$4 }'`  | Print fields 1 and 4        |
|                          |                             |

## Builtin Variables
| Variable        | Contents                                  |
| --------------- | ----------------------------------------- |
| `$0`            | Whole line                                |
| `$1`, `$2`, ... | Fields                                    |
| `NR`            | Number of records (lines)                 |
| `NF`            | Number of fields                          |
| `FS`            | Field Separator (white space)             |
| `RS`            | Record Separator (newline)                |
| `OFS`           | Output field separator (space)            |
| `ORS`           | Output record separator (newline)         |
| `FNR`           | Number of records (lines) in current file |
|                 |                                           |


## Addressing
conditions to use for addressing:
| Condition | Meaning |
| --------- | ------- |
| `/regex/` | Lines matching regex        |
| `NF==3`   | Lines with 3 fields        |
| `NR==7`   | Line 7        |
| `NR>3`    | Lines 4 and above        |
| `NF>2`    | Line with >2 fields        |
| `NF>0`    | Non-empty line        |

Ranges can be given with comma, e.g. `NF==2, /stuff/` (line 2 through line matching 'stuff')

## Examples
Find length of longest line:
`awk '{ if (length($0) > max) msx = length($0) } END { print max }'`

Count lines:
`awk 'END { print NR }'`

Print lines longer than 10 chars:
`awk 'length($0) > 10 { print }'`

Print lines matching foo but not commented:
`awk '/foo/ && !/^\s*#/'`

Find / Check for any string in specific column: 
`awk '{ if ($3 == "B6") print $0; }'`

Print square of numbers from 1..6:
`awk 'BEGIN { for(i=1;i<=6;i++) print "square of", i, "is",i*i; }'`

