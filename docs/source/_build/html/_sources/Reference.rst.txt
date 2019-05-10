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

    :param input_document: the document (or tweet) as a string
    :param remove_RTs: remove the `'RT (****) '` from the front of the tweet text. Nothing is put in its place.
        (Ex: `"RT @johnsmith hey there!"` => `"hey there!"`)
    :param remove_hashtags: remove hashtags present from the input_document. Works by simply replacing the whole hashtag with nothing.
    :param remove_mentions: remove a mentioned user. Works by simply replacing the mentioned user handle with nothing.
    :param remove_urls: remove any urls present in the input_document. Works on http and https, including tiny urls. Simply replaces the url present with nothing.
    :param remove_emoji: remove any emojis found in the input_document with nothing. 
    :param remove_swears: remove russian swear words from the input_documents with nothing. 
    :param remove_special_chars: remove special characters, such as symbols, ampersands, arrows, etc. (Full list: `"[→©ђ°ѓ¡|\|=/▶►‼?~é̄̃`«»;џ�_●▪™“„#ї*&%¿$\-\”<>'|/?~`\+\：«»;_“„&^№€…)(—]"`)
    :rtype: clean formatted string

.. method:: Check_word([word], [lemmatize=True], [remove_proper_nouns=True], [allow_acronyms=False], [exclude_english_words=True])

    Check_word - checks if the word is good to be included for natural language analysis. It takes the specified word, and returns the a result dictionary.

    :param word: input the word to check
    :param lemmatize: lemmatize the word to get the root
    :param remove_proper_nouns: check to see if the words is a noun, in which case do not return it in the response object and return a status of `status: 'empty'`
    :param allow_acronyms: check if the word is an acronym, if so, do not return in.
    :param exclude_english_words: exclude english words from the Russian text.
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

    Semantics is an objects that supports the extraction of one capability - calculating semantic similarity between two documents.

    :param clean: lean the document to extract social media type content that will negatively impact analysis, such as hashtags, mentions urls, emoji, etc. Attribute_types (specify what you want):
            
            - None - do not clean document
            - 'All' - remove everything (full list below)
            - ['RT','hashtags','mentions','urls','emoji','swears','special_chars'] - if you want to remove specific things, specify any from the above as strings in a list, such as ['RT','mentions'] and only the specified ones will be cleaned.


.. method:: Get_similarity([docs_list], [use_normal_form=False], [clean_documents=True], [stop_words=None], [use_ngrams=True])

    Return the cosine similarity betweet two documents. Behind the scenes, sklearn's tf-idf approach (`TfidfVectorizer()`) is used.

    :param docs_list: a list of documents for which to get semantic similarity
    :param use_normal_form: lemmatization of all words present in the documents
    :param clean_documents: if `True`, utilize the `nlpru.Cleaner.Clean_documents()` method.
    :param stop_words: if you want to use a specific set of stop words, specify them as a list.
    :param use_ngrams: if you want to use 2-3 n-grams for the semantic similarity specify `True`. Otherwize, unigrams (i.e. single words) will be used.
    :rtype: depending on 'similarity_to' param, either similarity row vector of the first document to all others docs is returned, or (if 'All' is specified) matrix of of all docs against all others


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
