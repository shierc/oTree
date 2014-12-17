---
layout: wiki
title: Rounds
wikiPageName: Rounds
menu: wiki
---

### Round numbers

Subsession objects have attributes `round_number`, which contains the current round number, starting from 1.

### Grouping and randomization

For the first round, the players are randomly grouped with one another. By default, the groups chosen are kept the same for subsequent round. If you would like to change this, you can define either of the following methods in `models.py` on the `Subsession` model:

#### `def first_round_groups(self)`

[todo]

#### `def next_round_groups(self, current_round_group_matrix)`

This method defines how players should be grouped into groups with one another, e.g. partner grouping, stranger grouping, perfect stranger, etc.

The argument `current_round_group_matrix` is a matrix (list of lists) that represents how groups are assigned in the current round. In this matrix, each row defines the players in a group. For example, if you have a game with 2 players per group, and 6 players total (meaning 3 groups), this matrix would look something like:

`[[<P5>,<P4>], [<P2>,<P3>], [<P6>,<P1>] ]`

Looking at the first sub-list above, this means players 5 and 4 play together this round, and their `id_in_group` attributes would be 1 and 2, respectively. (So player 5's `id_in_group` would be 1.)

To change the group assignments for the next round, you should define an algorithm to permute `current_round_group_matrix` and return the permuted matrix. For example, if you want players to be reassigned to the same groups, you should just return the input argument as is, i.e.:

    def next_round_groups(self, current_round_group_matrix):
        return current_round_group_matrix

If you want players to be reassigned to the same groups but to have roles randomly shuffled around within their groups (e.g. so player 1 will either become player 2 or remain player 1), you would do this:

    def next_round_groups(self, current_round_group_matrix):
        group_matrix = current_round_group_matrix
        for group_list in group_matrix:
            random.shuffle(group_list)
        return group_matrix

[TODO: oTree should implement the most common grouping algorithms like stranger, perfect stranger, etc.]

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
