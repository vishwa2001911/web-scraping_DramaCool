# web-scraping_DramaCool
# Python Web Scraping Using BeautifulSoup and CSV for Download Link from Drama Cool Website

This tutorial will teach you how to use Python Web Scraping with BeautifulSoup and CSV to get download links from Drama Cool website. 

## Prerequisites

To complete this tutorial, you will need: 

* Python 3 installed on your computer 
* Basic knowledge of HTML and web scraping
* [BeautifulSoup4](https://pypi.org/project/beautifulsoup4/) library installed
* [Requests](https://requests.readthedocs.io/) library installed

## Scraping Drama Cool Website

We will be using the [Drama Cool](https://dramacool.la/) website as our example. 

### Step 1: Import Libraries 

First, we need to import the necessary libraries to our Python script: 

```python
import requests
from bs4 import BeautifulSoup
import csv
```

### Step 2: Make a Request 

Next, we will make a request to the Drama Cool website to get the HTML content of the page: 

```python
url = 'https://dramacool.la/drama/'
response = requests.get(url)
```

### Step 3: Parse the HTML 

Now, we will parse the HTML content and create a BeautifulSoup object: 

```python
soup = BeautifulSoup(response.text, 'html.parser')
```

### Step 4: Find the Links 

Next, we will find the links on the page and store them in a list: 

```python
links = []
for link in soup.find_all('a'):
    if link.get('href').startswith('https://dramacool.la/drama/'):
        links.append(link.get('href'))
```

### Step 5: Create a CSV File 

Now, we will create a CSV file to store the download links: 

```python
with open('drama_cool_downloads.csv', 'w') as csv_file:
    writer = csv.writer(csv_file)
    writer.writerow(['Download Link'])
    for link in links:
        writer.writerow([link])
```

## Conclusion 

In this tutorial, we have learned how to use Python Web Scraping with BeautifulSoup and CSV to get download links from Drama Cool website. 

Happy Scraping!
