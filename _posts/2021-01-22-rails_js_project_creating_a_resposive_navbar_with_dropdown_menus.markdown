---
layout: post
title:      "Rails/JS Project Creating a Resposive Navbar with Dropdown Menus"
date:       2021-01-22 12:21:47 -0500
permalink:  rails_js_project_creating_a_resposive_navbar_with_dropdown_menus
---


If you ever wanted or needed to understand how to implement a sticky navbar that moves with you as you scroll, well you (might have) came to the right place. Also, if for some reason the screen view was smaller, as in the window become smaller or maybe we’re viewing our app on mobile, whatever the case I wanted to be able to toggle the navbar so you could still see the options instead of losing them from the view or having them become squished and stacked on each other. Now I made this navbar for my Rails/Js project. I wanted to make some type of website where a user can look up games, create/add them, and attach a review if the user wanted. I went a little further than the requirements asked, because we did not need to implement a user with authentication, but it made more sense to be able to log in, before you could start posting, editing and deleting reviews.  

One of the main challenges was figuring out how I wanted this navbar to look. I went on a bunch of video game website and looked to see how they were modeled, I wanted to have a drop-down menu listing different page options. Ironically none of this will affect the direct CRUD of the app, but I was hoping to implement a console attribute to the games so if you click on the drop-down menu, JS will display different games. For right now its al just cosmetic for the page.   

I went online and just kept googling navbars and how to customize them.  I found a few great resources that helped in the process of creating the navbar. 

[](http://)https://www.w3schools.com/css/css_navbar_horizontal.asp 

[https://www.tailwindtoolbox.com/templates/responsive-header ](http://)

The first taught me how to create a nice layout and create some borders between my dropdown menus. The second link was very helpful, there's a lot of other cool things on this website that helped me craft my project view, but this website taught me how to code a toggle menu button for when the viewing window became smaller. 

This is the code for the toggle button, nothing crazy but it remains hidden until needed which I think is very cool. 

```
<div class="block lg:hidden"> 

      <button id="nav-toggle" class="flex items-center px-3 py-2 border rounded text-gray-500 border-gray-600 hover:text-white hover:border-white"> 

        <svg class="fill-current h-3 w-3" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg> 

      </button> 

    </div> 
```

Now to get this working we need to use Javescript to actually update the navbar for us as things change. I almost wanted to make an event listener for the toggle, but that could get messy fast. The website explains how to toggle using this bit of code right here. 

```
<script> 

    //Javascript to toggle the menu 

    document.getElementById('nav-toggle').onclick = function(){ 

      document.getElementById("nav-content").classList.toggle("hidden"); 

    } 

</script>
```

This was great, but took a lot of tweaking to get the code working right with the layout I had. It was also a little hard to get the drop-down method to work inside the fixed navbar. First, I had originally hard coded the navbar using list items in an unordered list, that was a rookie move looking back at it now. 

The main problem I had was after I got the navbar working, it was overlapping my containers and I could not get them to be positioned properly. There were coded to automatically move with the window if it shrunk, maybe you opened up inspect and the screen got smaller, that shouldn’t break the application. I was getting pretty frustrated trying to reposition everything and even then, it would still overlap at certain points. 

I went back into the navbar code and literally started messing with every bit of code seeing how everything changed.  

```
<nav class="flex items-center justify-between flex-wrap bg-gray-800 p-6 fixed w-full z-10 top-0"> 
```

I went online and looked to see if people have come across this in the past, and yes, many people have with many different situautions. It appeared people had trouble using a fixed navbar and the overlapping. I really couldn’t find anything to help with the repositioning, but I randomly decided to change fixed to sticky. I don’t know what made me do that, but it WORKED! 

```
<nav class="flex items-center justify-between flex-wrap bg-gray-800 p-6 sticky w-full z-10 top-0">
```

I refreshed the page and like magic everything aligned and fixed itself, I was so happy. I still wanted the fixed navbar because I liked that it would only follow the scroll after a certain point. I spent far too much time on this feature and had no problem settling for a small cosmetic difference when scrolling with the navbar. 

I hope that this post might help someone like me in the future trying to figure out how to deal with a finicky navbar, sometimes you need to take a step back and see if you're making things harder than they needed to be, and I certainly was. 
