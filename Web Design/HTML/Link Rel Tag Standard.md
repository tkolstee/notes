Defines semantic relationships between two HTML documents.
Codified in [RFC 5988](https://www.rfc-archive.org/getrfc?rfc=5988#gsc.tab=0) and updated in [RFC 8288](https://www.rfc-archive.org/getrfc?rfc=8288#gsc.tab=0)



Sure! RFC 5988 is a specification that defines the syntax and semantics of Web Linking, a mechanism that allows resources to be linked together on the web using hyperlinks.

The key components of Web Linking are "links" and "link relation types". A "link" is an association between two resources, typically expressed as a hyperlink, while a "link relation type" is a keyword that identifies the nature of the relationship between the two resources.

The syntax of Web Linking is based on HTTP headers and follows a specific format, consisting of a Link header field with one or more link-value pairs. Each link-value pair consists of a URI, followed by a comma-separated list of link parameters, which are used to describe the relationship between the two resources.

The specification also defines a set of standardized link relation types, such as "stylesheet" for linking to stylesheets and "next" for indicating the next page in a paginated sequence. Web Linking can be used to provide additional context and metadata for resources, improving the user experience and facilitating resource discovery and sharing.

Overall, RFC 5988 provides a standardized way of linking resources on the web, making it easier to navigate and interact with the vast array of content available online.

RFC 5988 defines several standardized link relation types, which are intended to provide a consistent way of describing the relationship between linked resources. These include:

-   `alternate`: Indicates that the link target is an alternate representation of the resource (e.g. a different format or language).
-   `author`: Indicates that the link target is the author of the resource.
-   `canonical`: Indicates that the link target is the preferred version of the resource, for use in search engine indexing and duplicate content detection.
-   `describedby`: Indicates that the link target provides a description of the resource.
-   `license`: Indicates that the link target provides licensing information for the resource.
-   `next`: Indicates that the link target is the next resource in a sequence.
-   `prev`: Indicates that the link target is the previous resource in a sequence.
-   `search`: Indicates that the link target provides a search interface for the resource.
-   `stylesheet`: Indicates that the link target is a stylesheet for the resource.

These link relation types can be used in Link headers or HTML link elements to provide additional context and metadata for linked resources.

No, those are just a few examples of the standardized link relation types defined in RFC 5988. There are actually many more link relation types defined in the specification, as well as in other related specifications such as the HTML5 Link Types specification and the IANA Link Relations registry.

Some other standardized link relation types defined in RFC 5988 include:

-   `collection`: Indicates that the link target is a collection of resources.
-   `first`: Indicates that the link target is the first resource in a sequence.
-   `last`: Indicates that the link target is the last resource in a sequence.
-   `prev-archive`: Indicates that the link target is a resource that is a previous archive in a sequence of archives.
-   `next-archive`: Indicates that the link target is a resource that is a next archive in a sequence of archives.
-   `up`: Indicates that the link target is a parent resource of the current resource.

There are many others, and new link relation types may be defined in the future as new use cases arise.

The total number of standardized link relation types defined in RFC 5988 is not fixed, as new link relation types may be defined in the future. However, as of the publication of RFC 8288, which updates and replaces RFC 5988, there are approximately 50 standardized link relation types defined in the specification.

Additionally, there are many more link relation types defined in related specifications such as the HTML5 Link Types specification and the IANA Link Relations registry.

Sure! Here are the URLs for the HTML5 Link Types specification and the IANA Link Relations registry:

-   HTML5 Link Types: [https://html.spec.whatwg.org/multipage/links.html#linkTypes](https://html.spec.whatwg.org/multipage/links.html#linkTypes)
-   IANA Link Relations registry: [https://www.iana.org/assignments/link-relations/link-relations.xhtml](https://www.iana.org/assignments/link-relations/link-relations.xhtml)

Both of these resources provide a comprehensive list of standardized link relation types that can be used in HTML link elements and Link headers.