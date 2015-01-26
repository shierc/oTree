---
layout: wiki
title: Rounds
wikiPageName: Rounds
menu: wiki
---

### Round numbers

Subsession objects have attributes `round_number`, which contains the current round number, starting from 1.

## Accessing data from previous rounds

Player objects have methods `in_previous_rounds()` and `in_all_rounds()` that returns a list of players representing the same participant in previous rounds of the same app. The difference is that `in_all_rounds()` includes the current round's player. For example, if you wanted to calculate a participant's payoff for all previous rounds of a game, plus the current one:

        cumulative_payoff = sum([p.payoff for p in self.player.in_all_rounds()])

Similarly, subsession objects have methods `previous_rounds()` and `all_rounds()` that work the same way.

## Accessing data from previous subsessions in different apps

The above method only works if the same app is repeated for multiple rounds. If you want to pass data between subsessions of different app types (e.g. the participant is in the questionnaire and needs to see data from their ultimatum game results), you should store this data in the participant object, which persists across subsessions. Each participant has a field called `vars`, which is a dictionary that can store any data about the player. For example, if you ask the participant's name in one subsession and you need to access it later, you would store it like this:

`self.player.participant.vars['first name'] = 'Chris'`

Then in a future subsession, you would retrieve this value like this:

`self.player.participant.vars['first name']` # returns 'Chris'

## Global variables

For session-wide globals, you can use `session.vars`,
either through `player.participant.session.vars` or `player.subsession.session.vars` (both are equivalent).

This is a dictionary just like `participant.vars`.

Also, you can pass a dictionary called `vars` to a `SessionType` in `sessions.py`. For example, you could use this
if you want 2 session types on the demo page that both play through the same app but have some parameter that is different
(e.g. each `SessionType` represents a different treatment group). You can access the `SessionType` from your app's code
with `subsession.session.session_type` or `player.participant.session.session_type`.
