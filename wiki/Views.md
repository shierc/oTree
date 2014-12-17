---
layout: wiki
title: Views
wikiPageName: Views
menu: wiki
---

Each page that your players see is defined by a `Page` class in `views.py`. (You can think of "views" as a synonym for "pages".)

For example, if your experiment involves showing the player a sequence of 5 pages, your `views.py` should contain 5 page classes.

At the bottom of your `views.py`, you must have a `pages()` function that specifies the order in which players are routed through your pages. For example:

    def pages():
        return [Start, Offer, Accept, Results]

This function should list all pages that anybody will see. You can filter individual pages from being seen.

The player must submit a valid form before they get routed to the next page. If the form they submit is invalid (e.g. missing or incorrect values), it will be re-displayed to them along with the list of errors they need to correct.

Here is what the code of a page should define (along with what attribute/method defines it):

## Page

### `player, group, subsession`
These attributes are provided automatically. For example, inside a method definition, you can access the current player with `self.player`, just as you can in `models.py` or `forms.py`.

### `template_name`

The name of the HTML template to display.

Example:

    # This will look inside your app under the 'templates' directory, 
    # to '/app_name/MyView.html'
    template_name = 'app_name/MyView.html'
    
### `form_models`

The model that this form modifies. It will most commonly be `models.Player` or `models.Group`.

### `form_fields`

A list of the field names from the model specified in `form_model` to include in the form.

### `timeout_seconds`

Set to an integer that specifies how many seconds the user has to complete the page. After the time runs out, the page
  auto-submits.

Example: `timeout_seconds = 20`

### `auto_submit_values`

Lets you specify what values should be auto-submitted if `timeout_seconds` is exceeded, or if the experimenter
moves the participant forward. If this is omitted, then oTree will default to `0` for numeric fields, `False` for boolean
fields, and the empty string for text/character fields.

This should be a dictionary where the keys are the elements of `form_fields`, and the values are the values that should
be auto-submitted.


### `def variables_for_template(self)`

Get any variables that will be passed to the HTML template. Add them to the dictionary as key-value pairs.

Example:

    def variables_for_template(self):
        return {'max_amount_offered': self.subsession.max_amount_offered,
                'reject_payoff': Constants.payoff_if_rejected}

Note that this method will be re-executed each time the player refreshes the page reloads the page (or submits an invalid form, which triggers a page reload). Make sure this doesn't cause undesired behavior. For example, if your code generates a payoff for the player based on a random number generator, the player could exploit this by refreshing the page until they get the payoff they want. To prevent issues like this, you can check if this variable has already been set, like this:

    if self.player.payoff is None:
        self.player.payoff = randint(0,100)

### `def participate_condition(self)`

Should return True if the page should be shown, and False if the page should be skipped. Default behavior is to show the page.

For example, if you only want a page to be shown to P2 in each group:

    def participate_condition(self):
        return self.player.id_in_group == 2
    
### `def after_next_button(self)`

After the player clicks the "Next" button, oTree makes sure that any form fields validate (and re-displays to the player with errors otherwise).

Here you can put anything additional that should happen after form validation. If you don't need anything to be done, it's OK to leave this method blank, or to leave it out entirely.

## `def variables_for_all_templates(self)`

This function is useful when you need certain variables to be passed to multiple pages in your app.
Instead of repeating the same values in each `variables_for_template`, you can define it in this function at the top of your views.py.

<!---
### time_limit_in_seconds()

Your page can have a time limit, in which case the player will see a countdown timer on the page.
This method lets you define what that time limit is.
If the user exceeds the time limit, they can still submit the form, but once they submit,
the `time_limit_was_exceeded` attribute will be set to `True`, which you can use to do anything you want.
--->

## Wait pages

Wait pages are created by subclassing from `WaitPage`.

If you have a wait page in your sequence of pages, then oTree waits until all players in the group have arrived at that point in the sequence, and then all players are allowed to proceed.

If your subsession has multiple groups playing simultaneously, and you would like a wait page that waits for all groups (i.e. all players in the subsession), you can set the attribute `wait_for_all_groups = True` on the wait page.

Wait pages can define the following methods:

### `def after_all_players_arrive(self)`

This code will be executed once all players have arrived at the wait page. For example, this method can determine the winner of an auction and set each player's payoff.

### `def title_text(self)`

The text in the title of the wait page.

### `def body_text(self)`

The text in the body of the wait page.

## Currency formatting
You can use the convert integer or float numbers to currency. For example, `c(5.10)` returns `"$5.10"`. oTree defaults to USD, but you can set to any currency code by specifying `PAYMENT_CURRENCY_CODE` in your project's `settings.py`. For example, you can set it to "EUR", "GBP", and so on.

### Points
If you set `USE_POINTS = True` in `settings.py`, then in-game currency amounts will be expressed in points rather than real money.
For example, `c(10)` is displayed as `10 points`.
You can specify the conversion rate to real money in `sessions.py` by providing a `money_per_point` argument to the `SessionType`.
For example, if you pay the user 2 cents per point, you would set `money_per_point = 0.02`.

You can convert a point amount to money using the `to_money()` method,
which takes as an argument the current subsession
(this is necessary because subsessions in different apps can have different conversion rates).

Let's say `money_per_point = 0.02`

```
c(10) # evaluates to Currency(10 points)
c(10).to_money(self.subsession) # evaluates to $0.20
```

