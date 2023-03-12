
Cryptographic hash algorithms like MD5, SHA1, etc. are sensitive to changes such that one byte of change in the input value changes the entire hash value output to a large (and unpredictable) degree.

Robust hash algorithms are particularly meant to do the opposite - they should work across small and perhaps even large changes in input.

Algorithms such as these are used to compare two inputs for similarity and not just identical inputs. Examples might include:
- Detection of a specific image that is resistant to cropping, color correction, printing out and scanning, etc.
- Detection of plagarism in text content
- Detection of similar forms of a word or similar-sounding words ([[Soundex Algorithm]])

Unlike cryptographic hashes, which can be applied to any arbitrary input, robust hashes are typically tuned for a particular type of content (text, images, numeric data, etc.)

There are several different approaches which seem to fall into a few broad categories and can be used together in depth:

**Screening Tests**

Exclusionary tests which are skewed toward more false positives and no or very few false negatives. Positive answers are not authoritative and so are submitted to further tests but negative results are rejected immediately.

**Feature Extraction**

As with machine learning, this is a technique that relies upon heuristics to extract a set of features which is characteristic of the input. These vary widely depending upon the type of content being examined.

**Statistically-based Tests**

These depend upon statistical features of the data being examined. For example an image with similar contrast that has been brightened or darkened might have similar standard deviation values for luminance, but a different mean and median. Images where the contrast is adjusted might have similar mean and median but different standard deviations. Photos with similar subject matter might have a characteristic distribution of hues.

**Extract matching**

This involves extracting some features of the data while rejecting others and comparing the similarity of the extracted data. Examples might include:
- Building a [[trie]] of *k*-word phrases from the document will reveal similar results for similar texts.
- Hashing fixed-length blocks will detect similar blocks, even if those blocks are shifted in position. This is dependent upon the data being aligned on block boundaries. 

**Context**
- Features separate from content may make good comparisons, such as filenames, metadata, etc.


----
## See Also:
[[Finding Similarities in a Large Filesystem]]