---
layout: post
title:      "NoMethodError in Sinatra MVC project"
date:       2020-09-17 19:27:37 -0400
permalink:  nomethoderror_in_sinatra_mvc_project
---


Something that you will run into very often while doing your Sinatra project, is a really fun error called the NoMethodError. This will happen while running shotgun in your terminal. Now your server is up and running, you type in the url something similar to this http://127.0.0.1:9393/ferret/something_wrong and wait for the view to render, only it never renders and you get redirected to a page saying NoMethodError in all red. Most of the time you will get a few hints on where your problem came from. To get your first hint you would immediatly look at the top. 

It will say no method error at and then say a route, mine was at `/ferrets/10` 
The next hint is directly underneath, it will say something like undefinded method 'email' for nil:NilClass 
In one case during my project I had problem trying to get the user who created a ferret to display. I should mention my project involved a ferret camp. In my user table there was a column for email and that was also used to be one of my validation features for a user. 

The method email was undefined in this case. 
The last hint for what is wrong is under the undefined method. It will say where the code was evaluated and had a problem, in my case it was in the show.html.erb file. THIS DOES NOT MEAN THE PROBLEM IS EXACTLY IN THAT FILE. 

The code was 
`<p><%= @ferret.user.email %></p>`
Looking at this there is nothing at all wrong with the code. I checked a bunch of thing but couldn't figure out where the problem was. The last most final thing to get some info about this error was the get and post information.... there was none. This immediately made me go look in my routes in the ferrets controller. All along it was just the way I was passing in my @ferret. The view couldnt render anything with the proper information.
It was a super easy fix, but also super easy to overlook. 

The quickest and best way to solve the NoMethodError problem for any undefinded method for nil:NilClass is to first ask what is being called.
Next figure out what is nil. Then of course ask why is this nil. What did I want to happen and what actually happened. Check our 3 main areas for hints. Be sure you are getting proper get or post data.

This logic of solving the NoMethodError came in very handy towards the end of my project. I was really trying to have only certain butons appear for certain users as well as access to certain content depending on if you created it or not. 
I first look where the NoMethodError is at. It happened in the /ferrets route, which is called right away. The controller looked fine so I kept looking at my hints.
It said the undefined method was for use for nil:NilClass. in my head I thought "Oh no what the heck does this mean, I solved my last problem that was almost exaclty the same, whats wrong now".

Under undefinded method was the file with the problem, the location and line. I got look at that and it was working fine for everything else. This was the code:
` def authorize_ferret(ferret)
    current_user == ferret.user  
  end`
Ok nothing wrong with that, but I started looking where I called authorize_ferret. I tried using it in the index views. 
```
<% if authorize_ferret(@ferret)%>
```
This where we ask those questions. 
What did you want to happen? I wanted to display only ferrets that were made by the logged in user.
What actually happened? I got a method returning nil.
My post and get had no data in them so I jumped to my controller and noticed something I missed the first time. I used @ferrets in the controller and @ferret in the route.
That was my first mistake. My second mistake with all of this was the way I went about setting up logic for my views. I tried using authorize ferret, which was something I setup just to set the current user to ferret.user. It was essential for when we would edit a registered ferret. This was the complete wrong place to use this and was the main reason the code didn't work.
```
<% current_user.ferrets.each do |ferret| %>
<li><a href="/ferrets/<%= ferret.id %>"><%= ferret.name %>  <%# ferret.hair %></li>
<% end %>
</ul>

```
I ended up using this line of code, a very simple interation of all the ferrets ascociated with the current_user.
I hope this logic helps you figure out and solve your NoMethodErrors faster! :)

![Error Pick](nomethoderror.png)
![Error Pick2](error.png)
