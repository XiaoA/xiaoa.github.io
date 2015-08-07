---
title: A Simple Way to Implement Case-Insensitive Searches in Rails
layout: post
date: 2015-07-13 20:08:47 -05:00
comments: true
category : blog
tags : [rails, sql, code]

---
In my current project for the [final Rails course](http://www.gotealeaf.com/curriculum#!production-apps) at [Tealeaf Academy](gotealeaf.com), I'm creating 'MyFlix,' a clone of Netflix, built with Ruby, instead of Java. I just added functionality to search for a video by title, but it was case-sensitive, so a search for `monk` returned an empty array, but a search for `Monk` returned the proper result. I wasn't satisfied with that, so I decided to implement case-insensitive searches. Fortunately, it's really easy in Postgresql. Here's how I did it...

<!-- more -->

## A Look at Oracle SQL
I've used various flavors of SQL, including MS Access, MySQL, Oracle, and Postgresql. They all share a common language, but each implementation has its own unique features and quirks. As a Blackboard Administrator, I've been accessing an Oracle database everyday, so I'm pretty comfortable with it. My favorite unique Oracle operator is `regexp_like`. Here's a simple example of how you could use it to find all Blackboard course sites from Summer Semester 2015 (with 'SS2015' in the Course ID):

{% highlight sql %}
SELECT * FROM course_main WHERE regexp_like(course_id, 'SS2015');
{% endhighlight %}

You'll receive a list of all records with 'SS2015' anywhere in the `course_id` field. A more generic SQL query would be:

{% highlight sql %}
SELECT * FROM course_main WHERE course_id LIKE '%SS2015%';
{% endhighlight %}

The advantage of using `regexp_like` in Oracle SQL is that feels a bit easier to type. Plus, it's easy to create more granular searches. For example, it's trivial to make your search case-insensitive, by adding an 'i' argument after the search terms:

{% highlight sql %}
SELECT * FROM users WHERE regexp_like(firstname, 'and', 'i');
{% endhighlight %}

In this case, you'd get a list of first names that included, for example, both 'Andrew' and 'Brandi.' But how does case-insensitive search work in Postgresql?

## Searching for Videos by Title in Postgresql

Like any video site, MyFlix needs an easy way for users to search for the video they'd like to watch. Here is the original version, without case-insenstive search:

{% highlight ruby linenos %}
class Video < ActiveRecord::Base
  belongs_to :category

  validates_presence_of  :title, :description

  def self.search_by_title(search_term)
    return [] if search_term.blank?
    where("title LIKE ?", "%#{search_term}%").order("created_at DESC")
  end
end
{% endhighlight %}	

I wasn't sure how I could implement a case-insensitive search. I figured I'd need work out some regex. But thanks to this blog post: <http://robb.weblaws.org/2013/12/05/yes-rails-supports-case-insensitive-database-queries/>, I learned about Postgresql's `ILIKE` operator. It's so simple, and yet powerful! With one change, from the `LIKE` operator to the `ILIKE` operator (compare line 8), you are no longer restricted to case-sensitive searches.

{% highlight ruby linenos %}
class Video < ActiveRecord::Base
  belongs_to :category

  validates_presence_of  :title, :description

  def self.search_by_title(search_term)
    return [] if search_term.blank?
    where("title ILIKE ?", "%#{search_term}%").order("created_at DESC")
  end
end
{% endhighlight %}	

Here's the Postgresql API documentation for functions matching: <http://www.postgresql.org/docs/8.3/static/functions-matching.html>.

