---
title: mysql date and time strings to datetime values
layout: post
author: brant
categories:
    - databases
---

Getting dates and times into MySQL can be a total pain.  Sometimes, it's easier
to just import the date values into a varchar column and do the same with time
values - and **then** convert them to a datetime type (which is far more handy)
than a date and a time column (since you can derive both from a datetime
column).

So, in my case, I have this setup:

{% highlight sql %}

mysql> select usdi, capture_date, time from all_bands_temp 
    -> order by RAND() limit 10;
+-----------+--------------+------+
| usdi      | capture_date | time |
+-----------+--------------+------+
| 154187574 | 5/7/98       | 1312 | 
| 139107796 | 5/14/90      | 0820 | 
| 136141001 | 5/2/85       | 1209 | 
| 187140505 | 5/31/05      | 0750 | 
| 190134590 | 5/9/06       | 0000 | 
| 190134700 | 7/10/06      | 0000 | 
| 139105075 | 4/28/88      | 1135 | 
| 139107358 | 8/11/89      | 1017 | 
| 190134254 | 4/29/04      | 0000 | 
| 154189988 | 5/20/03      | 1322 | 
+-----------+--------------+------+
10 rows in set (0.12 sec)

{% endhighlight %}

To convert these into a datetime value, all i need to do is:

{% highlight sql %}

mysql> select usdi, capture_date, time,
    -> str_to_date(concat(capture_date, ' ', time), '%m/%d/%y %k%i') 
    -> as str_to_datetime
    -> from all_bands_temp order by RAND() limit 10;
+-----------+--------------+------+---------------------+
| usdi      | capture_date | time | str_to_datetime     |
+-----------+--------------+------+---------------------+
| 139106995 | 6/12/91      | 0707 | 1991-06-12 07:07:00 | 
| 149143944 | 6/2/95       | 1212 | 1995-06-02 12:12:00 | 
| 139107786 | 5/12/90      | 1730 | 1990-05-12 17:30:00 | 
| 147164369 | 5/24/91      | 1030 | 1991-05-24 10:30:00 | 
| 149143925 | 5/28/95      | 1140 | 1995-05-28 11:40:00 | 
| 154189201 | 5/5/02       | 1338 | 2002-05-05 13:38:00 | 
| 123156987 | NULL         | NULL | NULL                | 
| 190134380 | 6/11/04      | 0000 | 2004-06-11 00:00:00 | 
| 139109340 | 7/10/87      | 0830 | 1987-07-10 08:30:00 | 
| 154189917 | 5/3/03       | 1332 | 2003-05-03 13:32:00 | 
+-----------+--------------+------+---------------------+

{% endhighlight %}

Now that we know that, all we need to do is insert these values into a datetime
column...