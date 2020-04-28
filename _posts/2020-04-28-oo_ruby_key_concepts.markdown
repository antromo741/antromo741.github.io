---
layout: post
title:      "OO Ruby Key Concepts "
date:       2020-04-28 15:42:58 +0000
permalink:  oo_ruby_key_concepts
---


As I continue on in this program, I have found it very helpful to go back and review the concepts that were talked about early on. At the time I had a decent understanding, but now everything makes way more sense. So here is a little cheat sheet or a summary of the basic concepts from OO Ruby.

**Abstraction**
I feel like abstraction is something any software developer should do first. At this point it' s almost being done subconciously. When coding anything its always good to use real world examples as a way to think about what the behaviours and attributes of our objects should be. We aren't even thinking about the small bits that are going to get this code working, but only focus on our objects and methods.

**Encapsulation**
As a way to organize and keep our objects unique we try set up some boundaries to encapsulate our code. Let's think of an example. We have two objects that are kinda similar like a PB&J sandwich  and a BLT sandwich. Both will contain similar behaviours like having bread and tasting good. But they have a few differences. We can keep track of these objects by encapsulating them into an instance of a class. Doing this allows the attributes to never overlap.

Also we can encapsulate methods to be private, public or protected. I personally have not needed to really worry about this or run into using a private method. Basically private methods can be accessed only within the class. Public can be outside the class. Protected methods are a sort of an inbetween of both private in public. It can behave like both depending on where it is used.

**Polymorphism**
Polymorphism is very useful and allows us to give our code unique methods with the same method name. We can even use name fo example. We can have two different classes that have an method called name that displays the name of the class. Both methods will be called the same thing, but will have different displays. This is good an allows us to have flexible code. We can change one of the name methods in one class without it affecting the other method. If we had two similar classes with similar methods the code will start looking pretty repetitive which isn't the wort thing in the world, but it directly leads into the next helpful key concept.

**Inheritance**
Inheritance is a great way to get rid of repetitive code, and can even help the lazy developer to become more lazy. Just an Avi reference haha, but it's very true. Inheritance allows classes to share methods and behaviours. It uses a pyramid structure/tree structure. There is a parent class or superclass which is full of useful methods, our other classes could use. Our subclass(es) will inherit from the parent class. After it has inherited those methods and behaviours we can add other methods to the subclass to make it more unquie. Lets say our parent class is called resturaunt and has all these nice methods for running a resturaunt. Now we have a subclass called pizzeria and it inherits from the parent class, but now we want to add some other methods like a menu for the different types of food.


**Modules**
I like to describe modules as inheritance.......but better. Haha, but seriously it is basically inheritance, we will get all the methods from the parent class, but they won't be in our code. What I mean is that if we used a module to get some method/behaviour it wont be in our code directly, but we are allowed to invoke that method on our class. Modules are basically a container of methods where we use the functionality only where it is needed.

**Self**
Ok we are finally at self. Self can get very confusing at times. For a while I was always unsure about what I was reffering too when I called on self. It is actually really easy to figure out what you are going to be reffering too whether its an object/instance of the class or the entire class itself. If we are inside the class and we say self.all, this is a class method and we are referring to the whole class. If we do self.name we are finding just an object or an instance of the class. See it's not that scary.

Well here's my little cheet sheet on these key concepts. Going over them again definitley helped my understanding of OO Ruby. I'd also reccomend rewatching some of those Avi videos on OO Ruby. 

