# atq2 - The improved atq command

## Overview

atq2 allows you to view the scheduled commands in your 'at' queue (or atq). You can also filter by command, order by ID or timestamp and more.

I run a server that can have around 10,000 tasks scheduled using 'at'. The 'atq' command only displays the ID and the timestamp of the scheduled command which isn't as useful as it could be. In order to view the command associated with each ID you would need to then run 'at -c *ID*' but even then it will display a bunch of mostly irrelevant info. This tool allows me to quickly see the information that I need.

<br>
## Install

Stick the *atq2* file into your **/usr/local/bin** directory and make sure it's executable.

<br>
## Options

```bash
Usage: atq2 [-c <num>] [-i | -t] [-g=<string>] [-n <num>]

Flags:
                -c)    Display X number of characters of scheduled command
                -i)    Order output by Job ID
                -t)    Order output by timestamp
                -g)    Only display scheduled commands containing specified string
                -n)    Display X number of lines
```
<br>
## Example Usage

In this example, I order by timestamp, show the first 120 characters of the command and only display 5 rows.
```
$ atq2 -t -c 120 -n 5
11131	Sun Jan 22 11:11:00 2017	 /path/to/script.sh
11126	Sun Jan 22 11:26:00 2017	 /path/to/another/script.sh "param1" "param2" "10" "param4"
10293	Sun Jan 22 11:33:00 2017	 curl -s -X GET "https://www.googleapis.com/youtube/v3/videos?id=9GZJeplKV18&fields=items(id,snippet(title,publishedAt,de
10285	Sun Jan 22 11:40:00 2017	 curl -s -X GET "https://www.googleapis.com/youtube/v3/videos?id=oavMtUWDBTM&fields=items(id,snippet(title,publishedAt,de
11136	Sun Jan 22 12:00:00 2017	 echo "Blah"

```
<br>
## Another Example

In this example, I order by ID and only show the commands with the word 'youtube'
```
$ atq2 -i -g youtube
10285	Sun Jan 22 11:40:00 2017	 curl -s -X GET "https://www.googleapis.com/youtube/v3/videos?id=9GZJeplKV18&fields=items(id,snippet(title,publishedAt,de
10293	Sun Jan 22 11:33:00 2017	 curl -s -X GET "https://www.googleapis.com/youtube/v3/videos?id=oavMtUWDBTM&fields=items(id,snippet(title,publishedAt,de

```
<br>
##Other Information

This script has been tested as far and wide as my **Ubuntu 16.04** machine.
I also wrote this in a very short space of time so it's likely to be ridiculously buggy.
Please fork and contribute if you find any bugs.
