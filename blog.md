---
layout: page
title: Blog
permalink: /blog/
---

#### 2015-05-29: New version available

There is a new version of otree-core with the following improvements/bugfixes:

* Values in `session.vars` were sometimes not being saved
* Multi-field validation (`error_message`) was not properly displaying the error message to the user
* `get_players()` was sometimes returning players in the wrong order
* Better warning if database is not created
* Validate apps before publishing to MTurk

To upgrade, modify the ``otree-core`` version number in ``requirements_base.txt`` (the
latest version is
`here <https://github.com/oTree-org/oTree/blob/master/requirements_base.txt>`__),
then run:

```
pip install -r requirements_base.txt
```

Thanks to the users who reported the above issues and made suggestions!

#### 2015-05-11: Glossary: z-Tree to oTree

For those coming from a z-Tree background, we posted a "z-Tree to oTree" glossary [here]({{ site.url_ztree }}).

#### 2015-05-06: Tutorial posted

We created a [tutorial]({{ site.url_tutorial }}) showing how to create some simple games.