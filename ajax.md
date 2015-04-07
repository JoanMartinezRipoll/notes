#Ajax in Rails

##Perform an AJAX call
 Use jquery that calls a .json controller action with a json response
 
##Submitting a form asynchronously
1. Use `remote=> true` in the form to send the data asynchronously and `respond_to js` in the controller to determine the response.

2. completely use [jquery](https://api.jquery.com/serialize/) and let `jquery` call a `.json` controller action.
`serialize` is usefull to serialize the form's attributes.
```
$( "form" ).on( "submit", function( event ) {
  event.preventDefault();
  console.log( $( this ).serialize() );
  $.post( "test.php", { name: "John", time: "2pm" } );
});
```

##Call a controller and use the response in js

1. Use `remote=> true` in the form and provide the controller action with a `.js.erb` response.
2. Completely use jquery and get the `.json` response in the callback function

```
$.get("/countries.json", function(data) {
```

##Testing 
Use `xhr` to call a controller through ajax
	```
	xhr :post, relationships_path, followed_id: @other.id
	```
	
