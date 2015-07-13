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

## Resources 

* [The Strange Ruby Splat](https://endofline.wordpress.com/2011/01/21/the-strange-ruby-splat/)