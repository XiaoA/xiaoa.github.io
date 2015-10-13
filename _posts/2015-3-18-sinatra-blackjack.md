---
layout: post
title: "Sinatra Blackjack"
author: "Andrew Buckingham"
date: 2015-03-18
permalink: /blog/2015/03/18/sinatra-blackjack/
category: blog
tags:
- ruby
- code
- tealeaf
- sinatra

---
Step up and place your bets! I've created a simple Blackjack game here: <https://salty-crag-8411.herokuapp.com/>. I hope you'll give it a try! I built it with [Sinatra][sinatra] and deployed it to [Heroku][heroku].

Like Rails, Sinatra is a Domain-Specific Language, or [DSL][dsl], based on Ruby. Sinatra uses a simple syntax for specifying routes with Ruby blocks, which are outlined on Sinatra's [Getting Started][intro] page.

In my [Sinatra Blackjack game][git], these routes help control the flow of the Blackjack game, as the player competes with the dealer for the highest Blackjack score (21). Just like Rails, it uses the [MVC](mvc) pattern to render or redirect the appropriate page. Sinatra is a pure joy to work with; simple but powerful! Here's how I used it to build a simple Blackjack game.

<!-- more -->

## Game Start
Sinatra serves the '/' (root) route, and evaluates the conditional in the `'do'` block:


{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 85 91 %}
{% endhighlight %}

If the `session[:player_name]` contains a value (because the user has entered a name into the input form), the game is redirected to the `/game` view. If it's empty, the user must enter a name, so it redirects to the `/new_player` route.

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 93 106 %}
{% endhighlight %}


The app does not use a database. Instead, the following types of `session[:id]` (cookies) are used to store persistent data:

- `[:player_bankroll]`: The player's total amount of money available to bet
- `[:player_name]`: The player's name
- `[:bet_amount]`: The value of the player's bet
- `[:dealer_cards]`: The dealer's hand
- `[:player_cards]`: The player's hand
- `[:deck]`: The deck
- `[:turn]`: Whose turn it is to hit/stand

When a user vists <https://salty-crag-8411.herokuapp.com/>, he or she is prompted for a name. This name is stored in `session[:player_name]`.

Next, the player is prompted for a bet.

The player is taken to "/bet" and the 'bet.html.erb' view is rendered:

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 108 124 %}
{% endhighlight %}


After the player enters a bet amount, a series of checks are performed:

1. If the player has no money, the game is redirected to '/no_money' and the game is over.
2. If the player tries to enter anything other than a number, the dealer asks for the player to try again.
3. If the bet is less than the minimum ($5), or more than the player's total bankroll, the player is asked to bet again.
4. If the bet is valid, the bet amount is saved as `session[:bet_amount]`, and the player is directed to the '/game' route.

In the `'/game'` route, the cards are shuffled and dealt.

- If the player has 21, it's a Blackjack.
- If the player's cards total more than 21, it's a bust.
- Oherwise the player is offered the chance to hit or stand.

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 128 155 %}
{% endhighlight %}

## The Player's Turn
If the player chooses to hit, he/she is redirected to `/game/player/hit`.  

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 156 169 %}
{% endhighlight %}



If the player chooses to stand, he/she is redirected to `/game/player/stand`.  

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 170 175 %}
{% endhighlight %}

## The Dealer's Turn
Now, it's the dealer's turn. The dealer must hit until he/she has at least 17. We can use a constant, `DEALER_MINIMUM_HIT_AMOUNT`, to represent this requirement.

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 176 193 %}
{% endhighlight %}

Until the dealer reaches at least 17, he/she must hit:

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 196 200 %}
{% endhighlight %}

## Choosing a Winner
Finally, if neither the player nor the dealer have hit Blackjack or busted, we need a way to compare the values of their hands, and declare a winner:

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 201 217 %}
{% endhighlight %}

## Ending the Game

At the end of each match, the player is routed back to the beginning, where he/she is free to place a new bet or quit. There are two scenarios where he game must end:

1. The player has money, but leaves the table
2. The player is out of money

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/305a73dfb31c31ad088a2040233eaca6ba6fe62a/main.rb 218 225 %}
{% endhighlight %}

Both of these scenarios can be handled very easily with the appropriate views:

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/ff0ec7cb44644e8a434c3c106675048098dbd4ae/views/no_money.erb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/ff0ec7cb44644e8a434c3c106675048098dbd4ae/views/no_money.erb %}
{% endhighlight %}

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/74ab3203e11c95eca5d2523cc517ba77c2e724d6/views/game_over.erb %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/74ab3203e11c95eca5d2523cc517ba77c2e724d6/views/game_over.erb %}
{% endhighlight %}

## Ajax!

One cool bonus, which you should notice as you play the game, is that the entire page does not reload with each action. The application includes jQuery code to prevent all but essential reloads for the following game actions:

- when the player hits
- when the player stands
- when the dealer hits

{% github_sample_ref /XiaoA/sinatra_blackjack_webapp/blob/67cece1a535da0f85af11c96456d4a477a7bed3c/public/application.js %}
{% highlight ruby %}
{% github_sample /XiaoA/sinatra_blackjack_webapp/blob/67cece1a535da0f85af11c96456d4a477a7bed3c/public/application.js %}
{% endhighlight %}

This provides for a smoother user experience, and it saves some bandwidth. I hope you've enjoyed this tour of my first Sinatra web app. I had a lot fun building it.


[sinatra]: http://www.sinatrarb.com/
[heroku]: https://www.heroku.com/
[intro]: http://www.sinatrarb.com/intro.html
[dsl]: http://en.wikipedia.org/wiki/Domain-specific_language
[git]: https://github.com/XiaoA/sinatra_blackjack_webapp
[no money]: https://github.com/XiaoA/sinatra_blackjack_webapp/blob/master/views/no_money.erb
[game_over]: https://github.com/XiaoA/sinatra_blackjack_webapp/blob/master/views/game_over.erb

