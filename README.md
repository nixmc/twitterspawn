# Twitterspawn

Uses [gevent](http://www.gevent.org/) and [requests](http://docs.python-requests.org/) to spawn multiple workers that fetch from the Twitter API in a scalable way, while staying within Twitter's rate limits.

See [example.py](https://github.com/swinton/twitterspawn/blob/develop/example.py) for a working example.

## Usage

Basically:

```python
import twitterspawn

# Define callback (can define 1 per request)
def callback(response):
    print "Got", response

# Add requests + callbacks
twitterspawn.add_request("https://api.twitter.com/1/users/show.json", 
                         dict(params=dict(screen_name="steveWINton")),
                         callback)
twitterspawn.add_request("https://api.twitter.com/1/users/show.json", 
                         dict(params=dict(screen_name="twitter")),
                         callback)
twitterspawn.add_request("https://api.twitter.com/1/users/show.json", 
                         dict(params=dict(screen_name="catbinlady")),
                         callback)

# Add workers
twitterspawn.add_worker(access_token="YOUR_FIRST_ACCESS_TOKEN", 
                        access_token_secret="YOUR_FIRST_ACCESS_TOKEN_SECRET", 
                        consumer_key="YOUR_CONSUMER_KEY", 
                        consumer_secret="YOUR_CONSUMER_SECRET", 
                        header_auth=False)
twitterspawn.add_worker(access_token="YOUR_SECOND_ACCESS_TOKEN", 
                        access_token_secret="YOUR_SECOND_ACCESS_TOKEN_SECRET", 
                        consumer_key="YOUR_CONSUMER_KEY", 
                        consumer_secret="YOUR_CONSUMER_SECRET", 
                        header_auth=False)

# Go!
twitterspawn.go()
```

See also [example.py](https://github.com/swinton/twitterspawn/blob/develop/example.py) for a working example.

## Installation
Clone:

    $ git clone git://github.com/swinton/twitterspawn.git .

Install requirements:

    $ pip install -r requirements.txt

## Contact

@[steveWINton](https://twitter.com/steveWINton).