---
layout: post
title: dynamodb keys
---

Spent some of the morning redoing DynamoDB tables after realizing a throughput of 2/2 up/down is actually too small for the visualization. After experimenting with combining tables, I get how flexible the schema really is - beyond sharing a relatively unique partition key/sort key combo, the documents can all be quite irregularly shaped. On the other hand, after building my key setup I had to redo it almost immediately after realizing that DynamoDB does not allow begins_with() on the hash key, only on the range key. 

Some of DynamoDB's error messages are a little peculiar, though. Ran into the "Aggregated size of all range keys has exceeded the size limit of 1024 bytes" error, only to realize Amazon specifically means just *one* key has exceeded 1024 bytes (a limitation that applies to range keys; the hash key can be larger). 

In the meantime, working with SEC Edgar XML files to build my next project. I've always wanted to see portfolio holdings from 13F filings in a organized format, something that the Bloomberg terminal, sadly, won't let you (at least on large funds - try running PORT <GO> on PIMCO's funds and see where that gets you).