Encoding Arbitrary Strings
```javascript
var value = 'Hellö Wörld@Javascript'
var encodedValue = encodeURIComponent(value)
console.log(encodedValue)
```

`encodeURIComponent()` should be used to encode query strings or path segments but not full URLs.
```javascript
var baseUrl = 'https://www.google.com/search?q='
var query = 'Hellö Wörld@Javascript'

// encode only the query string
var completeUrl = baseUrl + encodeURIComponent(query)
console.log(completeUrl)

// https://www.google.com/search?q=Hell%C3%B6%20W%C3%B6rld%40Javascript
```
