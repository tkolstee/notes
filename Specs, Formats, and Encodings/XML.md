eXtensible Markup Language

```toc
```

## Syntax
### Well-Formed vs. Valid
The XML rules of syntax are common to all XML documents. Those that conform to those standards are **well-formed**.

Additional specifications define the *schema* which a document purports to conform with and against which they can be validated. Documents that validate against their schema are **valid**.

## Format of an XML Document

All XML documents will contain
- A Metadata portion, which consists of
	- (Required) An [[XML Declaration]] identifying the document as XML, and often giving the version of the XML standard and the character encoding type used. The XML declaration comes before any other content.
	- (Optional) A reference to the schema used by the document, which may be in [[XML XSD]] or [[XML DTD 1]] formats.
- A body, contained within a singular top-level [[XML Element]].

[[XML Comments]]s may appear after any of these other elements, but not before the XML declaration.

There is one and only one [[XML Element]] (the root element) that encloses the entire body of the XML document. Other elements and text may be nested inside it. 

Unlike with HTML, whitespace is preserved as-is.

Line breaks are stored in UNIX-Style format (see [[Line Break Formats 2]]) by convention.

### Disallowed Characters
`<` and `&` characters are not allowed as literals. Use XML entities to represent these characters (`&lt;` and `&amp;` respectively).

## Declaration
Also known as the *prolog*, this identifies the document as XML and can also specify attributes of the document. This must be the first content given in the document.

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

### Attributes

- version: the XML specification version. Currently only "1.0" and "1.1" are officially used.
- encoding: The [[Text Encoding Schemes]] scheme used within this document.
- standalone: Defaults to "no" but can be "yes", indicating that everything needed to parse the document is included within the document (inline or no schema).

## Comments

Start with `<!--` and end with `-->`.

Comments can contain any text except a double-dash.

The can appear anywhere in an XML document EXCEPT:
- before the XML Declaration
- within attribute values or strings
- nested inside other comments

## Schema Definition
XML Schema can be defined in [[XML DTD 1]] or [[XML XSD]] forms, and in either embedded or external specifications.

## Elements
Building blocks of XML documents.

There should be one root-level element that makes up the body of the document, with all other elements nested inside it. The name of this root level element is defined in the schema if given.

### Tags
Delimiters at the start and end of elements. Enclosed in angle brackets (`<>`) and contain the name of the element.

Elements that contain things have starting and ending tags. Ending tags have a slash before the element name.

```XML
<myelement>contents of element</myelement>
```

Empty elements can be specified in starting and ending tags or an empty tag with a slash before the closing bracket

```XML
<myemptyelement />
```

### Element Names
Case sensitive and cannot contain spaces.
Contain letters, digits, hyphens, underscores, and periods.
Can only start with letter or underscore.
Cannot start with "xml" in any mix of upper/lowercase

Use of non-English letters is legal but discouraged.

### Attributes
Elements can have attributes which have a name and value. 
Specified inside the starting tag.
XML schema can make attributes required or constrain values.
```XML
<image width="400" url="http://url.to/image.jpg" />
```
#### Attribute Names
Each element name must be unique within a tag.
Naming rules are similar to element names.

#### Attribute Values
Each attribute can only contain one value.
Values must be quoted.

#### Attributes vs. Child Elements
Attributes cannot contain multiple values, and are more difficult to expand, code for, and validate. Where possible child elements are often a better solution:
```XML
<car color="blue" make="ford" model="fiesta">
```

```XML
<car>
  <color>blue</color>
  <make>ford</make>
  <model>fiesta</model>
</car>
```

#### ID Attributes
Attributes named 'id' are often useful to differentiate many instances of the same element.

### Nesting Elements
Elements can contain other elements, which must be properly nested.
```XML
<note>
  <title>Hi there</title>
  <body>Hello, world!</body>
<note>
```

## Entities
Used for expansion of text, like macros or escape characters.
Specified with an ampersand, a name, and a semicolon.

Built-in XML Entities
| Entity   | Expansion | Name Meaning   |
| -------- | --------- | -------------- |
| `&lt;`   | `<`       | less-than      |
| `&gt;`   | `>`       | greater-than   |
| `&amp;`  | `&`       | ampersand      |
| `&apos;` | `'`       | apostrophe     |
| `&quot;` | `"`       | quotation mark |

More entities can be defined in the document's schema (DTD or XSD).

## Namespaces
Prevent element name conflicts using namespaces. 

Ex: distinguish HTML table from dining room table
```xml
<h:table xmlns:h="http://www.w3.org/TR/html4/">...</h:table>
<f:table xmlns:f="https://www.w3schools.com/furniture">...</f:table>
```

Namespaces can also be declared in the root element:
```xml
<root
	  xmlns:h="http://www.w3.org/TR/html4/"
	  xmlns:f="https://www.w3schools.com/furniture"
>
	...
	<h:table>
		<h:tr>
			...
		</h:tr>
	</h:table>
</root>
```

NOTE: The URI is not used to parse or validate the document.

All children of these elements inherit their namespace.
You can use this to set a  **Default Namespace**
```xml
<table xmlns="http://www.w3.org/TR/html4/">
  <tr>
    ... <!-- Note no "namespace:element" notation here -->
```


---
# Source
[XML Tutorial](https://www.w3schools.com/xml/default.asp)