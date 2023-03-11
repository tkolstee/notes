`cut -bSPEC [INFILE]`
`cut -cSPEC [INFILE]`
`cut -fSPEC [INFILE]`

`-b` bytes
`-c` characters
`-f` fields
`-d":"` change field delimiter (one char only, tab is default)

SPEC:
	`4`
	`1,2,8`
	`1-12`
	`1-3,5-12`
	`-12`
	`6-`



`--complement` print all BUT selector
`--output-delimiter=STRING`  Use string (of any length) as output delimiter (GNU)


