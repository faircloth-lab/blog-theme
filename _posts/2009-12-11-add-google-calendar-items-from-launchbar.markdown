---
title: add google calendar items from launchbar
layout: post
author: brant
categories:
    - random
---

I came across a post on Launchbar's [forum][1], discussing a means of [adding entries to your Google Calendar via Launchbar][2]. I've made a small simplification to the script that runs the terminal command in the background (with less error checking, of course). Follow the instructions up to the script presented in the forum post (install [GData][3] and [python-dateutil][4], [download][5] and place the gcalcli script somewhere) and copy the following into AppleScript Editor:   
  
<script src="http://gist.github.com/254567.js?file=gcal.scpt"></script>   
  
Then edit the first line to point to the gcalcli binary and save the script to ~/Library/Application Support/LaunchBar/Actions/.

I may eventually add some other modifications, although Applescript is not my bag.

**Update**:  Google Calendar [Quick Add Grammar][6]

 [1]: http://forums.obdev.at/viewforum.php?f=24
 [2]: http://forums.obdev.at/viewtopic.php?f=24&t=1591
 [3]: http://code.google.com/p/gdata-python-client/
 [4]: http://www.labix.org/python-dateutil
 [5]: http://code.google.com/p/gcalcli/downloads/list
 [6]: http://www.google.com/support/calendar/bin/answer.py?hl=en&answer=36604#text

