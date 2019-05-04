:mod:`nlpru` --- Reference of all methods
=========================================

This page contains an overview of all methods in **nlpru**

Cleaner
-------

To clean tweet (or general text) objects to prepare them for other Natural Language Processing methods

.. class:: Cleaner([language="ru"])

    The Cleaner object works by cleaning a specified piece of text for natural language analysis

    :param language: default for Russian text, no other languages are yet availible


.. method:: Clean_document([input_document], [remove_RTs=True], [remove_hashtags=True], [remove_mentions=True], [remove_urls=True], [remove_emoji=True], [remove_swears=False], [remove_special_chars=True])

    Clean_tweet - cleans the tweet, removing all mentions, urls, hashtags, and emojis

    :param input_document:
    :param remove_RTs:
    :param remove_hashtags:
    :param remove_mentions:
    :param remove_urls:
    :param remove_emoji:
    :param remove_swears:
    :param remove_special_chars:
    :rtype: formatted string

.. method:: Check_word([word], [lemmatize=True], [remove_proper_nouns=True], [allow_acronyms=False], [exclude_english_words=True])

    Check_word - checks if the word is good to be included for natural language analysis. It takes the specified word, and returns the a result dictionary.

    :param word: input the word to check
    :praram lemmatize: lemmatize the word to get the root
    :param remove_proper_nouns: 
    :param allow_acronyms: 
    :param exclude_english_words: exclude english words from the Russian text
    :rtype: response dictionary of the word and the status, conditional on the cleaning  done, and based on the specified parameters

        .. code-block:: python

            {
                "status": "", #'ok' or 'empty' possible
                "word": "" #'word' or '' possible 
            }


Similarity
----------

Calculate semantic similarity between two documents

.. class:: Semantics([clean=None])

    The Cleaner object works by cleaning a specified piece of text for natural language analysis

    :param clean: default for Russian text, no other languages are yet availible


.. method:: Get_similarity([docs_list], [use_normal_form=False], [clean_documents=True], [stop_words=None], [similarity_to='first'], [use_ngrams=True])

    Check_word - checks if the word is good to be included for natural language analysis. It takes the specified word, and returns the a result dictionary.

    :param docs_list:
    :param use_normal_form:
    :param clean_documents:
    :param stop_words:
    :param similarity_to:
    :param use_ngrams:
    :rtype: numpy array representing cosine similarity matrix


FindTopics
----------

Categorize tweets (or documents) by topic

.. class:: FindTopics([**kwargs])

    Detect topics in documents/tweets. 

    :param kwargs: under the hood, `FindTopics._init_()` can convert the inputs into `tweet_dict` (that is required for the method to work with). Henc all of the possible `kwargs` reference the `Convert_to_tweet_dictionary()` inputs


.. method:: Keyword_Match([topic_dict])

    Categorize the tweet/document depending on whether specific words are present

    :param topic_dict: a dictionary of topics is required as an input
    :rtype: dictionary of documents/tweets with the key as the uniqueid, and the text/topic as sub-dicts



Conversations
-------------

Categorize tweets/documents by topic by also taking conversation threat concepts into account

.. class:: Conversations([**kwargs])

    The Cleaner object works by cleaning a specified piece of text for natural language analysis

    :param kwargs: 


.. method:: Recategorize_topics([topic_for_which_to_check], [no_topic_label="none detected"], [**kwargs])

    Check_word - checks if the word is good to be included for natural language analysis. It takes the specified word, and returns the a result dictionary.

    :param topic_for_which_to_check:
    :param no_topic_label:
    :param kwargs:
    :rtype: dictionary of documents/tweets with the key as the uniqueid, and the text/topic as sub-dicts
