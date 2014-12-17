---
layout: wiki
title: Running Lab Sessions
wikiPageName: Running-Lab-Sessions
menu: wiki
---

### Creating sessions

Create a session in the admin.
[TODO: more info]

### Opening links

To launch a session, each participant must open their link. There are 2 options for how to open URLs.

#### Lab

In the admin interface, go to the "global data" section, and copy the "lab link". This is a permanent URL that will last as long as you use the same server [TODO: finish]

Each workstation has a permanent URL that, when clicked, will route the participant to the currently active session.


choose an active session from the dropdown. Then, copy 


#### Unique URLs




If you are running your experiment in a lab, you should deploy the links to the target workstations using whatever means is available to you. If you have a tool that can push distinct URLs to each PC in the lab, you can use that. Or you can set up a unique email account for each workstation, and then send the unique links to PCs using a mail merge. Then open the link on each PC.

#### Player labels
oTree uses a unique code to identify each participant. However, you can assign each session participant a "label" that can be any convenient way to identify them to you, such as:

* Name
* Computer workstation number
* Email address
* ID number

This label will be displayed in places where participants are listed, like the oTree admin interface or the payments page.

You can assign each participant a label by adding a parameter to each start link.
For example, if you want to assign a participant the label "WORKSTATION_1", you would take the start link for that participant:

    http://[participant's unique link]?some_param=1

And change it to:

    http://[participant's unique link]?some_param=1&participant_label=WORKSTATION_1

Outside of oTree, you can create a script that adds a unique `participant_label` to each start link as indicated above. Then, when the link is opened, the oTree server will register that participant label for that participant.

### Monitor sessions
While your session is ongoing, you can monitor the live progress in the admin interface. The admin tables update live, highlighting changes as they occur. The most useful table to monitor is "Session participants", which gives you a summary of all the participants' progress. You can also click the "participants" table of each app to see the details of all the data being entered in your subsessions.
