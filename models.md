#Models

Rails models have attributes. These are the ones that we define with the generators, which are actually the ones that are stored at the database and that we can check at the Schema file or with `self.attribute_names`. Each of them has an `attr_accessor`, so getters and setters methods, like self.my_attribute="bla" or a=self.my_attribute.
Notice however that even having an `attr_accessor` of something will not generate the instance variable until the method is called. So this is lazy done.
Of course, attr_accessors can also be declared like `attr_accessor :remember_token`, but this does not mean that they belong to the model's attributes


##Creating

Create a user and save it, the parenthesis are default values

```
user = User.new(name: "Michael Hartl", email: "mhartl@example.com")
user.save
```

This can be done in a single step

`User.create(name: "A Nother", email: "another@example.org")`

The `create!` method is just like the `create` method, except it raises an exception for an invalid user rather than returning false. This behavior makes debugging easier by avoiding silent errors.

Erros can be checked with

`user.errors.full_messages`

##Retrieving 
- Find a user `User.find(1)`
- Find by attribute `User.find_by(email: "mhartl@example.com")`
- Find where. Using sql,the ? is super important since it perfomrs escaping
	
	```
	User.where(:country => 'canada')
	User.where("user_id IN (?) OR user_id = ?", following_ids, id)
	```
- Count `User.count`

######DATES
 - Event.where(:date => Date.today..Date.tomorrow)
 - Event.where(:date > ?, Date.today)	

##Updating
```
user.name = "John"
user.save
```
Or

```user.update_attribute(:name, "John")```

Or to update several attributes

```user.update_attributes(name: "The Dude", email: "dude@abides.org")```

IMPORTANT! `update_attributes` performs validation whereas `update_attribute` doesn't

Reload values from the database `user.reload.name`

##Associations
```
rails generate model Micropost content:text user:references
```
Then, at Micropost.rb `belongs_to :user`

At user.rb `has_many :micropost`

Having one user several microposts:

- `micropost.user`Returns the User object associated with the micropost
- `user.microposts` Returns a collection of the user's microposts
- `user.microposts.create(arg)` Creates a micropost associated with user
- `user.microposts.create!(arg)` Creates a micropost associated with user (exception on failure)
- `user.microposts.build(arg)` Returns a new Micropost object associated with user
- `user.microposts.find_by(id: 1)` Finds the micropost with id 1 and user_id equal to user.id

Destory dependencies can be added:
`has_many :microposts, dependent: :destroy`


##Advanced associations

`has_many :microposts` works because by convention Rails looks for a `Micropost` model corresponding to the `:microposts` symbol. But what if we wanted to use another name?. We can then indicate what class the relation is referencing to:

```
 rails generate model Relationship follower_id:integer followed_id:integer
 class User < ActiveRecord::Base
 	has_many :active_relationships, class_name:  "Relationship",
                                  foreign_key: "follower_id",
 end

 class Relationship < ActiveRecord::Base
  	belongs_to :follower, class_name: "User"
  	belongs_to :followed, class_name: "User"
 end

```
Notice that by default, Rails expects a foreign key of the form `<class>_id`, where `<class>` is the lower-case version of the class name. If this is not the case, the foreign_key needs to be indicated too
It is also possible to get information through a relation
`has_many :following, through: :active_relationships, source: :followed`

##Polymorphism
At the model

```
class Shout
  belongs_to :content, polymorphic: true
end
```
At the controller

```
  def create
    content = TextShout.new(text_shout_parameters)
    shout = current_user.shouts.build(content: content)
    shout.save
  end
```

View

We then render a parial, that will render the correct model of the polymorphism
`<%= render shout.content %>`
