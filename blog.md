---
layout: page
title: Blog
permalink: /blog/
---

#### 2015-06-17: Skype "office hours"

If you have questions about oTree, I will be available to give help via Skype call on Tuesday June 23 at 4PM Zurich time (10AM New York time).
I will be online for 2 hours. You can ask any general questions, and we can use Skype/TeamViewer screen sharing to work through oTree installation or code writing.

You can add me on Skype by searching by my email (chris@otree.org).


#### 2015-06-11: New version available

There is a new version of otree-core with the following improvements/bugfixes:

* oTree localized to French, Spanish, and Russian (see [docs]({{ site.url_localization }}))
* Fixed bug with `group_by_arrival_time`
* Minor improvements and bugfixes

To upgrade, modify the `otree-core` version number in `requirements_base.txt` (the
latest version is
[here](https://github.com/oTree-org/oTree/blob/master/requirements_base.txt)),
then run:

```
pip install -r requirements_base.txt
```

Thanks to the users who reported the above issues,
and to those who contributed translations to different languages!


#### 2015-05-29: New version available

There is a new version of otree-core with the following improvements/bugfixes:

* Values in `session.vars` were sometimes not being saved
* Multi-field validation (`error_message`) was not properly displaying the error message to the user
* `get_players()` was sometimes returning players in the wrong order
* Better warning if database is not created
* Validate apps before publishing to MTurk
* Validation of min= and max= were not being done in Safari


#### 2015-05-11: Glossary: z-Tree to oTree

For those coming from a z-Tree background, we posted a "z-Tree to oTree" glossary [here]({{ site.url_ztree }}).

#### 2015-05-06: Tutorial posted

We created a [tutorial]({{ site.url_tutorial }}) showing how to create some simple games.