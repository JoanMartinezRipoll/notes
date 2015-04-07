#Views

##form_for

When restful and having a controller instance variable,works like:
	
	```
	form_for(@user) do |f|
	<%= f.label :name %>
	<%= f.text_field :name, class: 'form-control' %>
	<%= hidden_field_tag :email, @user.email %>
	```
	
The forms will always call db options like create, delete, patch/put Magic: The same code can be used and `form_for` will now when to do a post or a `put/patch` because it will check if that `@user` exists at the db or not.

The form will call the method (the url) that due to routes.rb will call the controller action. There will then be a parms hash, that will include what the form has added. Whatever that is added to f, will be added to the resource (in this case @user) and will end up like `params[:user][:name]`. If there is no model resource, we need to indicate the resource as a symbol. Like

```
	form_for(:session, url: login_path)
	<%= f.label :name %>
	<%= f.text_field :name, class: 'form-control' %>
```

We would then have params like `params[:session][:name]`


##Collection select
```
  <%= f.label :languages, "Offered languages" %>

  <%= f.collection_select(:language_ids, Language.all, :id, :name,{}, {:multiple => true})  %>
  ```
  
##Select tag
```
  = select_tag :by_attribute, options_for_select([['No', :finalized_at], ['Yes', :created_at]], @captable.filtered_by)
```
