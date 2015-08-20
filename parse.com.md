# Passing User object to the REST API

Query by user object (rather then ID) via rest API from command line with curl

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

# Parse hacker terminal layout

Parse develop command line sucks for 2 reasons: It tends to get stuck and it will swollow syntax errors. So the work around is to use 2 terminal windows. 3 if you're commiting as well.

###### main screen 
 ```bash
 parse log -l ERROR -f
 ```
 
###### lower left
 
zig zag between these 2:
 1. ```git commit -a -m"....."; git push```
 2. 
```bash
curl -X POST  \
 -H "X-Parse-Application-Id: <<<>>>" \
 -H "X-Parse-REST-API-Key: <<<>>>" \
 -H "Content-Type: application/json" \
 -d '{ "sourceId": "jQsulDGk8Z" }' \
 https://api.parse.com/1/functions/nearby | python -m json.tool
```

###### lower right 
```bash
while `true`; do sleep 0.5; parse deploy; if [ $? -ne 0 ]; then sleep 10; fi; done
```

![parse.com iTerm setup](https://raw.githubusercontent.com/maximveksler/null/master/parse.com/iTerm.png)
