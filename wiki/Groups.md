---
layout: wiki
title: Groups
wikiPageName: Groups
menu: wiki
---



### Grouping and randomization

For the first round, the players are randomly split into groups of `Constants.players_per_group`. In subsequent rounds, By default, the groups chosen are kept the same for subsequent round. If you would like to change this, you can define the grouping logic in `Subsession.initialize`.

A group has a method `set_players` that takes as an argument a list of the players to assign to that group, in order. For example, if you want players to be reassigned to the same groups but to have roles randomly shuffled around within their groups (e.g. so player 1 will either become player 2 or remain player 1), you would do this:

    def initialize(self):
        if self.round_number > 1:
            for group in self.get_groups():
                players = group.get_players()
                players.reverse()
                group.set_players(players)

The subsession has a method `set_groups` that takes as an argument a list of lists, with each sublist representing a group. You can use this if your groups have uneven size. For example, if you have a session with 7 participants and want to split into a group of 2 and another group of the remaining 7, you could set `players_per_group = None` and instead do this:

    def initialize(self):
        if self.round_number == 1:
            players = self.get_players()
            g1 = players[:2]
            g2 = players[2:]
            self.set_groups([g1, g2])

[TODO: oTree should implement the most common grouping algorithms like stranger, perfect stranger, etc.]
