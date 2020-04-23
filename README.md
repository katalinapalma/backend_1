# Intro:
**https://api.softhouse.rocks** <br>
An API that implements jsonplaceholder post and users endpoints, backed by a mongo database.

The purpose for this API is educational and meant as a step between using jsonplaceholder in a UI and implementing your own API.

# Posts
### The HTTP Methods supported are:
- GET
- POST
- PUT
- PATCH 
- DELETE

### Paths should look like this:
/posts - List of posts <br>
/posts/{postId} - Gets a specific post with Id

### Method: GET

#### Example 1:
```
curl -i -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1
```

Gets the information from the specified URI

**The result will look like this:**<br>
```
{"_id":"5e806d9f42fbde006b6b9ecf","userId":1,"id":1,"title":"sunt aut facere repellat provident occaecati excepturi optio reprehenderit","body":"quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto","__v":0}
```

#### Example 2 with jq and {postId}:
```
curl http://api.softhouse.rocks/posts/1 | jq .
```

Gets the information in the specified URI and displays it in JSON format

**The result will look like this:**<br>
```json
  {
    "_id": "5e9ecdbd3c9c34a2d807ce9d",
    "id": 1,
    "__v": 0,
    "body": "string",
    "title": "string",
    "userId": 1
  }
```

### Method: POST
#### Example 1:
```
curl -i -X POST -H "Content-Type:application/json" http://api.softhouse.rocks/posts -d '{"title":"Hi, World", "body":"Fresh as morning dew", "userId": "1"}' 
```

Posts the information you give to the Object

**The result will look like this:**<br>
```
{"_id":"5e9eb17e09cee0002106f314","body":"Fresh as morning dew","title":"Hi, World","userId":1,"id":811,"__v":0}
```

#### Example 2 with jq:
```json
{
  "_id": "5e9eadf3a8eb15002609e47b",
  "body": "Fresh as morning dew",
  "title": "Hi, World",
  "userId": 1,
  "id": 807,
  "__v": 0
}
```

### Method: PUT
#### Example 1<br>
```
curl -i -X PUT http://api.softhouse.rocks/posts/3 -H "Content-Type:application/json" -d  '{
  "body": "NewBody", "title": "NewTitle", "userId": "1337"}'
```

  Replaces the information on the specified path, with the provided data

#### Result:
```
Status: 200 OK
```
Returns body with the old information, should look like this
```
{"_id":"5e9ed8353c9c34a2d807f465","id":3,"__v":0,"body":"OldBody","title":"OldTitle","userId":13}
```

With jq:
```json
{
  "_id": "5ea14af48e9e2e7dc0da885c",
  "id": 3,
  "__v": 0,
  "body": "NewBody",
  "title": "NewTitle",
  "userId": 1337
}
```


### Method: PATCH
#### Example: <br>
```
curl -i -X PATCH http://api.softhouse.rocks/posts/3 -H "Content-Type:application/json" -d  '{
  "body": "newBody", "userId": "3"}'
```
  Updates a part of the object on the specified path, depending on the provided data

#### Result:
```
Status: 200 OK
```
Returns body with the updated information

```
{"body": "newBody", "title": "oldTitle", userId": "3"}
```

### Method: DELETE

#### Example:
```
curl -i -X DELETE http://api.softhouse.rocks/posts/1
```

Deletes an object or endpoint at the specified path

#### Result:
```
Status: 
200 OK - Path found, was deleted

204 No Content - Path not found, nothing changed
```

# Users
### The HTTP Methods supported are:
- GET
- POST
- PUT - Must have specific user Id

### Paths should look like this:
/users - List of users <br>
/users/{userId} - Gets a specific user with users Id


### Method: GET 
#### Example 1:
```
curl -i -H "Content-Type:application/json" http://api.softhouse.rocks/users/1
```
Gets the information from the specified URI.

#### Result will look like this:<br>
```
{"address":{"geo":{"lat":-37.3159,"lng":81.1496},"street":"Kulas Light","suite":"Apt. 556","city":"Gwenborough","zipcode":"92998-3874"},"_id":"5e806d9f42fbde006b6b9ec5","id":1,"name":"Leanne Graham","username":"Bret","email":"Sincere@april.biz","__v":0}
```

#### Example 2 with jq:
```
curl -X GET http://api.softhouse.rocks/users/1 | jq .<br>
```

```json
{
  "address": {
    "geo": {
      "lat": -37.3159,
      "lng": 81.1496
    },
    "street": "Kulas Light",
    "suite": "Apt. 556",
    "city": "Gwenborough",
    "zipcode": "92998-3874"
  },
  "_id": "5e806d9f42fbde006b6b9ec5",
  "id": 1,
  "name": "Leanne Graham",
  "username": "Bret",
  "email": "Sincere@april.biz",
  "__v": 0
}
```
Gets the information in the specified URI and displays it in JSON format.

