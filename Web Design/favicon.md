
Usual filename/URL `/favicon.ico`

Override type and location with [[Link Rel]] tag:
`<link rel="shortcut icon" type="image/png" href="image/favicon.png">`

Browser support
| Browser | ICO | PNG  | GIF  | Animated GIF | JPEG | APNG |  SVG   |
| ------- |:---:|:----:|:----:|:------------:|:----:|:----:|:------:|
| Edge    | Yes | Yes  | Yes  |      No      | Yes  | unk  |  Yes   |
| Firefox | 1.0 | 1.0  | 1.0  |     Yes      | Yes  | 3.0  |  41.0  |
| Chrome  | Yes | Yes  | 4.0  |      No      | 4.0  |  No  |   80   |
| IE      | 5.0 | 11.0 | 11.0 |      No      |  No  |  No  |   No   |
| Opera   | 7.0 | 7.0  | 7.0  |     7.0      | 7.0  | 9.5  |  44.0  |
| Safari  | Yes | 4.0  | 4.0  |      No      | 4.0  |  No  | NonStd |
|         |     |      |      |              |      |      |        |


Use:
| Browser |      Address Bar      | Address Bar Drop Down | Links Bar | Bookmarks |                Tabs                | Drag to Desktop |
| ------- |:---------------------:|:---------------------:|:---------:|:---------:|:----------------------------------:|:---------------:|
| Edge    |          No           |          Yes          |    Yes    |    Yes    |                Yes                 |       Yes       |
| Firefox |   1-12 yes<br>13+ no    |          Yes          |    Yes    |    Yes    |                Yes                 |       Yes       |
| Chrome  |          No           |          No           |    Yes    |    Yes    |                1.0                 |       No        |
| IE      |          7.0          |          No           |    5.0    |    5.0    |                7.0                 |       5.0       |
| Opera   | 7.0-12.17 yes<br>14+ no |          No           |    7.0    |    7.0    |                7.0                 |       7.0       |
| Safari  |          Yes          |          Yes          |    No     |    No     | 1-8 yes<br>9-11 no<br>12+ optional | No                |
|         |                       |                       |           |           |                                    |                 |

Square at 16, 32, 48, or 64 pixels
8, 24, or 32-bit color depth

[Favicon - Wikipedia](https://en.wikipedia.org/wiki/Favicon)
[ICO (file format) - Wikipedia](https://en.wikipedia.org/wiki/ICO_(file_format))

```HTML
<link rel="shortcut icon" href=".." />
<link rel="icon" type="image/gif" href=".." />
<link rel="icon" type="image/png" href=".." />
<link rel="icon" type="image/svg+xml" href=".." />  <!-- Not supported on Safari -->
<link rel="mask-icon" href="..." color="red" />     <!-- Only supported on Safari -->
```
