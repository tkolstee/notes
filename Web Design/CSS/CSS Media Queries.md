```css
/* Only make H1 red when being printed */

@media print {
	h1 {
		color: red;
	}
}

/* Other queries */
@media speech { ...  }
@media only screen and (max-width: 600px) { ... }
@media screen and (min-width: 900px) { ... }
```