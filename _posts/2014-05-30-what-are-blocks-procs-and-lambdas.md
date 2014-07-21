---
layout: post
title: "What are Blocks, Procs, and Lambdas?"
description: "Understanding and using Ruby blocks, procs and lambdas."
modified: 2014-06-13 16:38:12 -0700
tags: [technical, ruby, code, phase 0]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

As we learn more about Ruby as a programming language, we get to explore the many ways in which we can interact with, alter and change objects. Three dynamic and useful tools towards that end are blocks, Procs and lambdas. Let’s learn a little about each and how we can utilize them in our code.

### Blocks

You can think of blocks as useful little add-ons that interact with certain methods. They are especially useful when iterating using methods like #each or #times. They are also key to the success of methods like #collect and #select. Blocks can be built using either `do…end` syntax or more commonly, the `{ }` syntax.

{% highlight ruby %}
nums = *1...10

doubled = nums.collect do |i|
           i * 2
         end

evens = nums.select {|i| i % 2 == 0}

p nums     # => [1, 2, 3, 4, 5, 6, 7, 8, 9]
p doubled  # => [2, 4, 6, 8, 10, 12, 14, 16, 18]
p evens    # => [2, 4, 6, 8]
{% endhighlight %}

### Procs

In Ruby, almost everything is an object. One of the few exceptions to that rule are blocks. They aren’t objects and as such have a limited function. They aren’t embedded with all the powers and abilities of objects. Also, if you plan on using the same block more than once, you’ll need to retype it again and again. Here’s where Procs come in. Procs are objects and as such, can be used to convert our little blocks into more powerful objects that can be used over and over.

{% highlight ruby %}
ones = *1...10
tens = *10...20
twenties = *20...30

odds = Proc.new {|i| i % 2 !== 0}

odd_ones = ones.select(&odds)
odd_tens = tens.select(&odds)
odd_twenties = twenties.select(&odd)

p odd          # => [1, 2, 3, 4, 5, 6, 7, 8, 9]
p odd_ones     # => [1, 3, 5, 7, 9]

p tens         # => [10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
p odd_tens     # => [11, 13, 15, 17, 19]

p twenties     # => [20, 21, 22, 23, 24, 25, 26, 27, 28, 29]
p odd_twenties # => [21, 23, 25, 27, 29]
{% endhighlight %}

### Lambdas

Much like Procs, lambdas are also objects. They function very similarly to Procs and can sometimes be used interchangeably. They do have one distinct behavior difference that can have an impact on output. When used within a method, a lambda will execute and then pass control back to the calling method. A Proc on the other hand, when executed will do so immediately without going back to the calling method.

{% highlight ruby %}
def who_has_power
  proc_gets = Proc.new { return "I have the power!"}
  proc_gets.call
  "I thought I had it."
end

def now_who_has_power
  lambda_gets = lambda { return "I think I have power."}
  lambda_gets.call
  "Nope, I have the power now!"
end

puts who_has_power     # => I have the power!
puts now_who_has_power # => Nope, I have the power now!
{% endhighlight %}

### Learn More

As you can see, blocks, Procs and lambdas are great tools to add to our Ruby toolbox. They can increase the scope and power of the methods and objects we build. If you want to learn more about them, check out these useful resources.

* [Codecademy - Ruby Track - Blocks, Procs, and Lambdas](http://www.codecademy.com/courses/ruby-beginner-en-L3ZCI/0/1?curriculum_id=5059f8619189a5000201fbcb)
* [Tuts+ Tutorial - Ruby on Rails Study Guide: Blocks, Procs, and Lambdas](http://code.tutsplus.com/tutorials/ruby-on-rails-study-guide-blocks-procs-and-lambdas--net-29811)
* [Rubymonk - Ruby Primer: Ascent - Blocks 0.4 - Blocks, Procs, and Lambdas](http://rubymonk.com/learning/books/4-ruby-primer-ascent/chapters/18-blocks/lessons/64-blocks-procs-lambdas)

They're common elements of many methods and programs. Once you pick up the basic syntax you’ll be coding with blocks, Procs and lambdas too.
