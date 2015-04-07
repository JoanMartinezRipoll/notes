#Commands
##Rails

###Create a new app
`rails new ProjectName` or

`rails new ProjectName -d mysql` to add a mysql database (database.yml must then be changed too)

###Generate a scaffold

`rails generate scaffold User name:string email:string`

A scaffold generates your model, views, controller, and writes to your routes.rb file. It does this for all the CRUD actions 
###Generate a controller

`rails generate controller Welcome index`
 
The possible actions are index show new edit create update destroy and if we write them, views are too generated(which we might not desire)

###Generate a model
`rails generate model Article title:string text:text book:references`

###Generate a mailer

`rails generate mailer UserMailer account_activation password_reset`
###Destroy a generation

If a previous db migrate was done, frist do

 `rake db:rollback`, then
 
  `rails destroy scaffold HighScore game:string score:integer`
  
NOTE: This does not remove all files, such as the app/assets/stylesheets/scaffolds.scss file!

###Generate a migration
######Indexes
 `rails generate migration addEmailIndexToUsers`
 
This generates a file containing `add_index :users, :email, unique: true`   

######Attributes
`rails generate migration addPasswordDigestToUsers password_digest:string`
This adds the `password_digest` attribute to the `user` model (and db), it is convenient to end the name with toUsers, since in this case Rails automatically constructs a migration to add columns to the users table.

###Environments
`rails console {test | production| development }`to start the rails console for the test, production or development environment

`rails server --environment production`to start the server with the production environment

`rake db:migrate RAILS_ENV=production` to migrate to the production environment

##Writting a gem
- `bundle gem hola`
- `gem build hola.gemspec`
- `gem install ./hola-0.0.0.gem`

##Rake

- `rake -T` See all rake commands 
- `rake routes` See the application routes
- `rake db:migrate` Migrate generated migration files

######Reverting database migrations

- `db:rollback` Undo a single migration step, this can be called several times
- `rake db:migrate VERSION=0` Go to a specific version, e.g. the begginig. The migration number is the one at the migration folder 

######Recreating the DB
- `rake db:reset` 
- `rake db:drop db:create db:migrate db:seed` 
- `db:setup does db:create, db:schema:load, db:seed`
- `rake db:migrate:reset`

##Heroku
- `git push heroku master` push to heroku
- `heroku restart -a refactorlicious` restart app
- `heroku apps:rename refactorlicious` rename app
- `heroku apps:info` info of your apps
- `heroku run rake db:migrate` or any other rake/rails command
- `heroku logs` check the logs
