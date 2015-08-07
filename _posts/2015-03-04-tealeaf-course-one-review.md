---
layout: post
title:  "Tealeaf Course One Review"
author: "Andrew Buckingham"
date:   2015-03-04 7:29
permalink: /blog/2015/03/04/tealeaf-course-one-review/
category: blog
tags:
- ruby
- code
- tealeaf

---

I've finished the first course at [Tealeaf Academy](http://www.gotealeaf.com), and I feel great about what I've accomplished. I took my time, because I believe that it's important to get the fundamentals right. Before I signed up, I read a lot of blogs from people who had gone through the course, and one thing I noticed was that some of them admitted that they'd rushed a bit in the beginning, and so felt overwhelmed later. Perhaps that is inevitable, because there is so much to learn, but I wanted to make sure that I had a solid foundation. Ruby on Rails is a powerful framework for building applications, but it is **just Ruby**. So that means the better I understand Ruby, the better I'll understand how to use Ruby on Rails.

There are a lot of choices if you want to learn how to code. I've already discussed my rationale for signing up with Tealeaf in [an earlier post](http://andrewbuckingham.net/blog/2014/08/13/Tealeaf-Academy/). So how did my first course go?
<!-- more -->

In a word, it was outstanding. I know there are many other good programs out there there, but I know I picked the best one for me. I'll address the four most important aspects of the program:

1. The quality of instruction
2. The structure of the course
3. The content of the lessons
4. Final thoughts

## The quality of instruction

Unlike some programs, you don't get to meet with a mentor each week. But you are never alone. If you have a question, or if you need to have someone review your code, you can use the forum to post it, and you'll receive prompt and personalized attention. Obviously, the response times are faster during certain hours of the day, but you'll get help within a few hours, at the very most. I often posted things at night, had a response waiting when I got up the next morning. On top of that, you can always chat with other students (and often TAs/instructors) in the 'Student Lounge.'  Honestly, I probably retreated and spent too much time working through the material on my own, but that was my process. Officially, the course is a four-week course, but it took me closer to four months. Throughout all of that, the instructors are always kind and patient, and they know their stuff. 

