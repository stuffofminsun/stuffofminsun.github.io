---
layout: post
title: dynamodb and heroku setup
---

Managed to currently hook the first set of charts from <a href="https://minsun-agencytrading.herokuapp.com/">my visualization</a> to pull from AWS' DynamoDB instead of from a stored csv file. Spent most of the day cleaning up code to be a little more future proof (some of the visuals hard code the mortgage coupons instead of just looking at the table headers, something not a particularly good idea when the Fed keeps moving rates up 25 bps at a time), cleaning up some of the visuals (now every agency has their own specific color!), running the code against a full year and a half of data, and setting up Heroku to pull data from DynamoDB. The remaining few charts haven't been migrated to DynamoDB yet since I've been busy writing the data to the database verrrryyyy slowly... I set the write and read capacity down to 2 for each table, much to my horror and regret, and am too lazy to stop it since it'll finish overnight anyway. Once that works, plan on working through AWS Data Pipeline and get the web scraping part of all this all automated.

Since I'm very new to nosql databases, I read through the docs to note that the general advice, at least from DynamoDB, is that you should try to stick to using *one* table, or very few tables. I didn't follow this at all for the viz since this seemed ultra confusing to execute (I used five tables/collections/whatever you call them), but once I get more comfortable with this, I might try it out. Possibly sign up for the MongoDB education series since they sort of seem to be within the same nosql family.

Getting DynamoDB to work with Heroku is, oddly enough, not that obvious. I found the info split up across a lot of different websites and docs. The long and short of it is, which I'm writing for others as well as for myself so I don't have to google all day on this again:

## Accessing DynamoDB from python: 

There are two main ways to access DynamoDB tables in python, either through Client or Resource. Probably if you've been messing with it like I have and followed <a href="https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStarted.Python.html">Amazon's getting started guide</a>a>, you've been using boto3.resource() instead. <a href="
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html#client">boto3.client()</a>a> does something similar to resource, but queries are structured ever so slightly differently, as are results. Different enough that it'd be a hassle to rewrite code you've already started, anyway.

In any case, if you use client to manipulate the DynamoDB database, you can pass the credentials directly:

```
import boto3

client = boto3.client(
	'dynamodb', 
	aws_access_key_id=ACCESS_KEY, 
	aws_secret_access_key=SECRET_KEY,
	aws_session_token=SESSION_TOKEN,
	region_name='YOUR_REGION',
)
```

This is not super obvious until your Heroku app fails and you dig through your logs, but you *must* set a region as well. Session token's optional, though.

If you use Resource instead, you pass your credentials first through a session, since you can't pass credentials directly through a resource:
```
import boto3

session = boto3.session(
	'dynamodb', 
	aws_access_key_id=ACCESS_KEY, 
	aws_secret_access_key=SECRET_KEY,
	aws_session_token=SESSION_TOKEN,
	region_name='YOUR REGION',
)

dynamodb = session.resource('dynamodb')
```

Yet again, region must be specified, and session token is optional. 

## Setting up AWS credentials with Heroku

You can be very lazy and just pass your keys into your program intact but that's probably a terrible idea. You could set up your keys as a Heroku environment variable instead, either setting them through their <a href="https://devcenter.heroku.com/articles/config-vars">CLI or just popping them in the dashboard under an app's settings</a>. You can check your variables in settings on the dashboard or typing in this on the command line to check that they're there: 

```
heroku config --app YOUR_APP_NAME
```

You'll see something like this: 
```
=== YOUR_APP_NAME Config Vars
AWS_ACCESS_KEY_ID:     ACCESS_KEY_STRING
AWS_SECRET_ACCESS_KEY: AWS_SECRET_ACCESS_KEY_STRING
```

Writing the above made me realize I didn't install the Heroku CLI on my home computer, so I'll pause here to go and install that.

Then you can follow what Heroku says about setting the config variables in python (see above link about environment variables) or just ignore it since you don't strictly need to import an S3Connection at all for this and instead just pass your environment variables through your Session or Client like so: 

```
import boto3
import os

session = boto3.session(
	'dynamodb', 
	aws_access_key_id=os.environ['ACCESS_KEY'], 
	aws_secret_access_key=os.environ['SECRET_KEY'],
	region_name='YOUR REGION',
)

dynamodb = session.resource('dynamodb')

# rest of your table code
```
And there you have it, a heroku app that works with DynamoDB. Just make sure you set up your local environment similarly if you're going to test locally and all that jazz.