`load`
- takes absolute or relative path to working dir
- returns true
- raises LoadError
- globals are imported but not locals
- Calling multiple times re-executes code
- Looks in `$LOAD_PATH` or current dir

`require`
- Only executes once, returns `false` if already executed
- Keeps track in `$LOADED_FEATURES`
- No need to include file extension (`.rb`, `.so`, `.o`, `.dll`)
- Does not check cur dir, only `$LOAD_PATH`

`require_relative`
- Like require but takes path from current file (not cwd)