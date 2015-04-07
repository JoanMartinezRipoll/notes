#Testing

##General
###let, let!, before

- **let:** Executed with lazy loading
    `let(:country) { create(:country) }`
    
- **let!:** Executed in the order they are defined, uses explicit reference to variable(a method)
    `let!(:country) { create(:country) }`
    
- **before(:each)** Executed before each of the tests. Before should be used to define configurations or actions such as `sign_in` or setting up some state for the tests. To deal with objects to which assertions will be made `let!` and `let` are better because they are safer, since instance variables can lead to typos, and ruby will consider them to be null, making the tests fails when they shouldn't.

	```
	before :each do
	  sign_in create(:admin_school)
	end
	```
    
- **before(:all)** Executed one before all tests are run

##Rspec
###Database Cleaner
When using tests that require js, use this DatabaseCleaner config. The problem is that the transaction strategy does not work with non rack_test drivers, because the other drivers create a new thread to simulate the browser and, since transactions are not shared across threads, the data you have put into the database in your test is no accessible.

```
  config.before(:each) do
    if Capybara.current_driver == :rack_test
      DatabaseCleaner.strategy = :transaction
    else
      DatabaseCleaner.strategy = :truncation
    end
    DatabaseCleaner.start
  end
  config.after(:each) do
    DatabaseCleaner.clean
```
###The faker gem

Use the faker gem to generate fake data.
  
 ```
  gem 'faker'
 ```
For example, to generate fake names.

```
  name  = Faker::Name.name
```

###Crazy nested_attributes
```
 foundation_event_attributes = attributes_for(:foundation_event, share_issuer_id: company.id,
          transactions_attributes: [attributes_for(:transaction, shareholder_id: kathi.id, shareholder_type: kathi.name)])
        post :create, company_id: company.id, foundation_event: foundation_event_attributes
```
