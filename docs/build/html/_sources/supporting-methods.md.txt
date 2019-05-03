# Supporting methods

## Convert to tweet dictionary

**nlpru** uses a dictionary method to process tweets -- both to categorize the **topics** and to assess **conversation thread** affects. For this it uses a dictionary structure:

```python
tweet_dict {
    "tweet id": {
        "text": "tweet text is stored here",
        "other": [
            "other vars are stored in a list here"
        ]
    }
}
```

If you want to utilize the method manually, you require:

@input parameters:
* **tweet_list** -- input the tweets as a list. In this case, you must specify the **location** of the tweet text and the tweet id in the list (counting from 0):
    * **tweet_text_index** -- specify the integer location of the tweet within the each tuple -- for ex:
    * **tweet_id_index** -- specify the integer location of the tweet id in the *tweet_list*. For ex:
        * `tweet_text_index = [('twtid','twt_text),...], tweet_text_index=1, tweet_id_index=0`
    * *NOTE*: the resulting dictionary is structured in order of input under the `other` category. In other words, the dictionary is structured as: 
    
And the folowing steps:
    
```python
from nlpru import Convert_to_tweet_dictionary

tweet_dict = Convert_to_tweet_dictionary(
    tweet_list=[('tweet id', 'tweet text',
                 'userid or other info...', ...), ...],
    tweet_text_index=1,
    tweet_id_index=0)
```