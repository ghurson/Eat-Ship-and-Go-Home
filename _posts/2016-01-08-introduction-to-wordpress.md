---
layout: post
title:  "Wordpress Introduction"
date:   2016-01-08 10:58:46 -0500
categories: wordpress
excerpt: "Wordpress is a big system. Here is where we're going to start."
---


Wordpress is an application masquerading as a framework. It's original intention was to create an online environment that people could customize. Think of a really big, fancy myspace account. It became very popular, and eventually was released as an open-source blogging platform. In the decade since that a community has grown around building up the Wordpress experience that draws from some of the best and brightest engineers all over the country. The result is a robust system that has greatly expanded on the core functions of the Wordpress blogging system. What that means for you as a developer is that there are many functions made available to you to help you access and parse your information. Many of these functions are simplifications of slightly more complex development functions. As you progress in your career, you will grow to understand their construction, but for now - just run with it.

The primary function of Wordpress that you don't see is the organization of the back end of the website. As a developer, it is important to think of a Wordpress installation in terms of the data structure in the admin section of the site. That is going to include your post types, your meta data, and your taxonomies. Sometimes the user accounts are going to be a part of the installation, but most often they are not. Smart backend architecture will enable you to build a content-rich website that finds use long after it's paid for. What separates a good developer from a great developer is just that - the ability to build a system that withstands the test of time to deliver a product worth reusing. 

That is where you come in. What has been sold to the client is a few pictures of a website and a whole lot of promises. It is up to you to find the relationships between the content you have been provided, the content that you find in the design you are given, and the content on the client's contract with us. You are encouraged to ask many questions about this. 

## Templating

Wordpress uses templates to display their sites. It's sort of like a view layer, but it completely isn't. That's like half the reason seasoned devs don't like working with Wordpress. Soon, you won't like it for the same reason. For now, you're going to use it to learn how to put together complex coding environments.

The way wordpress templates work at the top level is what's known as the *template heirarchy system*. This is a set of rules that determine what php file is going to be requested from your theme folder to display, when given a URL request. It, like most webservers, will start by looking for an index.php file to serve in response to this request. However, there are many instances where it would look for a different file first.

When a browser sends a request to a Wordpress installation, the WP installation scans the url, checking it against known post types, taxonomies and other keywords and, based on those parameters, will choose a template to display. This set of rules is based on the template heirarchy. Study it, know it.

### Pages

The content and structure of a Wordpress site is set by the information in the database. When a user creates a page in a Wordpress installation, they are creating a "post object" in the database. When that page is requested by a user through a URL request, what they are seeing is a template file that is loaded based on the *rules of the template* with the appropriate variables in place.

### Arrays

In order to build out Wordpress templates, one must be comfortable with the concept of an array.


{% highlight php %}

<?php

$array = array(1, 2, 3, 4);

foreach($array as $item):
    
    print $item;
    
endforeach;

?>

{% endhighlight %}

This block would print out "1234" in your html document. [link to docs here]

### The Wordpress Development Tango

There are three primary steps to building out sites in Wordpress. 

- Get the content in the database 
- Get the content out of the database 
- Display the content in your template
 
Accomplishing these tasks requires a little planning for the non-blog site. In a development sense, the steps involved here are

- Create a place to house data
- Configure your metadata (using Advanced Custom Fields)
- Input your data
- Locate / Create the template that you're going to use to display the information
- Query the database
- Sync up your data with an HTML structure.

For instance, a static html block may look as such:

{% highlight html %}

<div class='person_excerpt'>
    <h2>John Doe</h2>
    <p>
        Email: <a href='mailto: jdoe@email.com'>jdoe@email.com <br />
        Phone: <a href='tel: 555-555-4242'>555-555-4242</a>
    </p>
    
    <p><a href='#'>Learn More</a></p>
    
</div>

{% endhighlight %}

Now, lets say that the above segment is an entry in a directory that has been created for use on a website. We're not sure how many people are going to be listed in this directory - but we know there are going to be many. We also know that each of these people is going to have their own page on the site. So, we need to create a data environment where a client can create pages for the people that are going to be listed on the site. In order to accomplish this, we're going to need to define a custom post type. This is the "place to house the data" from the above steplist (not all custom data requirements will need a custom post type). 

By default, any post object in wordpress is going to have the same data fields. This will include a title, content, excerpt, featured image, taxonomy information, author and url information (aka the permalink). There are a few others, but we're going to focus on these for now. Right away, we can see an issue here - how are we supposed to define an email address and a phone number? Enter the "Custom Field". We use a plugin called Advanced Custom Fields to configure a post's metadata. It is very well documented, I cannot recommend reading the docs enough.

By configuring the custom fields on your post type, you can add fields for the client to enter a phone number and an email address directly into the post data.






## Logic

### Wordpress Automagication

Wordpress is an application. It does many things for you as a developer. By the time your template is loaded, the application dials into a database, pulls out a specific slice of information, formats it and serves it to the developer. Wordpress is an application that is indended for people who are unfamilar with modern MVC development environments. The modern term for this would be something like an "opinionated framework". So, when wordpress displays a given template from the heirarchy after scanning the URL's keywords - there are a host of variables that have been set by the Wordpress system.

These are the global variables, and they are set based on which template has been loaded from the heirarchy (based on the URL). In terms of development, it is very useful to note that the global variables are set by the url that the browser requests.

### The Loop

You can't talk about wordpress installations without talking about the loop. It sort of encapsulates the entire issue between WP and modern development environments. When wordpress scans the URL of the browser request and directs to a file in the theme directory - it also creates a query.

In Wordpress parlance, "the query" is a PHP object created on page load. It has a whole bunch of stuff in it, but the really important parts are the query's post, and the associated objects and arguements. One of the strongest reasons to make use of the template heirarchy in Wordpress is that it customizes these queries based purely on the template used. So, if you create a file named archive-car.php, and then pulled up a wordpress installation that had a post type called "car", and that post type was configured to have archives, when you requested a url that fit into the "show the archive for the car's post type" - you're going to find that your query variable is put together with your posts and your helper functions in place. Replicating those queries is a very time intensive process and is strongly discouraged.

## Structure

### Classes

PHP Classes are collections of functions, all grouped together so that they can work together. 

{% highlight php %}

<?php

namespace TSD

class Display {

    static function say_hi_to_admin(){
        if(!is_user_logged_in()):
            return false;
        endif;
        
        print 'hi admin';
    }

}

?>

{% endhighlight %}