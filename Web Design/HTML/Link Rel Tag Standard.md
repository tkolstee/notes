Defines semantic relationships between two HTML documents.
Codified in [RFC 5988](https://www.rfc-archive.org/getrfc?rfc=5988#gsc.tab=0) and updated in [RFC 8288](https://www.rfc-archive.org/getrfc?rfc=8288#gsc.tab=0)

```HTML
<link rel="stylesheet" href="http://www.example.org/css/style.css">
```

| Relation Type | Description |
| ------------- | ----------- |
| alternate | Indicates that the link target is an alternate representation of the resource (e.g. a different format or language).|
| author | Indicates that the link target is the author of the resource.|
| canonical | Indicates that the link target is the preferred version of the resource, for use in search engine indexing and duplicate content detection.|
| describedby | Indicates that the link target provides a description of the resource.|
| license | Indicates that the link target provides licensing information for the resource.|
| next | Indicates that the link target is the next resource in a sequence.|
| prev | Indicates that the link target is the previous resource in a sequence.|
| search | Indicates that the link target provides a search interface for the resource.|
| stylesheet | Indicates that the link target is a stylesheet for the resource.|
| collection | Indicates that the link target is a collection of resources.
| first | Indicates that the link target is the first resource in a sequence.
| last | Indicates that the link target is the last resource in a sequence.
| prev-archive | Indicates that the link target is a resource that is a previous archive in a sequence of archives.
| next-archive | Indicates that the link target is a resource that is a next archive in a sequence of archives.
| up | Indicates that the link target is a parent resource of the current resource.

There are many others, and new link relation types may be defined in the future as new use cases arise.

The total number of standardized link relation types defined in RFC 5988 is not fixed, as new link relation types may be defined in the future. However, as of the publication of RFC 8288, which updates and replaces RFC 5988, there are approximately 50 standardized link relation types defined in the specification.

Additionally, there are many more link relation types defined in related specifications such as the HTML5 Link Types specification and the IANA Link Relations registry.

Sure! Here are the URLs for the HTML5 Link Types specification and the IANA Link Relations registry:

-   HTML5 Link Types [https://html.spec.whatwg.org/multipage/links.html#linkTypes](https://html.spec.whatwg.org/multipage/links.html#linkTypes)
-   IANA Link Relations registry [https://www.iana.org/assignments/link-relations/link-relations.xhtml](https://www.iana.org/assignments/link-relations/link-relations.xhtml)

Both of these resources provide a comprehensive list of standardized link relation types that can be used in HTML link elements and Link headers.