# Sample Spring Boot Service Learning Path

### Summary
This project is intended to help bring a new software engineer up to speed with the current tech stack and implementations of team Motion's platform services.
The exercise will help you become familiar with
1. How to write a spring boot application to service incoming REST requests
2. Usage of spring boot patterns and practices
3. Organization of code in the project
4. Familiarization with data access to postgres DB and Flyway
5. Writing of unit, functional, and integration tests

### Objective
This application should contain the 3 REST API endpoints defined in [Tasks](#tasks). When the application starts, a docker container will start that will 
contain the DB with all the mocked information you need to use

### How to run application
This app and it's database are dockerized and is started by running `docker compose up` which starts the application, creates a postgres db, runs the flyway scripts,
and load sample data. Running `docker compose down -v --remove-orphans` will shut all the containers. The docker images are isolated so you don't have to worry about getting the right version of dependencies and any previous state.

NOTE: The application will not work if your ports 8080 and 8888 are being used. You can update your ports in the docker-compose.yml file.

### Tasks
Your goal in this exercise is to make this application fully functional by adding the 3 REST API endpoints defined below. These endpoints will need to access data through the defined postgres DB, apply some business logic, and return a response as defined below. There is no right or wrong approach to completing the application. Feel free to include any new dependencies and files or delete existing ones. The current structure is merely a guide.

### Guide

Step 0: Validate application starts
  - run 'docker compose up' and validate that http://localhost:8080/version returns 'test'

Step 1: Complete DAO layer
  - Write queries to retrieve the relevant information from the DB
  - Map the DB response to a Model Class

Step 2: Complete Controllers layer
  - Write controller logic to pull require data from API url
  - Validate the params
  - Return response

Step 3: Complete Service layer
  - Grab the data model returned from DAO layer
  - Apply business logic
  - Shape response to what is expected
  - Handle any errors

Step 4: Test Functionality
  - Use postman to test your APIs
  - *Optional* Add swagger UI functionality

Step 5: Write Tests
  - Write unit tests for each of your layers
  - *Optional* Achieve 80% unit test coverage
  - Write a functional test to test each of the endpoints
  - Write a integration test to test your DB queries

Step 6: Better Practices
  - Add logging to capture code path and errors
  - Determine which errors needs to be handled (404, 500, etc)
  - Make code more readable: use Java libraries+builtin functionality, move code to classes which is in it's area of responsibilty
  - Add documentation to your classes



GET /sellerId/{sellerId}/products/{productId}/taxonomy RESPONSE: endpoint1.json

GET /sellerId/{sellerId}/products/{productId}/details RESPONSE: endpoint2.json

