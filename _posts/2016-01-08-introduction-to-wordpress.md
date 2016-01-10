# Wordpress

Wordpress is an application masquerading as a framework. It's original intention was to create an online environment that people could customize. Think of a really big, fancy myspace account. It became very popular, and eventually was released as an open-source blogging platform. In the decade since that a community has grown around building up the Wordpress experience that draws from some of the best and brightest engineers all over the country. The result is a robust system that has greatly expanded on the core functions of the Wordpress blogging system.

## Templating

Wordpress uses templates to display their sites. It's sort of like a view layer, but it completely isn't. That's like half the reason seasoned devs don't like working with Wordpress. Soon, you won't like it for the same reason. For now, you're going to use it to learn how to put together complex coding environments.

The way wordpress templates work at the top level is what's known as the template heirarchy system. This is a set of rules that determine what php file is going to be requested from your theme folder to display, when given a URL request. It, like most webservers, will start by looking for an index.php file to serve in response to this request. However, there are many instances where it would look for a different file first.

When a browser sends a request to a Wordpress installation, the WP installation scans the url, checking it against known post types, taxonomies and other keywords and, based on those parameters, will choose a template to display. This set of rules is based on the template heirarchy. Study it, know it.

## Logic

### Wordpress Automagication

Wordpress is an application. It does many things for you as a developer. By the time your template is loaded, the application dials into a database, pulls out a specific slice of information, formats it and serves it to the user. Wordpress is an application that is indended for people who are unfamilar with modern MVC development environments. The modern term for this would be something like an "opinionated framework". So, when wordpress displays a given template from the heirarchy after scanning the URL's keywords - there are a host of variables that have been set by the Wordpress system.

These are the global variables, and they are set based on which template has been loaded from the heirarchy (based on the URL). In terms of development, it is very useful to note that the global variables are set by the url that the browser requests.

### The Loop

You can't talk about wordpress installations without talking about the loop. It sort of encapsulates the entire issue between WP and modern development environments. When wordpress scans the URL of the browser request and directs to a file in the theme directory - it also creates a query.

## Structure

### Classes