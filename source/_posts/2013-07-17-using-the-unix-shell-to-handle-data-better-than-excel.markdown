---
layout: post
title: "Using the Unix Shell to handle data better than Excel"
date: 2013-07-17 18:45
comments: true
categories: 
---
Recently in my internship I needed to analyze hundreds of results from our Apache Solr server.  Our app has buttons that allow users to see results from our database of events by category, and when a user selects a category a search query is executed.  I was trying to optimize those search queries and get the best results possible.

The good news was that the Solr client would output results from search queries in .csv format.  The bad news was that all of the relevant data was in a single field, and in JSON.  I just wanted a portion of all of that JSON data in a column by itself.  In the past I would have tried all kinds of Excel trickery to make it work, but luckily I had just seen 