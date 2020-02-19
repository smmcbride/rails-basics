# Ruby and Rails
Rails is a web framework written in the Ruby language. Ruby is a very extensible 
language and Rails takes advantage of this extensibility so it can be confusing
when first approaching Ruby on Rails to figure out where the Ruby language ends
and the Rails framework begins.

The following example demonstrates one of these extensions to the Array class:

#### Rails Console
```
Loading development environment (Rails 6.0.2.1)
irb(main):001:0> [1,2,3.4].first
=> 1
irb(main):002:0> [1,2,3.4].second
=> 2
irb(main):003:0>
```

#### Ruby Console
```
root@a663e02f70a8:/app# irb
irb(main):001:0> [1,2,3,4].first
=> 1
irb(main):002:0> [1,2,3,4].second
Traceback (most recent call last):
        4: from /usr/local/bin/irb:23:in `<main>'
        3: from /usr/local/bin/irb:23:in `load'
        2: from /usr/local/lib/ruby/gems/2.6.0/gems/irb-1.0.0/exe/irb:11:in `<top (required)>'
        1: from (irb):2
NoMethodError (undefined method `second' for [1, 2, 3, 4]:Array)
Did you mean?  send
irb(main):003:0>
```

The Rails core extensions to Ruby are collected in the `ActiveSupport` library and can be browsed on GitHub  
https://github.com/rails/rails/tree/master/activesupport/lib/active_support/core_ext

Rails provides excellent documentation for the core extensions on it's website:
https://guides.rubyonrails.org/active_support_core_extensions.html

<details>
  <summary>Example</summary>
  <pre>
    long console output here
  </pre>
</details>
   
   
#### Monkey-Patching
Monkey patching is the term used to describe adding functionality to classes in ruby by re-opening them and
defining new methods. It's generally regarded as a bad idea without good reason, but it *is* the primary way 
many of the Rails Core Extensions are added.  The following is an example of adding a new method, `shout!`
to the `String` class:
```
irb(main):001:0> greeting = 'hello'
=> "hello"
irb(main):002:0> greeting.shout!

Traceback (most recent call last):
        4: from /usr/local/bin/irb:23:in `<main>'
        3: from /usr/local/bin/irb:23:in `load'
        2: from /usr/local/lib/ruby/gems/2.6.0/gems/irb-1.0.0/exe/irb:11:in `<top (required)>'
        1: from (irb):2
NoMethodError (undefined method `shout!' for "hello":String)

irb(main):003:0> class String
irb(main):004:1>   def shout!
irb(main):005:2>     "#{upcase}!"
irb(main):006:2>   end
irb(main):007:1> end
=> :shout!
irb(main):008:0> greeting.shout!

=> "HELLO!"
```

---

# Migrations (Schemas) and Models

Migrations are where we define updates to the structure of our database. ActiveRecord Models are the entities
we use to communicate with our database. 

The `schema.rb` file tracks the current state of the project's database structure.  It does not
yet exist on a new project and will be created after the first migration.  This file is auto-generated
by Rails so do not make any hand-edits or they will be lost by future migrations.

When first approaching Ruby on Rails as a frontend developer it can be helpful to think of the Model as the 
frontend and the database as the backend. Both Models and databases have their own configurations and constraints 
and it can be important to keep them both in mind, just as we might have form validation in a UI to prevent 
sending known-bad data to an API.

When your application is running on a distributed system where code deployments take time to 
propagate to all servers, and database migrations happen independently,  it becomes critical 
to deploy database migrations and associated code updates separately to prevent either system
from relying on changes made to the other.  This will often force a relatively simple update 
to be broken down into multiple deployments.

Rails provides extensive documentation on Migrations at it's website:
https://edgeguides.rubyonrails.org/active_record_migrations.html


# Exercises

Run `rake db:migrate` from the api container to execute the existing migrations.  Explore the `db/migrations`
folder to get an idea of the general structure of migration files. These migrations have several problems
that will be explored in the exercises.


