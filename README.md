# did_you_mean [![Gem Version](https://badge.fury.io/rb/did_you_mean.svg)](https://rubygems.org/gems/did_you_mean) [![Build Status](https://travis-ci.org/yuki24/did_you_mean.svg?branch=master)](https://travis-ci.org/yuki24/did_you_mean)

'Did you mean?' experience in Ruby. No, Really.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'did_you_mean', group: [:development, :test]
```

## Examples

### NameError

#### Correcting a Misspelled Method Name

```ruby
class User
  attr_accessor :first_name, :last_name

  def to_s
    "#{f1rst_name} #{last_name}" # f1rst_name ???
  end
end

user.to_s
# => NameError: undefined local variable or method `f1rst_name' for #<User:0x0000000928fad8>
#
#     Did you mean? #first_name
#
```

#### Correcting a Misspelled Class Name

```ruby
class Book
  class TableOfContents
    # ...
  end
end

Book::TableofContents # TableofContents ???
# => NameError: uninitialized constant Book::TableofContents
#
#     Did you mean? Book::TableOfContents
#
```

### NoMethodError

```ruby
# In a Rails controller:
params.with_inddiferent_access
# => NoMethodError: undefined method `with_inddiferent_access' for {}:Hash
#
#     Did you mean? #with_indifferent_access
#
```

### ActiveRecord::UnknownAttributeError

```ruby
User.new(nmee: "wrong flrst name")
# => ActiveRecord::UnknownAttributeError: unknown attribute: nmee
#
#     Did you mean? name: string
#
```

## 'Did You Mean' Experience is Everywhere

_did\_you\_mean_ gem automagically puts method suggestions into the error message. This means you'll have the "Did you mean?" experience almost everywhere:

![Did you mean? on BetterErrors](https://raw2.github.com/yuki24/did_you_mean/master/docs/did_you_mean_example.png)

## Support

_did\_you\_mean_ gem supports the following implementations:

 * MRI 1.9.3, 2.0.0, 2.1.x, 2.2.0-preview1 and ruby-head
 * JRuby (tested against 1.7.16)

Any other implementations are **NOT** supported (Rubinius support is work in progress).

## Contributing

1. Fork it (http://github.com/yuki24/did_you_mean/fork)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License

Copyright (c) 2014 Yuki Nishijima. See MIT-LICENSE for further details.
