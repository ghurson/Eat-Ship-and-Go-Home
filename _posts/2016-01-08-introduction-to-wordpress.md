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

## PHP

PHP is a language that is designed to work with html on apache servers. The way that we utilize it is to communicate with a server, allowing us to retrieve and manipulate information that is stored in a database. As a jr. front-end developer, your initial interactions with PHP will be limited to making requests through helper functions. As you develop experience working through the patterns of development, you will use PHP to customize your build process, refining your structures and building elegant code.

In a document, PHP lives alongside HTML. In the order of rendering a page, the PHP is calculated first, as a server-side operation. The browser goes from top to bottom of the document, and follows any instructions laid out for it. Essentially, PHP as you use it is going to be something to populate content inside templates. You will declare variables equal to the values of database queries, arrays of information, strings, numbers, values of true and false and more. From there, you create conditional statements to determine the circumstances in which your functions execute.


In Wordpress, you're going to be working with arrays and objects pretty much right off the bat. Arrays are going to be used in places where we are looping through sets of data, and objects are going to be used when we're working with individual sets of complex data.

### Variables

One of the primary tools used in PHP to build complex environments is the variable. 


{% highlight php %}

<?php

$variable = 'test value';

print $variable;

// outputs the string test value. the quotations aren't included.

?>

{% endhighlight %}


There are 9 (I think) types of variables. You're going to use 5 in 99% of your job.

Strings: A series of text characters. PHP will keep track of its length, and has tools to search and rearrange strings.

Boolean: Values of true or false. There is no content stored here, just an on or off value. These are used in logical scenarios, making sure that the data displayed on the page is the data you wanted.

Integers: These are numbers. PHP has a lot of tricks for math. Probably more than you will ever need, but who knows? Mostly what we do is equivalent to math you could do with a simple calculator. It's easy to trip yourself up working with numbers if they aren't actually integers. It's possible to have the number 2 as a variable, but to have the variable be a string. Adding 2 (string) and 3 (number) will result in 23, not five. 1 plus 1 doesn't always equal 2 in programming.

Arrays: Groups of variables. I'm going to go into greater depth about this below.

Objects: Collections of variables. Yes, there is a difference. See below.


{% highlight php %}

<?php

// bolean
$is_user_awesome = true;

// integer
$user_points = 3;

// string
$user_name = "You";

if($is_user_awesome){

  // Due to the awesome nature of the user,
  // a point is awarded. The user is then
  // notified of the good news via a printed
  // message.
  
  $total_points = $user_points + 1;
  
  print "Good for " . $user_name;
  print "A point has been awarded to your house.";
  
} else {

  // In this scenario, the user is not awesome.
  // Their points are removed, and they are
  // consoled.
  
  $total_points = 0;
  print "Bummer. Try not to look at the scoreboard.";
}

// What we have here is a simple logic structure
// that judges a person based on something arbitrarily
// made up and then either rewards them, or robs
// them entirely.
 
// Lets say we wanted to let a whole group of people
// know what we thought about them.

$bystanders = array('Chris', 'Nick', 'Colm');

// We have created an array out of three strings.
// PHP has tools that will allow us to cycle through
// this array and do things to each entry specifically.
// This is called a for each loop. You're going to do
// this a lot. For each item in the loop, you give the
// given slot in the array a variable name so you can
// access its content with the as command.

foreach($bystander as $person):
  print "Hey, " . $person . "! I think you're alright!";
endforeach;

// Gratifying.

// Now that we know we can group variables together and
// loop through them, wouldn't it be neat to be able to
// build a mechanism by which we could cast judgement
// on an entire array of people?

// But we hit an issue! An array can only cycle through
// one entry at a time, but if we're going to judge people,
// we need to know more than just their name, right? So,
// we need to group the variables together in a way that
// we can access them as we loop through our array.

// Hence the object. The collection of variables.

$nick = new Person(
  'name' => 'Nick',
  'is_cool' => true,
  'points' => 2
);

$chris = new Person(
  'name' => 'Chris',
  'is_cool' => false,
  'points' => 5
);

$colm = new Person(
  'name' => 'Colm',
  'is_cool' => true,
  'points' => 3
);

$bystanders = new array($nick, $chris, $colm);

foreach($bystanders as $person):

  if($person->is_cool):
    print "Hey, " . $person->name . "! I think you're alright!";
    
    // we're going to give them a point here, you
    // know the drill. putting ++ or -- at the end
    // of an integer will increase or decrease that
    // integer by 1
    $person->points++;
    
  else:
    // uncoolness must be rectified.
  
    $person->points = 0;
    print "Between you and me? Not the biggest fan, " . $person->name;
  endif;
