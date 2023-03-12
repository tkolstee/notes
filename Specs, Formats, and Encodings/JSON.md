JavaScript Object Notation

-   Object notation using curly braces { }
-   Key-value pairs separated by a colon :
-   Strings enclosed in double quotes " "
-   Numbers (in this case an integer) without quotes
-   Boolean values (true and false) without quotes
-   Arrays enclosed in square brackets [ ]
-   Nested objects
-   Nested arrays
-   Multiple levels of nesting within an object
-   Comments are not supported in JSON

````ad-example
title: Sample JSON file
collapse: false
```JSON
{
  "name": "John",
  "age": 35,
  "isMarried": true,
  "hobbies": [
    "reading",
    "music",
    "traveling"
  ],
  "address": {
    "street": "123 Main St",
    "city": "Anytown",
    "state": "CA",
    "zip": "12345"
  },
  "friends": [
    {
      "name": "Mary",
      "age": 28,
      "isMarried": false
    },
    {
      "name": "David",
      "age": 42,
      "isMarried": true
    }
  ],
  "education": {
    "degree": {
      "name": "Bachelor of Science",
      "major": "Computer Science",
      "year": 2010
    },
    "certifications": [
      {
        "name": "Certified Information Systems Security Professional (CISSP)",
        "year": 2015
      },
      {
        "name": "Project Management Professional (PMP)",
        "year": 2016
      }
    ]
  }
}
```
````




----
# Source
[JSON](https://www.json.org/json-en.html)
