
## Modules and Packages
**Modules** are python files that hold functions that can be `import`ed into other python programs.
**Packages** are special types of modules which may contains other modules or packages in a hierarchy.

## Importing and Namespaces
When using `import`, each module is imported into its own namespace.
We can use `from` to import things into the global namespace, and `as` to change the names.

Example: Package `foo` contains functions `bar` and `baz`, and submodule `sub`.
`sub` contains function `quux`
```python
import foo
import foo.sub
```