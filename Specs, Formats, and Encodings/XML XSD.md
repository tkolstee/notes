XML Schema Definition
Defines an XML document schema, and is itself specified in XML

## Embedded Definition
```xml
<?xml version="1.0"?>
<xs:schema
  xmlns:xs="http://www.w3.org/2001/XMLSchema"
  targetNamespace="https://www.w3schools.com"
  xmlns="https://www.w3schools.com"
  elementFormDefault="qualified"
>

	<xs:element name="note">  
		<xs:complexType>  
			<xs:sequence>  
				<xs:element name="to" type="xs:string"/>  
				<xs:element name="from" type="xs:string"/>  
				<xs:element name="heading" type="xs:string"/>  
				<xs:element name="body" type="xs:string"/>  
			</xs:sequence>  
		</xs:complexType>  
	</xs:element>  


</xs:schema>

```

- XSD doc itself uses the XMLSchema namespace
- Root element is xs:schema
- targetNamespace specifies the namespace being defined
- xmlns attribute above says this is also our default namespace
- elementFormDefault attr says that the elements must be namespace-qualified

## External Definition
```xml
<?xml version="1.0"?>  
  
<note  
xmlns="https://www.w3schools.com"  
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xsi:schemaLocation="https://www.w3schools.com/xml note.xsd"
>  
	<to>Tove</to>  
	<from>Jani</from>  
	<heading>Reminder</heading>  
	<body>Don't forget me this weekend!</body>  
</note>

```

## Simple Elements
Can only contain text, not other elements
```xml
<xs:element name="lastName" type="xs:string" />
<xs:element name="language" type="xs:string" default="EN"/>
<xs:element name="language" type="xs:string" fixed="EN"/>
```

Built-in types for content:
- string
- decimal
- integer
- boolean
- date
- time

### Attributes

Always declared as simple types
```xml
<xs:attribute name="lang" type="xs:string"/>
<xs:attribute name="age" type="xs:integer" use="required"/>
<xs:attribute name="country" type="xs:string" default="US"/>
<xs:attribute name="species" type="xs:string" fixed="homo sapiens"/>
```

### Restrictions
```xml
<xs:element name="age">
	<xs:simpleType>
		<xs:restriction base="xs:string">
			<!-- restrictions go here -->
		</xs:restriction>
	</xs:simpleType>
</xs:element>
```

minInclusive and maxInclusive for numeric values:
```xml
<xs:minInclusive value="0"/>
<xs:maxInclusive value="120"/>
```

Enumeration for only fixed values:
```xml
<xs:enumeration value="Audi"/>
<xs:enumeration value="Golf"/>
<xs:enumeration value="BMW"/>
```

Pattern for regex patterns
```xml
<xs:pattern value="[A-Z][A-Z][A-Z]"/>
<xs:pattern value="[A-Za-z][a-z]*"/>
<xs:pattern value="male|female"/>
```
Preserve whitespace, convert to spaces, or collapse to single space
```xml
<xs:whiteSpace value="preserve"/>
<xs:whiteSpace value="replace"/>
<xs:whiteSpace value="collapse"/>
```
Length restrictions
```xml
<xs:length value="8"/>     <!-- exactly 8 chars -->
<xs:minLength value="5"/>  <!-- Min/Max Length -->
<xs:maxLength value="8"/>
```

type|meaning
---|---
enumeration|Defines a list of acceptable values
fractionDigits|Specifies the maximum number of decimal places allowed. Must be equal to or greater than zero
length|Specifies the exact number of characters or list items allowed. Must be equal to or greater than zero
maxExclusive|Specifies the upper bounds for numeric values (the value must be less than this value)
maxInclusive|Specifies the upper bounds for numeric values (the value must be less than or equal to this value)
maxLength|Specifies the maximum number of characters or list items allowed. Must be equal to or greater than zero
minExclusive|Specifies the lower bounds for numeric values (the value must be greater than this value)
minInclusive|Specifies the lower bounds for numeric values (the value must be greater than or equal to this value)
minLength|Specifies the minimum number of characters or list items allowed. Must be equal to or greater than zero
pattern|Defines the exact sequence of characters that are acceptable
totalDigits|Specifies the exact number of digits allowed. Must be greater than zero
whiteSpace|Specifies how white space (line feeds, tabs, spaces, and carriage returns) is handled

## Complex Elements
Simple elements contain text that can be given a type.
Complex elements can contain:
- nothing
- only other elements
- only text
- both

**Declaration Styles**

Inline
```xml
<xs:element name="employee">
	<xs:complexType>
	    ...
	</xs:complexType>
</xs:element>
```

Declared and referenced elsewhere
```xml
<xs:element name="employee" type="personinfo"/>
...
<xs:complexType name="personinfo">
	...
</xs:complexType>
```

**Containing only other elements**
```xml
<xs:complexType name="personinfo">
	<xs:sequence>
		<xs:element name="firstname" type="xs:string"/>
		<xs:element name="lastname"  type="xs:string"/>
	</xs:sequence>
</xs:complexType>
```
`sequence` indicates that the elements have to be in the listed order

**Extending a complex type**
Starting with `Personinfo` above which contains `firstname` and `lastname`:
```xml
<xs:complexType name="personwithaddress">
	<xs:complexContent>
		<xs:extension base="personinfo">
			<xs:sequence>
				<xs:element name="address" type="xs:string"/>
				<xs:element name="city" type="xs:string"/>
				<xs:element name="country" type="xs:string"/>
			</xs:sequence>
		</xs:extension>
	</xs:complexContent>
</xs:complexType>
```

**Defining an empty complex type with an attribute**
```xml
<xs:complexType name="productinfo">
  <xs:complexContent>
    <xs:restriction base="xs:integer">
      <xs:attribute name="prodid" type="xs:positiveinteger">
    </xs:restriction>
  </xs:ComplexContent>
</xs:complexType>
```
OR more simply:
```xml
<xs:complexType name="productinfo">
  <xs:attribute name="prodid" type="xs:positiveInteger">
</xs:complexType>
```
**Text-only complex type**
This type contains only simple content, so we add a simpleContent element around the content. You must define an extension OR a restriction within the simpleContent element.
```xml
<!-- with extension -->
<xs:complexType name="somename">
  <xs:simpleContent>
    <xs:extension base="basetype">
      ...
    </xs:estension>
  </xs:simpleContent>
</xs:complexType>

<!-- with restriction -->
<xs:complexType>
  <xs:simpleContent>
    <xs:restriction base="basetype">
      ...
    </xs:restriction>
  </xs:simpleContent>
</xs:complexType>


<!-- For Example: -->
<xs:complexType name="shoesize">
  <xs:simpleContent>
    <xs:extension base="xs:integer">
      <xs:attribute name="country" type="xs:string"/>
    </xs:extension>
  </xs:simpleContent>
</xs:complexType>
```

[Note taking Left off here](https://www.w3schools.com/xml/schema_complex.asp)

---
# Source
[XML Tutorial](https://www.w3schools.com/xml/default.asp)

