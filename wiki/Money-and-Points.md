---
layout: wiki
title: Money and Points
wikiPageName: Money-and-Points
menu: wiki
---

In a typical lab experiment, participants are paid money at the end. Their payoffs may depend on how they played the games.

You can specify the payment currency in `settings.py`, by setting `PAYMENT_CURRENCY_CODE` to "USD", "EUR", "GBP", and so on. This means that all currency amounts the participants see will be automatically formatted in that currency, and at the end of the session when you print out the payments page, amounts will be displayed in that currency.

In oTree apps, currency values have their own data type. You can define a currency value with the `c()` function, e.g. `c(10)` or `c(0)`. Correspondingly, there is a special model field for currency values: `CurrencyField`. For example, each player has a `payoff` field, which is a `CurrencyField`. Currency values work just like numbers (you can do mathematical operations like addition, multiplication, etc), but when you pass them to an HTML template, they are automatically formatted as currency. For example, if you set `player.payoff = c(1.20)`, and then pass it to a template, it will be formatted as `$1.20` or `1,20 €`, etc., depending on your `PAYMENT_CURRENCY_CODE` and `LANGUAGE_CODE` settings.

Note: instead of using Python's built-in `range` function, you should use oTree's `currency_range` with currency values. For example, `currency_range(c(0), c(0.10), c(0.02))` returns something like:

```
[Money($0.00), Money($0.02), Money($0.04), Money($0.06), Money($0.08), Money($0.10)]
```

### Points
Sometimes it is preferable for players to play games not for real money but for points or "experimental currency units", which are converted to real money at the end of the session. You can set `USE_POINTS = True` in `settings.py`, and then in-game currency amounts will be expressed in points rather than real money.

For example, `c(10)` is displayed as `10 points`. You can specify the conversion rate to real money in `sessions.py` by providing a `money_per_point` argument to the `SessionType`. For example, if you pay the user 2 cents per point, you would set `money_per_point = 0.02`.

You can convert a point amount to money using the `to_money()` method,
which takes as an argument the current subsession
(this is necessary because subsessions in different apps can have different conversion rates).

Let's say `money_per_point = 0.02`

```
c(10) # evaluates to Currency(10 points)
c(10).to_money(self.subsession) # evaluates to $0.20
```
