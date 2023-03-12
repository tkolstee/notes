A Document Type Definition (DTD) defines the schema for an [[XML]] document.
It is not written in XML itself, but in a language specific to DTDs.


## Overview
An XML document need not specify a schema to be well-formed, but if it does it must conform to the schema to be considered valid.

## Example
DTD document:
```DTD
<!ELEMENT note (to, from, heading, body)>
<!ELEMENT to      (#PCDATA)>
<!ELEMENT from    (#PCDATA)>
<!ELEMENT heading (#PCDATA)>
<!ELEMENT body    (#PCDATA)>
```

An XML document that references the DTD above:
```XML
<?xml version="1.0"?>
<!DOCTYPE note SYSTEM "https://www.w3schools.com/xml/note.dtd">
<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note>
```

DTDs can also be specified inline:
```XML
<?xml version="1.0"?>  
<!DOCTYPE note [  
<!ELEMENT note (to,from,heading,body)>  
<!ELEMENT to (#PCDATA)>  
<!ELEMENT from (#PCDATA)>  
<!ELEMENT heading (#PCDATA)>  
<!ELEMENT body (#PCDATA)>  
]>  
<note>  
<to>Tove</to>  
<from>Jani</from>  
<heading>Reminder</heading>  
<body>Don't forget me this weekend</body>  
</note>
```

## Elements
Elements are specified using the ELEMENT component.

The first text immediately after the !ELEMENT text is the name of the element. Additional parameters show what the element can contain:

```DTD
# Empty element, e.g. "<br />"
<!ELEMENT br EMPTY>    

# Any type of parseable data
<!ELEMENT note ANY>

# Element that can contain parsed character data
<!ELEMENT from (#PCDATA)>

# All child elements must appear in the same sequence
<!ELEMENT note (to,from,heading,body)>

# Child element must appear once
<!ELEMENT note (message)>

# Child element can appear one or more times
<!ELEMENT note (message+)>

# Child element can appear zero or more times
<!ELEMENT note (message*)>

# Child element can appear zero or one time
<!ELEMENT note (message?)>

# Either/or
<!ELEMENT note (to,from,header,(message|body))>

# Mixed
<!ELEMENT note (#PCDATA|to|from|header|message)*>
```

### Element Attributes
`<!ATTLIST element-name attribute-name attribute-type attribute-value>`

```DTD
<!ELEMENT person type EMPTY>
<!ATTLIST person name CDATA #REQUIRED>     # Required, no default
<!ATTLIST person age CDATA #IMPLIED>       # Optional, no default
<!ATTLIST person citizen (yes|no) "yes">   # Enumerated options with default
<!ATTLIST person present "yes" #FIXED>     # Anything other than "yes" is an error
```
|attribute-type|description|
|--|--|
|CDATA|Character Data|
|(en1\|en2\|..)|Enumerated list of possible values|
|ID|Value is a unique ID|
|IDREF|ID of another element|
|IDREFS|List of other IDs|
|NMTOKEN|Valid XML name|
|NMTOKENS|List of valid XML names|
|ENTITY|Value is an entity|
|NOTATION|Value is the name of a notation|
|xml:|Predefined XML value|

|attribute-value|description|
|--|--|
|value|Default value of the attribute|
|\#REQUIRED|attribute is required|
|\#IMPLIED|attribute is optional|
|\#FIXED value|attribute value is fixed|

