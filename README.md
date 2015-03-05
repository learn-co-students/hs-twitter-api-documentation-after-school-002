---
tags: kids, twitter, api, gems
languages: ruby
type: walk-through, documentation
---

##You want to use data from Twitter!?

Here's a walkthrough to get your app up and running with data from Twitter, using the [Twitter gem](https://github.com/sferik/twitter).


###Get Started
When you use the Twitter API in a web application, you are just using code to look up tweets for you. This process of getting Twitter's data through your own code mimics the same process of going to someone's page and looking at their tweets yourself.

Just like you as a person have to log into Twitter to read certain people's tweets or post tweets yourself, you application has to log in to Twitter. 

You must have a Twitter account in order to register an app. You can create an account [here](https://twitter.com/signup).**To get Twitter credentials for your application, go [[here](https://apps.twitter.com/)*** 
<img src="https://s3.amazonaws.com/after-school-assets/twitter-app-form.png">


###Access Tokens
Once you register your app through Twitter, there are some special authorization tokens that you'll need. In order to get all of those, click the link `manage keys and access tokens`.
<img src="https://s3.amazonaws.com/after-school-assets/twitter-access-keys.png">

At the top of the page you'll find the `Consumer Key` and `Consumer Secret`. You'll need those series of letters and numbers in your code.

<img src="https://s3.amazonaws.com/after-school-assets/twitter-access-keys.png">

Next, you need to create `Personal Access Tokens`, by clicking the `create my access token` link.
<img src="https://s3.amazonaws.com/after-school-assets/twitter-create-access-token.png">

Once the page reloads, you'll find your access token and access secret by scrolling down till you find:
<img src="https://s3.amazonaws.com/after-school-assets/twitter-access-tokens.png">

###Configuring code to get tweets

```ruby
  client = Twitter::REST::Client.new do |config|
    config.consumer_key        = "YOUR_CONSUMER_KEY"
    config.consumer_secret     = "YOUR_CONSUMER_SECRET"
    config.access_token        = "YOUR_ACCESS_TOKEN"
    config.access_token_secret = "YOUR_ACCESS_SECRET"
  end
```

You will want to copy and paste your `consumer_key`, `consumer_secret`, `access_token`, and `access_token_secret`.

In the above code, we're setting up a variable `client`This variable is storing a new instance of the `Client` class. This `client`, is our hook into Twitter.

###Getting all the tweets from a specific user


```ruby
  client.user_timeline("vicfriedman")
  client.user_timeline(213747670)
```

Above are two different examples of how to retrieve a specific user's tweets. The first example is based on the user's twitter handle. 

We call the `user_timeline` method, which is a method define in the Twitter gem. This method can accept an argument in two different forms: a twitter handle as a string or the user's unique id number as an integer. 




