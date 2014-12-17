---
layout: wiki
title: For Django Devs
wikiPageName: For-Django-Devs
menu: wiki
---

## Guidelines for developers contributing to oTree's library of games

### Keep it simple
The purpose of the oTree sample games library is to show examples so that new users can understand how to do things in oTree. They will then copy-paste these code snippets when they create their own apps. So, we want a consistent coding style in the oTree library, especially because many users will be novice Python programmers. In general we should avoid complex code and algorithms. We should also try to avoid code that relies on less commonly used Python/Django features or "tricks"/hacks. Even if it works nicely in a particular context, these risk causing confusion when someone copies them without really understanding.

Examples of code that could confuse a newcomer:
* Using `a[::-1]` to reverse a list (not obvious what this is doing, and hard to Google
* Decorators like `@property` or `@staticmethod`
* Using class inheritance within your app (e.g. subclassing one view from another, other than subclassing oTree's built-in views)
* Use lists instead of tuples, because when a tuple only has 1 element you have to remember the (comma,)

### Consistency
* Don't delete unused imports in the <standard imports> section; a user should always be able to rely on those being there.

### Don't repeat yourself
* If a certain page is being repeated in multiple apps, it may be better suited as a separate app that gets added to `subsession_apps` for each session in `sessions.py`. Examples: surveys and feedback pages.
* You should obey to Django's "Don't repeat yourself" principle: "Every distinct concept and/or piece of data should live in one, and only one, place. Redundancy is bad."
 * Numeric constants, even simple ones like 0.5 or 3, should go in the `Constants` class

### Separate logic from presentation
* User-facing strings should be defined in the template wherever possible. This is to keep a separation between logic and UI, which makes it easier for a non-programmer to modify a string, since they only have to look at the HTML. Also, in the template, strings are displayed in context, whereas if they are defined in Python code, they are usually out of context.
* Try not to put much logic in templates. It makes it hard for a non-programmer to understand and edit the template, and anyways logic in templates is often more verbose and harder to debug.

## Intro to oTree for Django developers

### Differences between oTree and Django

#### Models
* Field labels should go in the template formrow, rather than the model field's `verbose_name`.
* `null=True` and `default=None` are not necessary in your model field declarations; in oTree fields are null by default.
* On `CharField`s, `max_length` is not required.

