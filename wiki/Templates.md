---
layout: wiki
title: Templates
wikiPageName: Templates
menu: wiki
---

Your ``templates/`` directory will contain the templates for the HTML that gets displayed to the player.

oTree uses Django's [template system] (https://docs.djangoproject.com/en/dev/topics/templates/).

### Template blocks

Instead of having to write all your HTML from scratch, for example::

    <!DOCTYPE html>
    <html lang="en">
        <head>
        <!-- and so on... -->
    
You just have to define 2 blocks:
{% raw %}
    {% block title %}
        Title goes here
    {% endblock %}
    
    {% block content %}
        Body HTML goes here.

        {% formrow form.contribution with label="What is your contribution?" %}

        {% next_button %}
    {% endblock %}
{% endraw %}
You may want to define your own base template rather than using oTree's built-in base template.
This is useful when you want to customize the appearance or functionality (e.g. by adding custom CSS or JavaScript), or customize the structure of HTML headings. This is easily done. Just edit the file `templates/global/Base.html`.

### Static files

You will likely want to include images, CSS, or even JavaScript in your pages.

To do that, put the following line in your template below the ``extends`` block:
{% raw %}
    {% extends "Base.html" %}
    {% load staticfiles %}
{% endraw %}
And follow the [instructions here] (https://docs.djangoproject.com/en/dev/howto/static-files/).

## Additional tools

### Bootstrap

oTree comes with [Bootstrap] (http://getbootstrap.com/), a very popular library for customizing a website's user interface.

You can use it if you want a [custom style] (http://getbootstrap.com/css/), or a [specific component] (http://getbootstrap.com/components/) like a table, alert, progress bar, label, etc. You can even make your page dynamic with elements like [popovers] (http://getbootstrap.com/javascript/#popovers), [modals] (http://getbootstrap.com/javascript/#modals), and [collapsible text] (http://getbootstrap.com/javascript/#collapse).

Bootstrap is very easy to use and well documented. Usually you just need to add a ``class=`` attribute to your HTML element, and Bootstrap will take care of the rest.

For example, the following HTML will create a "Success" alert:

    <div class="alert alert-success">Great job!</div>

### HighCharts

oTree comes pre-loaded with [HighCharts](http://www.highcharts.com/demo). You can find examples in the library of how to use it.

To pass data like a list of values from Python to HighCharts, you can use the `otree.common.safe_json()` function. This converts to the correct JSON syntax and also uses "mark_safe" for the template.

Example:

    >>> a = [0, 1, 2, 3, 4, None]
    >>> safe_json(a)
    '[0, 1, 2, 3, 4, null]'


### jQuery

oTree comes pre-loaded with [jQuery](http://jquery.com/), a JavaScript library that lets you make your pages dynamic. Just include a script with the standard `$` variable.

### LaTeX


oTree comes pre-loaded with [KaTeX](http://khan.github.io/KaTeX/); you can insert LaTeX equations like this: `<span class="latex">1 + i = (1 + r)(1 + \pi)</span>`

##Smartphones and tablets
Since oTree uses Bootstrap for its user interface, your oTree app should work on all major browsers (Chrome/Internet Explorer/Firefox/Safari). When participants visit on a smartphone or tablet (e.g. iOS/Android/etc.), they should see an appropriately scaled down "mobile friendly" version of the site. This will generally not require any effort on your part since Bootstrap does it automatically, but if you plan to deploy your app to participants on mobile devices, you should test it out on a mobile device during development, since some HTML code doesn't look good on mobile devices.
