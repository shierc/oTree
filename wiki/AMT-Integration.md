---
layout: wiki
title: AMT Integration
wikiPageName: AMT-Integration
menu: wiki
---

## Overview
oTree provides integration with <strong><a href="https://www.mturk.com/mturk/welcome" target="_blank">Amazon Mechanical Turk (AMT)</a></strong>. oTree authenticates users visiting from the AMT service, and then sends payments to the correct AMT account. Researchers, however, must have an employer account with AMT, which currently requires a U.S. address and bank account.
## Session for AMT
Login to oTree admin panel and create new session:

![Create session](http://i.imgur.com/oXr33PU.png)

Set the session open and copy html snippet to your AMT HIT page:

![HTML snippet](http://i.imgur.com/gxoz3hh.png)

## AWS credentials
To make payments to participants you need to generate
`AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`
[here](https://console.aws.amazon.com/iam/home?#security_credential):

![AWS key](http://i.imgur.com/dNhkOiA.png)

On heroku add generated values to your environment variables:

    heroku config:set AWS_ACCESS_KEY_ID=YOUR_AWS_ACCESS_KEY_ID --app=YOUR_APP_NAME
    heroku config:set AWS_SECRET_ACCESS_KEY=YOUR_AWS_SECRET_ACCESS_KEY --app=YOUR_APP_NAME

## Payment

    heroku run "./otree mturk_pay SESSION_ID" --app=YOUR_APP_NAME
