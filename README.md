

## Cryptography Resources

### The Bcrypt Gem

We are using the Bcrypt gem in our application to store encrypted passwords AND to confirm that a user is submitting the correct password when they sign in. BUT Bcrypt cannot do this through decryption - the Bcrypt gem can't decrypt a password_hash back into the original password. So how does it actually work?

How do we check for equality between two values in Ruby? With a `==`.

The creators of Bcrypt took advantage of that convention and Ruby’s syntactic sugar and wrote a method called `def ==(secret)`.

So when we compare the stored password_hash to a password from a sign in form like this:

```ruby
  @user.password == params[:password]
```
what we are actually doing is calling the `def ==(secret)` method like this:

```ruby
  @user.password==(params[:password]) 
```
This `def ==(secret)` method takes `params[:password]` (the password that a user submitted when signing in), runs it through the hashing algorithm to create a hash, and compares this new hash to the password_hash. If they match, `def ==(secret)` returns true.

Pretty cool, huh? 

You can take a closer look at `def ==(secret)` in the [Bcrypt gem](https://github.com/codahale/bcrypt-ruby) under: `bcrypt-ruby/lib/bcrypt/password.rb`.

Check out the "More Information" section of the Bcrypt README for links to more technical explanations of how Bcrypt works.

### Public Key Cryptography

Every time you push your code up to Github you are taking advantage of public key cryptography. Check out this video for an explanation on how that works: https://www.youtube.com/watch?v=3QnD2c4Xovk&feature=plcp

### Learn More About Cryptography

Like the style of that last video? Check out Brit Cruise's [Cryptography course on Kahn Academy](https://www.khanacademy.org/computing/computer-science/cryptography). 

You can get a full history of cryptography by starting at [Ancient Cryptography](https://www.khanacademy.org/computing/computer-science/cryptography/crypt/v/intro-to-cryptography) section.

Or take the fast track to understanding how public key cryptography works with [Modern Cryptography](https://www.khanacademy.org/computing/computer-science/cryptography/modern-crypt/v/the-fundamental-theorem-of-arithmetic-1).
