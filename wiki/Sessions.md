---
layout: wiki
title: Sessions
wikiPageName: Sessions
menu: wiki
---

In oTree, the term "session" refers to an event where a group of people spend time taking part in oTree experiments.

An example of a session would be: 

> On Tuesday at 3PM, 30 people will come to the lab for 1 hour, during which time they will play a trust game, followed by 2 ultimatum games, followed by a questionnaire. Participants get paid EUR 10.00 for showing up, plus bonus amounts for participating.

A session can be broken down into what oTree calls "subsessions". These are interchangeable units or modules that come one after another. Each subsession has a sequence of one or more pages the player must interact with. The session in the above example had 4 subsessions:

* Trust game
* Ultimatum game 1
* Ultimatum game 2
* Questionnaire

Each subsession is created by an oTree app. The above session would require 3 distinct apps to be coded:

* Trust game
* Ultimatum game
* Questionnaire

You can define your session's properties in `sessions.py`. Here are the parameters for the above example:

    SessionType(
        name='my_session',
        fixed_pay=1000,
        app_sequence=['trust', 'ultimatum', 'questionnaire'],
    )        

## Players vs. participants

The terms "player" and "participant" mean similar things but are slightly different.

A participant is a person who takes part in a session. The participant object contains properties such as the participant's name, how much they made in the session, and what their progress is in the session.

A player is an instance of a participant in one particular subsession. A participant can be player 1 in the first subsession, player 5 in the next subsession, and so on.

Each player has an attribute called participant that refers to the participant. In the above example, here is how this participant would be modeled in oTree:

* participant
    * label: "John Smith"
    * time_started: "3 PM"
    * players:
        * player in trust subsession
            * bonus: $0.50
        * player in ultimatum subsession 1
            * bonus: $0.65
        * player in ultimatum subsession 2
            * bonus: $0.80
        * player in questionnaire subsession
            * bonus: $0.00
    * total bonuses for participant: ($0.50 + $0.65 + $0.80 + $0.00) = $1.95
