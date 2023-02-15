Library for web scraping with Python

```python
import requests
from bs4 import BeautifulSoup

url = 'https://www.example.com/index.html'
html_text = requests.get(url).text
soup = BeautifulSoup(html_text, 'html.parser')
```

`soup.find()` will find one element
`soup.find_all()` will find all matching elements

```python
soup.find(id='banner_ad').text   # Get text in HTML element for banner ad

for link in soup.find_all('a'):
    print(link.get('href'))
```

```python
for card in soup.find_all('div', class_='card topic'):
    cardname = card.find('div', class_='card-header').text
    txt = card.find('div', class_='card-text')
    for entry in txt.find_all('div', class_='entry'):
	    q = entry.find('div', class_='question').text
        a = entry.find('p', class_='answer').text
        print(f"-------------\nQuestion:\n{q}\nAnswer:\n{a}")
```


----
# See Also

[Web Scraping and Parsing HTML in Python with Beautiful Soup](https://www.twilio.com/blog/web-scraping-and-parsing-html-in-python-with-beautiful-soup)
[Beautiful Soup Documentation — Beautiful Soup 4.4.0 documentation](https://beautiful-soup-4.readthedocs.io/en/latest/)