endforeach;
  
// By grouping our variables into objects, and then
// into arrays, we can begin to build data structures
// capable of working with large quantities of data
// in a tidy and readable manner.

// The final step here is to wrap all that in a function call.
// This will allow us to execute all of this processing
// by merely executing our function, which we do as often
// as we like. Judgement, ahoy!

// A function is given a name, and can have variables given
// for use.
  
function cast_judgement($victim) {

  if($victim->is_cool):
    print "Hey, " . $victim->name . "! I think you're alright!";
    $person->points++;
  else:
    $victim->points = 0;
    print "Between you and me? Not the biggest fan, " . $victim->name;
  endif;

};

  
$bystanders = new array($nick, $chris, $colm);
    
foreach($bystanders as $person):
  cast_judgement($person);
endforeach;

// Alas, we are complete.
  
?>

{% endhighlight %}

Arrays and objects are how data structures are built in all programming languages - they're pretty universal concepts. At first, knowing the differences between them can be pretty tricky, and people don't always use them correctly in their code.

### Looping

In the example above, I glossed over the concepts behind looping through arrays. I'm going to continue that tradition here.

Shorthand examples:

{% highlight php %}

<?php

$bystanders = new Array($chris, $nick, $colm);

// there are two ways (and one shortcut) that you can write out
// foreach loops. you can use the curly brackets, you can use
// the colon in the beginning and the endforeach command at the
// end - I recommend you use this second way, and the reason is
// that as your foreach and if loops get complex, you can have
// this sea of closing tags and it's hard to keep them straight.

foreach($bystanders as $victim) {
 cast_judgement($victim);
}

foreach($bystanders as $victim):
 cast_judgement($victim);
endforeach;


// if you're only going to execute one line of code from your
// foreach loop, you can skip the endforeach altogether.

foreach($bystanders as $victim) cast_judgement($victim);

// which may also be written as

foreach($bystanders as $victim)
 cast_judgement($victim);

// all of the above examples are also true for if statements.

if($value_is_true) {
  cast_judgement($victim);
}

if($value_is_true):
  cast_judgement($victim);
endif;

if($value_is_true) cast_judgement($victim);

// which, again may also be written as

if($value_is_true)
 cast_judgement($victim);

// in addition to these shortcuts, there is a very neat way
// of writing out if statements. a full if / then loop looks
// like this

if($value_is_true):
  execute_function();
elseif($other_value_is_true):
  execute_another_function();
else:
  execute_a_third_function();
endif;

// Now, we dont always have this many options - there are many
// times where we just want to toggle a variable between two
// options

if($value_is_true):
  $dependant_variable = 5;
else:
  $dependant_variable = 10;
endif;

// There's a cleaner way to write this. We can write a ternary
// statement.

$dependant_variable = $value_is_true ? 5 : 10;

// What we're doing here is setting a value based on a condition.
// The condition comes between the equals and the question mark
// After that, we have what the outcome will be, separated by the
// colon. What comes before the colon will be the final value if
// the condition is true, and what comes after will be set if the
// condition is false. If the value is true, the dependant value
// will be set to 5, otherwise, 10.


?>


{% endhighlight %}

### Conditionals



## Templating

Wordpress uses templates to display their sites. It's sort of like a view layer, but it completely isn't. That's like half the reason seasoned devs don't like working with Wordpress. Soon, you won't like it for the same reason. For now, you're going to use it to learn how to put together complex coding environments.

The way wordpress templates work at the top level is what's known as the *template heirarchy system*. This is a set of rules that determine what php file is going to be requested from your theme folder to display, when given a URL request. It, like most webservers, will start by looking for an index.php file to serve in response to this request. However, there are many instances where it would look for a different file first.

When a browser sends a request to a Wordpress installation, the WP installation scans the url, checking it against known post types, taxonomies and other keywords and, based on those parameters, will choose a template to display. This set of rules is based on the template heirarchy. Study it, know it.

### Pages

The content and structure of a Wordpress site is set by the information in the database. When a user creates a page in a Wordpress installation, they are creating a "post object" in the database. When that page is requested by a user through a URL request, what they are seeing is a template file that is loaded based on the Template Heirarchy with the appropriate variables in place.

#### Post Types

