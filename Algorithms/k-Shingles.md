
k-shingles (or k-grams) are the set of strings of length *k* that appear in a document or data set.

These elements are overlapping using a sliding window of size *k*, and are collected as a set with duplicates ignored.

For example, if we split the input:

> Lorem ipsum dolor sit amet

into 5-shingles (5-grams), the set is:
`{ "lorem", "orem ", "rem i", "em ip", "m ips", " ipsu", "ipsum", "psum ", "sum d", "um do", "m dol", " dolo", "dolor", "olor ", "lor s", "or si", "r sit", " sit ", "sit a", "it am", "t ame", " amet"}`

6-shingles:
`{ "Lorem ", "orem i", "rem ip", "em ips", "m ipsu", " ipsum", "ipsum ", "psum d", "sum do", "um dol", "m dolo", " dolor", "dolor ", "olor s", "lor si", "or sit", "r sit ", " sit a", "sit am", "it ame", "t amet" }`

## Data Structures and Space Issues
The list of shingles takes up more space than the original text. This will be true of any *k* where *k* < *n*.

Data structures may store this as a binary (virtual) matrix of all possible shingles, showing which are contained in each set:

| 4-shingle | doc1 | doc2 | doc3 |
| ------- | ---- | ---- | ---- |
| aaaa    | 1    | 1    | 1    |
| aaab    | 0    | 1    | 0    |
| aaac    | 0    | 0    | 0    |
| ...     | 1    | 1    | 0    |
| ...     | 1    | 1    | 0    |
| ...     | 1    | 0    | 0    |
| zzzy    | 0    | 1    | 0    |
| zzzz    | 1    | 1    | 1    |

In some applications, you can hash shingles to save space (e.g. 9-shingles stored in 4 bytes). This will result in a small chance of collisions, but functions like a Screening Test; negative results are definitive and positive matches are presumptive.

----
## Sources
[[EWU CSCD340]]
