---
layout: wiki
title: Online Experiments
wikiPageName: Online-Experiments
menu: wiki
---

Experiments can be launched to participants playing over the internet, in a similar way to how experiments are launched the lab. Login to the admin, create a session, then distribute the links to participants via email or a website.

In a lab, you usually can start all participants at the same time, but this is often not possible online, because some participants might click your link hours after other participants. If your game requires players to play in groups, you may want to set the `group_by_arrival_time` argument on the `SessionType` to `True`. This will group players in the order in which they arrive to your site, rather than randomly, so that players who arrive around the same time play with each other.