## The structure of the course
The course stresses learning the fundamentals of Ruby, and then progressively builds upon that knowledge. Before the course, there is a pre-course (note that after I'd started the first course, they turned this into a free 'Prep Course', which might be different than the pre-course that I took). You can learn a lot for free, by going through the [free textbooks and workbooks](https://www.gotealeaf.com/books) they've written. If you're interested in trying the free Prep Course, create a free account here: <http://www.gotealeaf.com>). In the pre-course, you go through their textbook, and learn the basics of Ruby. I spent a lot of time with this. I made an [org-mode](http://www.orgmode.org) outline, complete with code blocks, which I could export into their own Ruby files (see the files and the [notes.org](https://github.com/XiaoA/tealeaf-precourse/blob/master/notes.org) notebook [here](https://github.com/XiaoA/tealeaf-precourse/blob/master/README.md)). In the notes, I reworded the lessons, in my own words, with extra experiments, comments, and my record of the exercises (complete with my successes and failures). Looking at it now, it's a very intimate record of my learning process. I wanted to explain everything in my own way, because that helped me process the information and internalize it. Plus, it's a great reference that I can refer to later.

The course itself consists of four lessons. In the past, before I joined Tealeaf, everyone learned together, and each lesson was scheduled to last one week. But over time, as some students fell behind, the format was changed to allow students to go at their own pace. This is one of the most unique aspects of the program, and one that has worked very well for me.



## The content of the lessons

### The Course included the following projects:
- [tealeaf-course1-week1](https://github.com/XiaoA/tealeaf-course1-week1)
- [reverse_madlibs](https://github.com/XiaoA/reverse_madlibs)
- [tealeaf-course1-lesson2](https://github.com/XiaoA/tealeaf-course1-lesson2)
- [Ruby_Blackjack](https://github.com/XiaoA/Ruby_Blackjack)
- [sinatra_blackjack_webapp](https://github.com/XiaoA/sinatra_blackjack_webapp)

Some of the other programs allow students to choose their own projects, and work with a mentor to complete them. That could work well for some, but while I have a lot of ideas for projects, I found it hard to choose one that would be appropriate. And worse yet, it might not allow me to learn everything I needed. The advantage of the Tealeaf way is that I know I'll get a really good understanding, which I can use to complete my own projects with later. 

The capstone project of the first lesson was a procedural Blackjack game. Ruby is a great Object-Oriented language, but it is possible to build some interesting things in a procedural way. But the limitations become very clear, very quickly. When I was 11, I learned BASIC in summer school. This lesson reminded me of that. The program worked from the top to the bottom, so everything had to be neatly ordered. It is possible to use loops and conditionals to build some sophisticated flow control behavior, but it's very brittle, and I cringed at the idea of adding a feature or making any changes, for fear of bringing the whole house of cards down.

In the second lesson, we dived into Object-Oriented Programming, which allowed us to write cleaner, more efficient code. We redid the Tic-Tac-Toe and Blackjack assignments, and they were much easier to write, read, and debug.

For example, in both versions, if either the player or dealer gets Blackjack or busts, the game is over, but if not, both the player and the dealer get a turn. At the end, the final card values are calculated, and the winner is declared. In the procedural version, the code to calculate a winner looks like this:

{% highlight ruby linenos %}
# ...preceding code cut for brevity...

if (dealer_sum > 21) && (player_sum < 21)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand}"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand}"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  say "Dealer busted. You win!"
  puts "  "
  player_cash_pot = (player_cash_pot.to_i + bet.to_i)
  puts "You won \$#{bet}. You now have \$#{player_cash_pot}."
elsif (dealer_sum == 21) && (player_sum !=21) && (dealer_hand.count == 2)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand}"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand}"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  say "Dealer hit Blackjack!"
  puts "  "
  player_cash_pot = player_cash_pot.to_i - bet.to_i
  puts "You lost #{bet}. You now have \$#{player_cash_pot}."
elsif (dealer_sum == 21) && (player_sum !=21) && (dealer_hand.count >= 3)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand}"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand}"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  say "Dealer wins!"
  puts "  "
  player_cash_pot = player_cash_pot.to_i - bet.to_i
  puts "You lost #{bet}. You now have \$#{player_cash_pot}."
elsif (player_sum < 21) && (dealer_sum < player_sum)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand}"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand}"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  puts "#{name} wins!"
  puts "  "
  player_cash_pot = (player_cash_pot.to_i + bet.to_i)
  puts "You won \$#{bet.to_i}. You now have \$#{player_cash_pot}."
elsif (player_sum == 21) && (dealer_sum !=21) && (player_hand.count >= 3)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand}"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand}"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  say "#{name} wins!"
  puts "  "
  player_cash_pot = (player_cash_pot.to_i - bet.to_i)
  puts "You lost \$#{bet.to_i}. You now have \$#{player_cash_pot}."
elsif (player_sum > 21) && (dealer_sum < 21)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand}"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand}"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  say "You busted!"
  puts "  "
  player_cash_pot = (player_cash_pot.to_i - bet.to_i)
  puts "You lost \$#{bet.to_i}. You now have \$#{player_cash_pot}."
elsif (dealer_sum < 21) && (player_sum < dealer_sum)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand},"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand},"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  say "Dealer wins"
  player_cash_pot = (player_cash_pot.to_i - bet.to_i)
  puts "You lost \$#{bet}. You now have \$#{player_cash_pot}."
elsif (dealer_sum >= 17) && (dealer_sum <= 21) && (dealer_sum == player_sum) 
  system 'clear'
  push = player_sum
  puts "---"
  puts "#{name}'s hand: #{player_hand},"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand},"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  player_cash_pot = player_cash_pot.to_i
  say "We both got #{push}. It's a push!"
  say "The bet will carry over to the next hand..."
elsif (dealer_sum > 21) && (player_sum > 21)
  system 'clear'
  puts "---"
  puts "#{name}'s hand: #{player_hand},"
  say "value: #{player_sum}"
  puts "---"
  puts "Dealer's hand: #{dealer_hand},"
  say "value: #{dealer_sum}"
  puts "---"
  puts "  "
  say "We both busted. #{name} loses."
  player_cash_pot = (player_cash_pot.to_i - bet.to_i)
  puts "You lost \$#{bet}. You now have \$#{player_cash_pot}."