## Entities
[[Documents and Encodings/XML/XML#Entities|Entities]] are like text expansions and their values can be defined in the DTD:

```DTD
<!ENTITY author "John Smith">
<!ENTITY copyright "Copyright &copy; &year;, &author;">
```

They can also be references to entities from other DTDs:
```DTD
<!ENTITY author SYSTEM "https://www.example.org/entities.dtd">
```

## PCDATA (Parsed Character Data)
This is data where entities will be expanded and the content validated by a parser.

For example, an element may contain other elements (PCDATA) which then must be validated.

PCDATA should not contain any `&`, `<`, or `>` characters, and their respective [[Documents and Encodings/XML/XML#Entities|Entities]]should be used to represent them.

## CDATA
This is data that will NOT be expanded or parsed. Tags inside CDATA will not be treated as markup and entities will not be expanded.

## Other DTD Examples
TV Schedule:
```DTD
<!DOCTYPE TVSCHEDULE [  
  
<!ELEMENT TVSCHEDULE (CHANNEL+)>  
<!ELEMENT CHANNEL (BANNER,DAY+)>  
<!ELEMENT BANNER (#PCDATA)>  
<!ELEMENT DAY (DATE,(HOLIDAY|PROGRAMSLOT+)+)>  
<!ELEMENT HOLIDAY (#PCDATA)>  
<!ELEMENT DATE (#PCDATA)>  
<!ELEMENT PROGRAMSLOT (TIME,TITLE,DESCRIPTION?)>  
<!ELEMENT TIME (#PCDATA)>  
<!ELEMENT TITLE (#PCDATA)>   
<!ELEMENT DESCRIPTION (#PCDATA)>  
  
<!ATTLIST TVSCHEDULE NAME CDATA #REQUIRED>  
<!ATTLIST CHANNEL CHAN CDATA #REQUIRED>  
<!ATTLIST PROGRAMSLOT VTR CDATA #IMPLIED>  
<!ATTLIST TITLE RATING CDATA #IMPLIED>  
<!ATTLIST TITLE LANGUAGE CDATA #IMPLIED>  
]>
```

Newspaper Article:
```DTD
<!DOCTYPE NEWSPAPER [  
  
<!ELEMENT NEWSPAPER (ARTICLE+)>  
<!ELEMENT ARTICLE (HEADLINE,BYLINE,LEAD,BODY,NOTES)>  
<!ELEMENT HEADLINE (#PCDATA)>  
<!ELEMENT BYLINE (#PCDATA)>  
<!ELEMENT LEAD (#PCDATA)>  
<!ELEMENT BODY (#PCDATA)>  
<!ELEMENT NOTES (#PCDATA)>  
  
<!ATTLIST ARTICLE AUTHOR CDATA #REQUIRED>  
<!ATTLIST ARTICLE EDITOR CDATA #IMPLIED>  
<!ATTLIST ARTICLE DATE CDATA #IMPLIED>  
<!ATTLIST ARTICLE EDITION CDATA #IMPLIED>  
  
<!ENTITY NEWSPAPER "Vervet Logic Times">  
<!ENTITY PUBLISHER "Vervet Logic Press">  
<!ENTITY COPYRIGHT "Copyright 1998 Vervet Logic Press">  
  
]>
```

Product Catalog:
```DTD
<!DOCTYPE CATALOG [  
  
<!ENTITY AUTHOR "John Doe">  
<!ENTITY COMPANY "JD Power Tools, Inc.">  
<!ENTITY EMAIL "jd@jd-tools.com">  
  
<!ELEMENT CATALOG (PRODUCT+)>  
  
<!ELEMENT PRODUCT  
(SPECIFICATIONS+,OPTIONS?,PRICE+,NOTES?)>  
<!ATTLIST PRODUCT  
NAME CDATA #IMPLIED  
CATEGORY (HandTool|Table|Shop-Professional) "HandTool"  
PARTNUM CDATA #IMPLIED  
PLANT (Pittsburgh|Milwaukee|Chicago) "Chicago"  
INVENTORY (InStock|Backordered|Discontinued) "InStock">  
  
<!ELEMENT SPECIFICATIONS (#PCDATA)>  
<!ATTLIST SPECIFICATIONS  
WEIGHT CDATA #IMPLIED  
POWER CDATA #IMPLIED>  
  
<!ELEMENT OPTIONS (#PCDATA)>  
<!ATTLIST OPTIONS  
FINISH (Metal|Polished|Matte) "Matte"  
ADAPTER (Included|Optional|NotApplicable) "Included"  
CASE (HardShell|Soft|NotApplicable) "HardShell">  
  
<!ELEMENT PRICE (#PCDATA)>  
<!ATTLIST PRICE  
MSRP CDATA #IMPLIED  
WHOLESALE CDATA #IMPLIED  
STREET CDATA #IMPLIED  
SHIPPING CDATA #IMPLIED>  
  
<!ELEMENT NOTES (#PCDATA)>  
  
]>
```

----
# Source
[XML Tutorial](https://www.w3schools.com/xml/default.asp)
