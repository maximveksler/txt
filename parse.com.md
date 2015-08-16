### Query user object via rest API from command line

```javascript
/*
http://www.parse.com/docs/js/api/symbols/Parse.Cloud.FunctionRequest.html

curl -X POST  \
 -H "X-Parse-Application-Id: <<yours-truly>>" \
 -H "X-Parse-REST-API-Key: <<not-today>>" \
 -H "Content-Type: application/json" \
 -d '{ "user": {"__type":"Pointer","className":"_User","objectId":"6NZ1q2uTyG"} }' \
 https://api.parse.com/1/functions/nearby
*/ 

Parse.Cloud.define("nearby", function(request, response) {
	var currentUser = request.params.user

	currentUser.fetch({
	           success: function(fetchedUser) {
				   response.success(JSON.stringify(fetchedUser))
	           },
	           error: function() {
	               console.log("and.. it's gone");
	           }
	       });
})
```
