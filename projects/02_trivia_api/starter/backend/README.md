# Backend - Full Stack Trivia API

### Installing Dependencies for the Backend

1. **Python 3.7** - Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)


2. **Virtual Enviornment** - We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)


3. **PIP Dependencies** - Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:
```bash
pip install -r requirements.txt
```
This will install all of the required packages we selected within the `requirements.txt` file.


4. **Key Dependencies**
 - [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

 - [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py.

 - [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server.

### Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

### Running the server

From within the `./src` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.

## ToDo Tasks
These are the files you'd want to edit in the backend:

1. *./backend/flaskr/`__init__.py`*
2. *./backend/test_flaskr.py*


One note before you delve into your tasks: for each endpoint, you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior.

1. Use Flask-CORS to enable cross-domain requests and set response headers.


2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories.


3. Create an endpoint to handle GET requests for all available categories.


4. Create an endpoint to DELETE question using a question ID.


5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score.


6. Create a POST endpoint to get questions based on category.


7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question.


8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions.


9. Create error handlers for all expected errors including 400, 404, 422 and 500.



## Review Comment to the Students
```
This README is missing documentation of your endpoints. Below is an example for your endpoint to get all categories. Please use it as a reference for creating your documentation and resubmit your code.

Endpoints
GET '/api/v1.0/categories'
GET ...
POST ...
DELETE ...

GET '/api/v1.0/categories'
- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Arguments: None
- Returns: An object with a single key, categories, that contains a object of id: category_string key:value pairs.
{'1' : "Science",
'2' : "Art",
'3' : "Geography",
'4' : "History",
'5' : "Entertainment",
'6' : "Sports"}

```


## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
# API Reference
## Getting Started

-   Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, `http://127.0.0.1:5000/`, which is set as a proxy in the frontend configuration.
-   Authentication: This version of the application does not require authentication or API keys.

## Error Handling

Errors are returned as JSON objects in the following format:

```
{
    "success": False,
    "error": 400,
    "message": "bad request"
}
```

The API will return four error types when requests fail:

-   400: Bad Request
-   404: Resource Not Found
-   422: Unprocessable
-   505: Internal Server Error

## Endpoints
#### GET /categories
- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Arguments: None
- Returns: An object with a single key, categories, containing object of id: category_string pairs
- `curl http://127.0.0.1:5000/categories`
```
{
 "categories": {
 "1": "Science",
 "2": "Art",
 "3": "Geography",
 "4": "History",
 "5": "Entertainment",
 "6": "Sports"
 }
}
```
#### GET /questions
- Fetches a list of questions objects, total number of questions, all categories, and current category
- Request Arguments: page - integer
- Returns: An objects with questions (maximum 10 per page), number of total questions, all the categories, and current category
- `curl http://127.0.0.1:5000/questions`
```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "current_category": null,
  "questions": [
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    },
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }
  ],
  "total_questions": 19
}
```
#### GET /categories/{category_id}/questions
- Fetches a list of questions objects for a category specified by an id, total number of questions, and current category
- Request Arguments: category_id - integer
- Returns: An objects with questions for the specified categoy (maximum 10 per page), number of total questions, and current category
- `curl http://127.0.0.1:5000/categories/6/questions`
```
{
  "current_category": "Sports",
  "questions": [
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    }
  ],
  "total_questions": 19
}
```
#### DELETE /questions/{question_id}
- Deletes a specified question using the id of the question
- Request Arguments: question_id - integer
- Returns: object with a success message and id of the deleted question
- `curl -X DELETE http://127.0.0.1:5000/questions/2`
```
{
  "deleted": 2,
  "success": true
}
```
#### POST /questions
- Creates a new question using the submitted question, answer, difficulty, and category
- Request Body:
```
{
    'question':  'Heres a new question string?',
    'answer':  'Heres a new answer string',
    'difficulty': 1,
    'category': 3,
}
```
- Returns: object with a success message and id of the added question
- `curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d '{"question":"Heres a new question string?", "answer":"Heres a new answer string", "difficulty":"1", "category": 3}'`
```
{
  "question_id": 24,
  "success": true
}
```
#### POST /questions
- Sends a post request to search for a specific question by a search term and then fetches a list of questions objects matching the search
- Request Body:
```
{
    "searchTerm": "some user inputted search text"
}
```
- Returns: an array of questions, number of total questions matching the search term, and a success message
- `curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d '{"searchTerm":"title"}'`
```
{
  "questions": [
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    }
  ],
  "success": true,
  "total_questions": 2
}
```
#### POST /quizzes
- Sends a post request in order to get the next question in the quiz or to end the quiz if all the questions have been tested
- Request Body:
	- an array of question id's
	- object for quiz_category
```
{
		previous_questions: [],
		quiz_category: {
			type: "click",
			id: 0
		}
}
```
- Returns: a single new question object
- `curl http://127.0.0.1:5000/quizzes -X POST -H "Content-Type: application/json" -d '{"previous_questions": [20, 22], "quiz_category": {"type": "Science", "id": "1"}}'`
```
{
  "question": {
    "answer": "Alexander Fleming",
    "category": 1,
    "difficulty": 3,
    "id": 21,
    "question": "Who discovered penicillin?"
  }
}
```
## Authors
Ben Resnick, Udacity student.
## Acknowledgements
The great staff and course at Udacity, mostly Ananta K and Mostafa E for [guidance](https://knowledge.udacity.com/questions/684367) in how to end my quizzes in the mentor section
