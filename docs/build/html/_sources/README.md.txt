# Welcome and overview

As you probably read in the home page, [**nlpru**](https://github.com/sergegoussev/nlpru) is a library meant to simplify Natural Language Processing and analysis of Russian text. While it is built for *Twitter* and for Russian language text, it can be used for Ukrainian text as well, and certain *methods* can be used as well as they are not language specific.

## Reasons to use **nlpru** 

The library makes it easy to use several methods commonly used with *natural language processsing*, such as categorizing tweets by topic, preprocessing (or cleaning text), etc. While several other libraries exist that can do many of these things, I found that general ones such as [**preprocessor**](https://github.com/s/preprocessor) don't seem to work well with Russian text. Russian specific libraries, such as [**pymorphy2**](https://github.com/kmike/pymorphy2) (which **nlpru** uses behind the scenes) offer useful NLP morphological analysis but not preprocessing or facilitation of different types of analysis.

## Installation

The *nplru* library is not yet availible via *Pypi*, hence to install it, it has to be downloaded from this gitab repository. This means there are two ways to do it:

You can install this library via git from github directly: 

    >>> pip install git+https://github.com/sergegoussev/nlpru.git

Or you can download the repo zip, and then use pip in the folder:

    >>> pip install .

## Quickstart

Once installed, you can call each method you require by importing it from nlpru. For example, let's say you have some tweets to preprocess:

```python
#import method
from nlpru import Clean

#initiate the method
c = Clean()

tweet = """п***ц какое расследование,почему б не указать,что наш Самарский ио @D_Azaroff
 ,вот он не бот,можно обратиться напрямую,не откажет"""

#use the method and save its output
clean_tweet = c.Clean_document(tweet, remove_swears=True)
```

If we print `clean_tweet`, it will return: 
`"какое расследование, почему б не указать, что наш Самарский ио @DAzaroff, вот он не бот, можно обратиться напрямую, не откажет"`