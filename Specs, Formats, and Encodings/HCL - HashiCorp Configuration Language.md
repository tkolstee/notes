Used by Packer and other HashiCorp products.
HCL2 is the current version.
File extension is `.app.hcl`, e.g. `pkr.hcl` for Packer
There is a (deprecated) [[JSON]] variant of the language (ext: `.app.json`)
Configuration files use UTF-8 encoding
UNIX-syle line endings (LF) rather than Windows-style (CRLF) are preferred.

```HCL
	<BLOCK TYPE> "<BLOCK LABEL>" "<BLOCK LABEL>" {
		# block body
		<IDENTIFIER> = <EXPRESSION> # Argument
	}
```

**Blocks** are containers for other content. They have:
- a type
- zero or more labels
- a body, which can contain:
	- comments
	- arguments which are name-value pairs
		- values can be an *expression* which is further processed at runtime.
	- nested blocks

----
# Sources
Source: [HCL Templates](https://www.packer.io/docs/templates/hcl_templates)

