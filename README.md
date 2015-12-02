# The Splat Operator

## Objectives

Understand what the splat operator is and how it is used. 

## What is the Splat Operator?

The `*` (or splat) operator allows a method to take an arbitrary number of arguments and is perfect for situations when you would not know in advance how many arguments will be passed in to a method.  Here's an example:

```ruby
def name_greeting(*names)
  names.each do |name|
    puts "Hello, #{name}!"
  end
end

name_greeting("Happy", "Sleepy", "Dopey", "Bashful")
Hello, Happy!
Hello, Sleepy!
Hello, Dopey!
Hello, Bashful!
=> ["Happy", "Sleepy", "Dopey", "Bashful"]
```

### How does it work?

The splat operater, placed before a parameter in a method signature (as above) tells the method to accept an unlimited number of arguments as an **array**. Let's take a look. We're going to play around with our `name_greeting` method in IRB using Pry. (Yes, you can use Pry inside IRB. Yes, it is awesome.)

* Drop into IRB in your terminal and type the following command `require 'pry'`. You should see a return value of `=> true`. That let's you know that you are able to use Pry. 
* Copy and paste the following method, with the binding.pry in it: 

```ruby
def name_greeting(*names)
  binding.pry
  names.each do |name|
    puts "Hello, #{name}!"
  end
end
```

* Then, call the method with multiple arguments: `name_greeting("Sally", "Bobby")`. You'll be dropped inside the method via your binding.pry. Type `names` into your terminal and you should see the following: 

```ruby
=> ["Sally", "Bobby"]
```

**The `*` has converted your multiple arguments into an array!**

Now, let's try the same method call but with *only one argument*.

* Exit out of your binding by typing `exit` in your terminal. Then, call the method again but this time with only argument: `name_greeting("Sally")`. Once again, you'll be dropped into the method via your binding.pry. Type `names` into your terminal and you should see the following: 

```ruby
=> ["Sally"]
```

The `*` *still* converts the argument into an array, but this time the array has only one element. 

What would happen if we tried to call our method *without any arguments at all?* Let's find out!

* Exit out of your binding and call the method again, this time without any arguments: `name_greeting`. You'll be dropped into your method via the binding. Type `names` into the terminal and you should see the following: 

```ruby
=> []
```

Instead of an ArgumentError, the lack of arguments has simply been converted into an empty array, thanks to the `*` operator. 

### A Note on Usage

You can define a method that takes in a required argument *and*, separately, an undefined number of additional arguments via the splat operator. Let's take a look: 

```ruby
def number_of_greetings(num, *names)
  num.times do 
    names.each do |name|
      puts "Hello, #{name}!"
    end
  end
end
```

We've defined a method that takes in a required argument of a number and an unlimited number of names. The method uses a times loop to puts out a greeting to each person, however many times the method has been told to via the `num` argument. Let's call the method: 

```ruby
number_of_greetings(5, "Sally", "Bobby")

#outputs:

Hello, Sally!
Hello, Bobby!
Hello, Sally!
Hello, Bobby!
Hello, Sally!
Hello, Bobby!
Hello, Sally!
Hello, Bobby!
Hello, Sally!
Hello, Bobby!
```

It is important to note that when defining a method to accept a required argument and splat arguments, you must define the method to *first* accept the required argument and *then* accept the splat arguments. 


## Resources 

* [The Strange Ruby Splat](https://endofline.wordpress.com/2011/01/21/the-strange-ruby-splat/)
<a href='https://learn.co/lessons/splat-readme' data-visibility='hidden'>View this lesson on Learn.co</a>
