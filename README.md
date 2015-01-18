---
tags: cryptography, bcrypt, kids, ruby, advanced, study guide
language: ruby
level: 2
type: study guide
---

## Cryptography Resources

### The Bcrypt Gem

We are using the Bcrypt gem in our application to store encrypted passwords AND also to confirm that a user is submitting the correct password when they sign in. However, Bcrypt cannot do this through decryption - the Bcrypt gem can't decrypt a password_hash back into the original password. So how does it actually work?

How do we check for equality between two values in Ruby? With a `==`.

The creators of Bcrypt took advantage of that convention and Ruby’s syntactic sugar and wrote a method called `def ==(secret)`.

So when we compare the stored password_hash to a password from a sign in form like this:

```ruby
  @user.password == params[:password]
```
what we are actually doing is calling the `def ==(secret)` method like this:

```ruby
  @user.password==(params[:password]). 
```
This `def ==(secret)` method takes params[:password] (the password that a user submitted when signing in), runs it through the hashing algorithm to create a hash, and compares this new hash to the password_hash. If they match, `def ==(secret)` returns true.

Pretty cool, huh? 

You can take a closer look at `def ==(secret)` in the [Bcrypt gem](https://github.com/codahale/bcrypt-ruby) under: `bcrypt-ruby/lib/bcrypt/password.rb`