end
{% endhighlight %}	

That's 124 lines of code, just to calculate a winner. In the object-oriented version, most of the components of the game, including: player, dealer, hand, and game are encapsulated as Classes, with methods and modules to support the action. So instead of having to chronologically describe each outcome of the game, each game scenario has been extracted into a method in the Game class. For example, if the player wins:

The player is awarded the winning pot:

{% highlight ruby linenos %}
def calculate_player_winning_cash_pot_balance
  self.cash_pot = show_cash_pot + show_bet
end
{% endhighlight %}

The player is declared a winner:

{% highlight ruby linenos %}
# ...preceding code cut for brevity...
def player_high_score_message   
  show_all_cards_at_end
  puts "=> Congratulations, #{player.name}! You won!"
  puts " " 
  puts "You bet \$#{show_bet}." 
  puts "You now have \$#{calculate_player_winning_cash_pot_balance}."
end
{% endhighlight %}

Notice that the **calculate_player_winning_cash_pot_balance** method is called from within the **player_high_score_message** method. There are similar methods for determining when the dealer wins, or when there is a tie, and they can be called during the game.

After I'd finished the game and submitted it for review, I looked at the last lines of the OOP code, and realized that when we begin a new game, we're actually calling a new **Game** object. *In other words, the game, itself, is an object!*

{% highlight ruby %}
game = Game.new
game.start
{% endhighlight %}

Confronted with the brilliance, expressiveness, and beauty of Ruby, how could I not love this language? 

In the third and fourth lessons, we switched to web development, and after covering the basics of HTTP, HTML, CSS, and JavaScript, we rebuilt the Blackjack game as a Sinatra webapp, and pushed it to [Heroku](https://www.heroku.com/).

[Sinatra](http://www.sinatrarb.com/) is a great Domain-Specific Language, or [DSL](http://en.wikipedia.org/wiki/Domain-specific_language), based on Ruby. I saw a lot of parallels to Ruby, and [Jekyll](http://jekyllrb.com/), which I've used to create this site. Sinatra has a simple syntax for specifying routes with Ruby blocks, which are outlined on Sinatra's [Getting Started](http://www.sinatrarb.com/intro.html).

I'm planning to talk more about my Sinatra Blackjack game in a separate post, but here is what the code looks like for comparing the Player's and Dealer's hands:

{% highlight ruby linenos %}
get '/game/compare' do
  @show_hit_or_stand_buttons = false

  player_total = calculate_total(session[:player_cards])
  dealer_total = calculate_total(session[:dealer_cards])

  if player_total < dealer_total
    loser!("#{session[:player_name]} stands at #{player_total}, and the dealer stands at #{dealer_total}.")
  elsif player_total > dealer_total
    winner!("#{session[:player_name]} stands at #{player_total}, and the dealer stands at #{dealer_total}.")
  else
    tie!("Both #{session[:player_name]} and the dealer stand at #{player_total}.")
  end

  erb :game, layout: false
end
{% endhighlight %}

If you'd like to play the Blackjack webapp game, it's here: <https://salty-crag-8411.herokuapp.com/>.

## Final thoughts
The most important thing that I've learned in this course is not Ruby, or how to build any of the projects that I've completed. What really helped was having mentors, who could help me stay focused on what is truly important. I love learning things on my own, but it's very easy to get sidetracked, and spend too much time on side topics that won't help me move forward. That's why I have a scattered skillset of HTML, CSS, JS, and SQL, but have struggled to bring them together to accomplish practical goals. The head teacher, Chris, always warns us, "Don't go sideways." In other words, you could spend a week online, looking at the differences between [RVM and RBENV](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=rvm%20vs.%20rbenv), for example, instead of just using one of them to learn how to build applications. Being able to rely on the experience and guidance of friendly and caring instructors, to help me understand what I needed to study (and more importantly, what I could ignore for now) has made a huge difference.

I enjoyed the first program, and I learned a lot. In the next course, I'll begin working with Ruby on Rails. After the foundation that I've established in the first course, I'm sure it will be challenging, but not overwhelming.




