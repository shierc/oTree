---
layout: wiki
title: Heroku
wikiPageName: Heroku
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

`heroku git:remote -a ancient-coast-2653

### Testing on Heroku

To recreate and push to Heroku, run this command:

```
git push myherokuapp master
./otree-heroku resetdb myherokuapp
```

Where `myherokuapp` is the name of your Heroku app `myherokuapp.herokuapp.com`

If it's a production website, you should set the environment variable `OTREE_PRODUCTION`, with:

`heroku config:set OTREE_PRODUCTION=1 --app myherokuapp`
