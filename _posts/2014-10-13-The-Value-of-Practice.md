---
layout: post
title:  "The Value of Practice"
author: "Andrew Buckingham"
date:   2014-10-13 21:39:23
permalink: /blog/2014/10/13/The-Value-of-Practice/
category: blog
tags:
- ruby
- code

---

I'm working my way through the pre-course '[Learn Ruby](https://www.gotealeaf.com/books/ruby/read/flow_control#casestatement)' online textbook at Tealeaf, and I came across a problem that I couldn't solve without checking the answer. So after I watched the video and followed along, I created my own simple variation. It was similar to the original, but different enough to demonstrate that I'd internalized the lesson. 

I like writing code because it's all about solving problems, and it can be incredibly expressive. But learning anything requires us to move just beyond our current capabilities, and apply what we know to new problems. Here is a simple example of how I did that.

<!-- more -->

The exact details of the problem are not that interesting, but essentially, Exercise 5 asked me to rewrite an **if/else method** ('evaluate_num'), which I'd made for Exercise 3, as a **case method**, using two different forms of the syntax ('evaluate_case1_num' and 'evaluate_case2_num'). I had some difficulty, so I checked the solution.

Here is the authors' solution:

{% highlight ruby linenos %}
# evaluate_num_revisited.rb

def evaluate_num(num)
  if num < 0
    puts "You can't enter a negative num!"
  elsif num <= 50
    puts "#{num} is between 0 and 50"
  elsif num <= 100
    puts "#{num} is between 51 and 100"
  else
    puts "#{num} is above 100"
  end
end

def evaluate_case1_num(num)
  case
  when num < 0
    puts "You can't enter a negative num!"
  when num <= 50
    puts "#{num} is between 0 and 50"
  when num <= 100
    puts "#{num} is between 51 and 100"
  else
    puts "#{num} is above 100"
  end
end

def evaluate_case2_num(num)
  case num
  when 0..50
    puts "#{num} is between 0 and 50"
  when 51..100
    puts "#{num} is between 51 and 100"
  else
    if num < 0
      puts "You can't enter a negative num!"
    else
      puts "#{num} is above 100"
    end
  end
end

puts "Please enter a number between 0 and 100."
number = gets.chomp.to_i

evaluate_num(number)
evaluate_case1_num(number)
evaluate_case2_num(number)
{% endhighlight %}

After I saw this and watched the video, I understood what I'd been doing wrong, but I wasn't sure if I could apply what I'd learned. So I created my own original version. It's very similar, but instead of asking for a number, it asks the user to talk about his/her day. The feedback the user gets depends on the length of the answer.

The point of doing three versions is to demonstrate three ways to solve the same problem, using both 'if/else' statements and 'case' statements. My program follows the same form, but makes a few changes. For example, in the **string_length** method:

* Instead of asking for a number, it lets you type in whatever you want, and it counts the number of characters in your answer. 
* It provides three answer options, depending on the length of your answer.

{% highlight ruby lineos %}
def string_length(num)
  if num == 0
    puts "You have to give me something to work with, here."
  elsif num <= 10
    puts "You're not much with words, are you?"
  elsif num <= 20
    puts "You've got a lot to say."
  else
    puts "Sounds like you had quite a day!"
  end
end
{% endhighlight %}


1. If the user provides no answer, the program replies, "You have to give me something to work with here."
2. If the user's answer is 10 characters or less, the program says, "You're not much with words, are you?"
3. For answers of 11 - 20 characters, the response is: "Sounds like you had quite a day!"
4. Answers with 21 or more characters prompt the reply, "Sounds like you had quite a day!"

Here's the full version, with the three versions that perform the same behavior:

{% highlight ruby linenos %}
# I had trouble figuring out 05_flow_control/evaluate_num.rb on my own, so I created a new version for practice.
# This program asks how your day was. The length of your answer determines the reply!
def string_length(num)
  if num == 0
    puts "You have to give me something to work with, here."
  elsif num <= 10
    puts "You're not much with words, are you?"
  elsif num <= 20
    puts "You've got a lot to say."
  else
    puts "Sounds like you had quite a day!"
  end
end

def string_length_case1(num)
  case
  when num == 0
    puts "You have to give me something to work with, here."
  when num <= 10
    puts "You're not much with words, are you?"
  when num <=20
    puts "You've got a lot to say."
  else
    puts "Sounds like you had quite a day!"
  end
end

def string_length_case2(num)
  case num
  when 1..10
    puts "You're not much with words, are you?"
  when 11..20
    puts "You've got a lot to say."
  else
    if num == 0
      puts "You have to give me something to work with, here."
    else
      puts "Sounds like you had quite a day!"
    end
  end
end

puts "Tell me about your day."
number = gets.chomp.to_s.length

string_length(number)
string_length_case1(number)
string_length_case2(number)
{% endhighlight %}

The code itself is very simple. But it's important to study good examples, and then use them as a basis for making new and more complex discoveries. *And that is how we learn!* I was a teacher before, and I have always been interested in understanding how the mind works, and how to improve my ability to learn. One of the most influential scholars, whose theories have resonated with my own experience of learning, is the Psychologist and Learning Theorist, [Lev Vgotsky](https://en.wikipedia.org/wiki/Lev_Vygotsky). He posited the idea of a "[Zone of Proximal Development](https://en.wikipedia.org/wiki/Zone_of_proximal_development)," which was just beyond the current level of a student's ability to perform learning tasks.

At the risk of oversimplifying, this means that learning occurs when we move from a point where we cannot perform tasks without help, to a point where we can do them on our own (A.K.A. our Zone of Proximal Development). With the proper support ('scaffolding') to build this competency, I have no doubt I'll keep learning for the rest of my life! This is just one example of how I am building my knowledge of Ruby every day. I have a lot to learn, but every day, I take another step...

