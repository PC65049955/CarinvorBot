Twitter Carnivore Retweet Bot
===================

This script is a simple program that searches for tweets containing the hashtags `#bitcoin`, `#beef`, and `#carnivore` and retweets them. It also includes an image, if the original tweet had one.

Requirements
------------

-   tweepy (A python library for accessing the Twitter API)
-   pickle

Installation
------------

1.  Install the required libraries by running the following command:



`pip install tweepy pickle`

1.  Create a new [Twitter developer account](https://developer.twitter.com/en/apps) and generate API keys.
2.  Replace the placeholders `consumer_key`, `consumer_secret`, `access_token`, and `access_token_secret` in the script with the actual keys.

Usage
-----

1.  Run the script using Python


`python twitter_retweet_bot.py`

1.  The script will continuously run and search for tweets containing the hashtags `#bitcoin`, `#beef`, and `#carnivore` every 30 seconds.
2.  When a tweet is found, it will check if it has already been retweeted before, If not it will retweet the tweet.
3.  The script also save the state of already_retweeted set across runs of the script to avoid retweeting the same tweet again.

Limitations
-----------

-   There is a rate limit for the number of requests that can be made to the Twitter API in a given time period. To avoid running into rate limit issues, the script includes error handling for the `tweepy.RateLimitError` exception.
-   If the script terminates unexpectedly, it will continue from the last state stored in the pickle file.
-   please make sure to have the correct permissions to interact with twitter API and to be compliant with twitter rules and terms of service.

Future Improvements
-------------------

-   Add more hashtags to search for
-   Search for tweets in a specific language
-   Add more advanced error handling
-   Integrate with a database to store the already retweeted tweets and also to store a fallback if the pickle file is corrupted
-   use a more robust library that has built-in rate limit handling and retry logic.

Please use this script responsibly and always keep in mind the Twitter API terms of service and developer agreement before posting any tweets.

How it works
------------

1.  The script uses the `tweepy` library to authenticate to the Twitter API using the provided API keys and creates an API object.
2.  It then attempts to open a pickle file named "already_retweeted.pkl" which holds a set of all the tweets that have already been retweeted in the past. If the file doesn't exist, it creates a new set.
3.  The script enters a while loop that continuously runs, it then uses the API object to search for tweets containing the hashtags `#bitcoin`, `#beef`, and `#carnivore`.
4.  For each tweet returned by the search, the script checks whether the tweet has an image and if it has not been retweeted before using the set of already_retweeted tweets.
5.  If the tweet is new, it then retweets the tweet, if the tweet had an image, it also includes the image in the retweet. If there is a rate limit error, script wait for the time mentioned in the retry-after header before continuing the operation.
6.  Once all the tweets from the current search have been processed, the set of already_retweeted tweets is pickled and saved to the "already_retweeted.pkl" file and script sleep for 30 seconds before running the search again.

Conclusion
----------

This script is a simple example of how to use the Twitter API to search for tweets and retweet them using the Python programming language and tweepy library. It can be used as a starting point to create more advanced Twitter bots or to gain more knowledge about how to interact with the Twitter API. Remember to always follow the Twitter API terms of service and developer agreement before posting any tweets.

Customization
-------------

You can customize the script to your liking by making changes to the search query, the hashtags that are being searched for, the time between searches and the file name of the pickle file used to store the state of the already_retweeted set.

You can also add more functionality to the script such as:

-   Searching for tweets in a specific language
-   Searching for tweets from a specific user or location
-   Filtering out tweets with specific keywords
-   Only retweeting tweets with a certain number of likes or retweets

Security
--------

As the script includes sensitive information such as Twitter API keys and access tokens, it's important to make sure that the script is stored in a secure location and is not shared with anyone who should not have access to it.

It's also important to note that this script is only intended to be run on a secure and protected environment like your local machine and not on a public server. Make sure to protect the script and the pickle file with a strong password.

By properly customizing, and securing the script, you can use it as a useful tool to gain insight into the topic you are interested in and also to automate engagement with your audience.

Please keep in mind that Twitter has rules and guidelines for automation, so make sure to read and understand them before using this or any other script to interact with the Twitter API.
