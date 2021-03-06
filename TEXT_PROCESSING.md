## Text Processing

## Simple

### bleach

https://github.com/mozilla/bleach

`pip install bleach`

Bleach is an allowed-list-based HTML sanitizing library that escapes or strips markup and attributes.

Bleach is intended for sanitizing text from *untrusted* sources. If you find yourself jumping through hoops to allow your site administrators to do lots of things, you're probably outside the use cases. Either trust those users, or don't.

Because it relies on [html5lib](https://github.com/html5lib/html5lib-python), Bleach is as good as modern browsers at dealing with weird, quirky HTML fragments. And *any* of Bleach's methods will fix unbalanced or mis-nested tags.

#### Basic use

```python
>>> import bleach

>>> bleach.clean('an <script>evil()</script> example')
u'an &lt;script&gt;evil()&lt;/script&gt; example'

>>> bleach.linkify('an http://example.com url')
u'an <a href="http://example.com" rel="nofollow">http://example.com</a> url'
```

------



## fuzzywuzzy

https://github.com/seatgeek/fuzzywuzzy

```
pip install fuzzywuzzy[speedup]
```

Fuzzy string matching like a boss. It uses [Levenshtein Distance](https://en.wikipedia.org/wiki/Levenshtein_distance) to calculate the differences between sequences in a simple-to-use package.

#### Basic use

```python
>>> from fuzzywuzzy import fuzz
>>> fuzz.ratio("this is a test", "this is a test!")
    97
>>> fuzz.partial_ratio("this is a test", "this is a test!")
    100
    
#token sort ratio    
>>> fuzz.ratio("fuzzy wuzzy was a bear", "wuzzy fuzzy was a bear")
    91
>>> fuzz.token_sort_ratio("fuzzy wuzzy was a bear", "wuzzy fuzzy was a bear")
    100
    
#token set ratio
>>> fuzz.token_sort_ratio("fuzzy was a bear", "fuzzy fuzzy was a bear")
    84
>>> fuzz.token_set_ratio("fuzzy was a bear", "fuzzy fuzzy was a bear")
    100
```



```python
>>> from fuzzywuzzy import process

>>> choices = ["Atlanta Falcons", "New York Jets", "New York Giants", "Dallas Cowboys"]
>>> process.extract("new york jets", choices, limit=2)
    [('New York Jets', 100), ('New York Giants', 78)]
>>> process.extractOne("cowboys", choices)
    ("Dallas Cowboys", 90)
```

You can also pass additional parameters to `extractOne` method to make it use a specific scorer. A typical use case is to match file paths:

```python
>>> process.extractOne("System of a down - Hypnotize - Heroin", songs)
    ('/music/library/good/System of a Down/2005 - Hypnotize/01 - Attack.mp3', 86)
>>> process.extractOne("System of a down - Hypnotize - Heroin", songs, scorer=fuzz.token_sort_ratio)
    ("/music/library/good/System of a Down/2005 - Hypnotize/10 - She's Like Heroin.mp3", 61)
```

### 

## Medium

### polyglot

https://github.com/aboSamoor/polyglot

```
pip install polyglot
```

Multilingual text (NLP) processing toolkit.

## Features

- Tokenization (165 Languages)
- Language detection (196 Languages)
- Named Entity Recognition (40 Languages)
- Part of Speech Tagging (16 Languages)
- Sentiment Analysis (136 Languages)
- Word Embeddings (137 Languages)
- Morphological analysis (135 Languages)
- Transliteration (69 Languages)