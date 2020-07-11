Udacity Full Stack Developer Nanodegree Capstone Project
Motivation
Create a back-end application which demonstrates the functinality of endpoints with Role Based Access tests. To implement that JWT authentication has been included in the project and current JWT's has been provided for testing. The motivation for this project is to demonstrate skills in combining the use of authorization tools, RBAC endpoints, error handling, test writing and handling data between the front and back-end of the application.

Coding standards: PEP8 compliant code
Authorization: RBAC roles and JWT is implemented by the 3rd party Auth0.
Testing: Comprehensive RBAC and error handling has been implemented as part of the test-driven development process.
Documentation: Setup instructions and endpoints has been documented.
Deployment: The final code is deployed on Heroku and tests can be run agains its database.
This project is for a movie agency which has movies and actors listed in its database. There are two roles, Casting Assistant and Casting Director. For viewing the list of movies and actors in the database the user shoul be logged with the Casting Assistant role. To add, delete and modify movies the role of the user has to be Casting Director.

Setup and dependencies
This project is based on Python3, pip and psql. Please make sure these are pre-installed on your system. To start the project create a virtual environment in the downloaded project folder with the following bash commands:

python3 -m venv env
source env/bin/activate
Following this install the required packages, PIP dependencies by running:

pip install -r requirements.txt
There are environment variables such as JWT codes and the database URL are stored in the setup.sh file. Before running the test file execute:

source setup.sh
Following this the application endpoints are ready to be tested with the deployed server by running:

python3 test_app.py
The deployed application can be found here:

https://fsnd-capstone-elp.herokuapp.com/

Note: If the existing JWT's are expired new ones could be obtained by following the link on the application homepage. For the Casting Director JWT please log in with the following credentials:

Athentication:
To login, use the route: 

'/login'
For executive_director account use the following account:
Username: aughr063@uottawa.ca 
Password: Adil1234! 


You'll be redirected to the main page where the JWT can be copied from the URL after the # part. Paste the JWT into the setup.sh into the CA_TOKEN and CD_TOKEN variables accordingly.

Key Dependencies
Flask is a lightweight backend microservices framework. Flask is required to handle requests and responses.

SQLAlchemy is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py.

Flask-CORS is the extension we'll use to handle cross origin requests from our frontend server.

Avaible Endpoints
In order to play the game, a number of operations take place, each one of them belong to a specific endpoint. The available operations are:

/
GET movies
GET actors
POST movies
POST actors
PATCH movies
PATCH actors
DELETE movies
DELETE actors
'/'

This is the main page of the application, it displays a link to log in and generate new JWT tokens.

GET '/movies'

This endpoint fetches all movies.

Request Arguments:

None
Returns: The return should include an success: True message along with a list of movies in JSON format.

{
  'success': True,
  'movies': formatted_movies
}
GET '/actors'

This endpoint fetches all actors.

Request Arguments:

None
Returns: The return should include an success: True message along with a list of movies in JSON format.

{
  'success': True,
  'actors': formatted_actors
}

POST '/movies'

This endpoint allows you to POST a movie.

Request Arguments:

A JSON object containing the title and the release date:

{
  'title': 'title',
  'release_date': 'release_date'
}
Returns: If there are no errors the following JSON data will be returned:

{
  'success': True,
  'movie': 'movie.format()'
}

POST '/actors'

This endpoint allows you to POST a movie.

Request Arguments:

A JSON object containing the name, age and the gender:

{
  'name': 'name',
  'age': 'age',
  'gender': 'gender
}
Returns: If there are no errors the following JSON data will be returned:

{
  'success': True,
  'actor': 'actor.format()'
}

PATCH '/movies/"id"'

This endpoint allows you to PATCH an existing movie.

Request Arguments:

A JSON object containing the title and the release date:

{
  'title': 'title',
  'release_date': 'release_date'
}

{
  'success': True,
  'movies': patched_movie.format()
}

PATCH '/actors/"id"'

This endpoint allows you to PATCH an existing actor.

Request Arguments:

A JSON object containing the name, age and the gender:

{
  'name': 'title',
  'age': 'age',
  'gender': 'gender'
}

{
  'success': True,
  'movies': patched_actor.format()
}


DELETE '/movies/"id"'

This endpoint allows you to delete a movie, based on its id.

Request Arguments:

id (integer) of the movie to delete.
Returns: An object with a success message, the id of the movie deleted.

{
  'success': True,
  'movie_id': str(delete_id)
}

DELETE '/actors/"id"'

This endpoint allows you to delete a movie, based on its id.

Request Arguments:

id (integer) of the movie to delete.
Returns: An object with a success message, the id of the actor deleted.

{
  'success': True,
  'actor_id': str(delete_id)
}



Testing
To run the tests, run

python test_app.py
Available Roles
There are 3 roles and 6 different permissions defined in the Authorization backend for this application

Permissions:
```
'get:movies': Get the list of all movies
'get:actors': Get the list of all actors
'post:movies': Post a new movie
'post:actors': Post a new actor
'patch:movies': Update a movie
'patch:actors': Update a actor
'delete:movies': Delete a movie
'delete:actors': Delete a actor
```
Roles
Casting Assistant
Can list actors and movies.

Casting Director
Can list movies & actors, post actors, update actors, delete actors

Executive Director
Can list movies & actors, post movies & actors, update movies & actors, delete movies & actors
