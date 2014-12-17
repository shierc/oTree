---
layout: wiki
title: Deploying on Heroku
wikiPageName: Deploying-on-Heroku
menu: wiki
---

TODO: add content about

* add-ons (Sentry, PG backups)

### To create new remote:
```
heroku login  # if not yet
heroku create
git push heroku master
```

### To add an existing remote:

`heroku git:remote -a ancient-coast-2653 -r ancient-coast-2653`

### Testing on Heroku

To recreate and push to Heroku, run this command:

```
git push myherokuapp master
./otree-heroku resetdb myherokuapp
```

Where `myherokuapp` is the name of your Heroku app. Note: You should first set the name of your Heroku git remote so that it matches the name of the Heroku app, e.g.:

e.g., "myherokuapp.herokuapp.com" and "git push myherokuapp master"

If your git remote is currently named `heroku` and you want to change it to `myherokuapp`, you would do this:

`git remote rename heroku myherokuapp`