In wordpress, out of the box there are two post types: pages and posts. This harkens back to the original intention of Wordpress to be used as a blogging platform. Typically, a blog would have a few pages with some content, maybe like a contact page where a blogger could let their followers know how to get in touch with them. For this, they would use a Page. The difference between Pages and Posts here is that Posts are programmed to display in archives, to have comments attached to them, and will be categorized and tagged. Given that there there are different roles that each of those types of content would play, it makes sense to separate them somehow, so that their information can be accessed in sensible ways.

The pages that you are going to create are going to contain a much wider assortment of data than a simple blog. The easiest use case to envision is a page that would contain a staff directory for a company. Envision the following use case:

A company wishes to include on their site a staff directory page that would contain 50-75 records. Each of these records will contain the name, picture and contact information of an individual. In addition to this, the pages will be broken up into sections, based on the individuals department within the company. Within those divisions, there will be different types of contact information - for instance, a person in sales will list their phone number on the directory page, but the people on the board of directors wouldn't want their names to be listed on the page.

How do we build this in a way that works on a responsive site and doesn't require the client to maintain a bulky HTML structure? We build a structure in the Wordpress backend that allows us to tailor information collected.


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

Now, lets say that the above segment is an entry in a directory that has been created for use on a website. We're not sure how many people are going to be listed in this directory - but we know there are going to be many. We also know that each of these people is going to have their own page on the site. So, we need to create a data environment inside Wordpress where a client can create pages for the people that are going to be listed on the website's frontend. In order to accomplish this, we're going to need to define a custom post type. This is the "place to house the data" from the above steplist (not all custom data requirements will need a custom post type). 

By default, any post object in wordpress is going to have the same data fields. This will include a title, content, excerpt, featured image, taxonomy information, author and url information (aka the permalink). There are a few others, but we're going to focus on these for now. Right away, we can see an issue here - how are we supposed to define an email address and a phone number? Enter the "Custom Field". We use a plugin called Advanced Custom Fields to configure a post's metadata. It is very well documented, I cannot recommend reading the docs enough.

By configuring the custom fields on your post type, you can add fields for the client to enter a phone number and an email address directly into the post data.






## Logic

### Wordpress Automagication

Wordpress is an application. It does many things for you as a developer. By the time your template is loaded, the application dials into a database, pulls out a specific slice of information, formats it and serves it to the developer. Wordpress is an application that is indended for people who are unfamilar with modern MVC development environments. The modern term for this would be something like an "opinionated framework". So, when wordpress displays a given template from the heirarchy after scanning the URL's keywords - there are a host of variables that have been set by the Wordpress system.

These are the global variables, and they are set based on which template has been loaded from the heirarchy (based on the URL). In terms of development, it is very useful to note that the global variables are set by the url that the browser requests.

### The Loop

You can't talk about wordpress installations without talking about the loop. It sort of encapsulates the entire issue between WP and modern development environments. When wordpress scans the URL of the browser request and directs to a file in the theme directory - it also creates a query.

In Wordpress parlance, "the query" is a PHP object created on page load. It has a whole bunch of stuff in it, but the really important parts are the query's post, and the associated objects and arguments. One of the strongest reasons to make use of the template heirarchy in Wordpress is that it customizes these queries based purely on the template used. So, if you create a file named archive-car.php, and then pulled up a wordpress installation that had a post type called "car", and that post type was configured to have archives, when you requested a url that fit into the "show the archive for the car's post type" - you're going to find that your query variable is put together with your posts and your helper functions in place. Replicating those queries is a very time intensive process and is strongly discouraged.

### Menus

CMS menus are a tricky beast. Ultimately, we're building a nested <ul> - but the process of making that out of recursive functions is really tricky. There are things called walker functions that you can use to customize the output of the menus, but they can be pretty tricky to understand.

### The Media Library

Wordpress has an online asset manager called the Media Library. It is pretty customizable, but we don't get super far into working with it. Each item, upon upload, is logged into the Database system according to it's own data model. Helper functions exist that will allow you access to the data stored in here, but that doesn't really come up in the front-end world.

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

<?php

// this would be in a different file

TSD\Display::say_hi_to_admin();

?>


{% endhighlight %}

The above code snippet could be placed anywhere on the page to send a message to anyone on the site who is logged in. These functions can be very helpful when you need to attach logic to a given command, without cluttering up your display files. It's important to keep a neat display file, and to keep your helper functions tucked away in your display classes. This will allow you to deliver a rich web experience without compromising the readability of your template files. This will also allow you to keep your structure flexible, for when people inevitably start requesting substantive changes to your template layout.

# Glossary


{% for term in site.data.glossary %}

{{ term.word }}

{% endfor %}
