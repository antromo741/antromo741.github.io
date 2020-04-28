---
layout: post
title:      "Instance Methods Vs Class Methods"
date:       2020-04-28 16:19:59 +0000
permalink:  instance_methods_vs_class_methods
---

When working with instance methods I would always get them confused with class methods. I also didn't understand what was actually happening when I would use an instance method. First off let me give an example of an istance method.
This would look something like

class cats

def useful_method
       self
 end
end

This an instance method and here self would be reffering to an instance of the cats class. 
An example of a class method would look something like

class cats 

@@all= []

def self.all
      @@all
 end
end
This is a class method. Anytime we have def self.something, we are usually looking at a class method. This could not work outside of the class if used, as self would have nothing to refer back to. Also in this case self refers to the whole class.

Now when working with instance methods its always good to go into the irb and check the object we just instantiated. I found this to be very helpful, because it really helped me see the difference between the the class method and the instance method. When we do a class method it is displaying something from the class that is already stored. Like listing all the objects in the class. When we use an instance method we get an instance of the class that gets stored to that object. In that instance the data gets stored to the object as I jst said, but If there is no save method, than that instance of the object will not be stored. Also a class method cannot be called on an instance of the class. These are just how the class and instance methods behave. It is good to understand the small framework of whats going on inside of the code.


