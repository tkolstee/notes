Defines semantic relationships between two HTML documents.
Codified in [RFC 5988](https://www.rfc-archive.org/getrfc?rfc=5988#gsc.tab=0) and updated in [RFC 8288](https://www.rfc-archive.org/getrfc?rfc=8288#gsc.tab=0)

```HTML
<link rel="stylesheet" href="http://www.example.org/css/style.css">
```

There are many more relation types in the RFCs ([RFC 5988](https://www.rfc-archive.org/getrfc?rfc=5988#gsc.tab=0) and  [RFC 8288](https://www.rfc-archive.org/getrfc?rfc=8288#gsc.tab=0)), [HTML5 Standards](https://html.spec.whatwg.org/multipage/links.html#linkTypes), and [IANA Link Relations registry](https://www.iana.org/assignments/link-relations/link-relations.xhtml](https://www.iana.org/assignments/link-relations/link-relations.xhtml), but stylesheet is the most common and widely supported.


| Relation Type | Description |
| ------------- | ----------- |
| alternate | Target is an alternate representation of the resource (e.g. a different format or language).|
| author | Target is the author of the resource.|
| canonical | Target is the preferred version of the resource, for use in search engine indexing and duplicate content detection.|
| describedby | Target provides a description of the resource.|
| license | Target provides licensing information for the resource.|
| next | Target is the next resource in a sequence.|
| prev | Target is the previous resource in a sequence.|
| search | Target provides a search interface for the resource.|
| stylesheet | Target is a stylesheet for the resource.|
| collection | Target is a collection of resources.
| first | Target is the first resource in a sequence.
| last | Target is the last resource in a sequence.
| prev-archive | Target is a resource that is a previous archive in a sequence of archives.
| next-archive | Target is a resource that is a next archive in a sequence of archives.
| up | Target is a parent resource of the current resource.

