#Rails tricks

##Flash
We can use the special method called `flash` to display temporary messages. We can treat flash as a hash. Rails adopts the convention of a :success key for a message indicating a successful result.

`flash[:success] = "Welcome to the Sample App!"`
We can then add to our `application.html.erb` layout a loop to show all the flash contents, adding a css class to each of them

Note that Bootstrap CSS supports styling for four such flash classes (success, info, warning, and danger)

```
<% flash.each do |message_type, message| %> 
<div class="alert alert-<%= message_type %>"><%= message %></div> 
<% end %>
```
Using `flash` makes the message last for a whole request, using `flash.now` only for a render(e.g flash.now[:render]