This is our high-quality Jokes API. You can use this API to request, add 
and remove different jokes.

### Retrive a Random joke

Retrieve a random joke from all jokes in the database

```endpoint
GET /jokes/random
```

#### Example request

```curl
$ curl http://localhost:3000/jokes/random
```
#### Example response

```json
{
    "id": 5,
    "text": "Why did the manager go to therapy? To work on their control issues.",
    "likes": 0,
    "dislikes": 0
}
```

 ### Retrive a random joke from a category of jokes

Retrieve a random joke from a category of jokes

```endpoint
GET /jokes/random/:category
```

#### Example request

```curl
curl http://localhost:3000/jokes/random/Science jokes
```

#### Example response

```json
{
    "id": 3,
    "text": "Why was the math book sad? Because it had too many problems.",
    "likes": 6,
    "dislikes": 2
}
```

 ### Retrive lists of categories

Retrieve  lists of categories from database

```endpoint
GET /categories
```

#### Example request

```curl
curl http://localhost:3000/categories
```

#### Example response

```json
[
    {
        "id": 1,
        "name": "Programming jokes"
    },
    {
        "id": 2,
        "name": "Science jokes"
    },
    {
        "id": 3,
        "name": "Management Jokes"
    }
]
```
### Retrieve all jokes for a category 

Retrieve all jokes using category name

```endpoint
GET /jokes/:category
```

#### Example request

```curl
curl http://localhost:3000/jokes/Programming jokes
```

#### Example response

```json
    [
    {
        "id": 1,
        "text": "Why did the programmer quit his job? Because he didn't get arrays",
        "likes": 0,
        "dislikes": 0
    },
    {
        "id": 2,
        "text": "Why do Java developers wear glasses? Because they can't C#",
        "likes": 0,
        "dislikes": 0
    }
]
```

### Joke by ID

Retrive a joke by ID

```endpoint
GET /joke/:id
```

#### Example request joke by ID

```curl
curl http://localhost:3000/joke/1
```

#### Example response

```json
{
    "id": 1,
    "text": "Why did the programmer quit his job? Because he didn't get arrays",
    "likes": 0,
    "dislikes": 0
}
```

### Add a new category of joke

 

```endpoint
POST /categories
```

#### Example request

```curl
curl -X POST -H "Content-Type: application/json" -d "{ \"name\": \"Dad_jokes\" }" http://localhost:3000/api/categories

```

#### Example request body

```json
{
    "name": "Dad_jokes"
}
```

#### Example response

```json
{
  "id": 6,
  "message": "Category added successfully"
}
```

### Add a new joke to a category

```endpoint
POST /jokes/:category
```

#### Example request

```curl
curl -X POST -H "Content-Type: application/json" -d "{ \"text\": \"Your Joke.\" }" http://localhost:3000/jokes/Dad_jokes

```

#### Example request body

```json
{
    "category": "Dad_jokes",
    "joke_text": "Your Joke"
}
```

#### Example response

```json
{
  "id": 13,
  "message": "Joke added successfully"
}
```

### Add existing joke to a category by joke id

Add an existing joke to a category by joke id 

```endpoint
POST /joke/:id/category/:category
```

#### Example request

```curl
curl -X POST http://localhost:3000/jokes/1/categories/Dad_jokes

```
#### Example request body

```json
{
    "id":1,
    "category": "Dad_jokes"
    
}
```


#### Example response

```json
{
  "id": 14,
  "message": "Joke copied to new category successfully"
}
```

### Give a like or dislike


```endpoint
POST /joke/:id/:type
```

#### Example request for Like

```curl
curl -X POST -H "Content-Type: application/json" -d "{ \"type\": \"like\" }" http://localhost:3000/api/jokes/5/vote
```
#### Example response for like

```json
{
  "message": "Successfully voted like for joke 5"
}
```
#### Example request for dislike

```curl
curl -X POST -H "Content-Type: application/json" -d "{ \"type\": \"dislike\" }" http://localhost:3
000/api/jokes/9/vote
```
#### Example response for dislike

```json
{
  "message": "Successfully voted disike for joke 9"
}
```