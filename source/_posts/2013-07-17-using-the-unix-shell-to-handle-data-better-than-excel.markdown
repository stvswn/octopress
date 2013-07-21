---
layout: post
title: "Fun with Data: the Unix utilities"
date: 2013-07-17 18:45
comments: true
categories: Data
---
Recently in my internship I needed to analyze thousands of results from our Apache Solr server.  Our app has buttons that allow users to see results from our database of events by category, and when a user selects a category a search query is executed.  I was trying to optimize those search queries to get the best results for the user.

The good news was that the Solr client would output results from search queries in .csv format.  The bad news was that all of the relevant data was in a single field, and in JSON format.  I just wanted a portion of all of that JSON data in a column by itself.  In the past I would have tried all kinds of Excel trickery to make it work, but luckily I had just seen <a href = 'http://www.gregreda.com/2013/07/15/unix-commands-for-data-science/'>this</a> link on Hacker News about using the Unix utilities.  

So, I wrote a two line shell script that was super simple:

```
curl -o results.csv $1
cat results.csv | cut -d, -f4 | cut -c12- | rev | cut -c3- | rev
```

The first line downloads the csv file from the URL I pass into it and puts it in a temporary csv file, the second line pulls the fourth column out of the csv file (which was JSON data) and then cleans it up by cutting out characters from the beginning and end of the field, which left me with just the event title that I was looking for.  It prints it to stdout (the terminal), so I can just copy and paste it into whatever spreadsheet I'm using.  I was able to handle 2000 rows in only a couple of seconds -- it would have been a nightmare in Excel.

I'm hoping to find a way to dive deeper into using the Unix utilities for data analysis - it's way more powerful than just this kind of stuff.  For someone like me that would normally battle with Excel by default, getting into some simple programming could be a huge timesaver.