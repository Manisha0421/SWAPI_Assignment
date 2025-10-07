**Star Wars API (SWAPI) – Postman Test Collection**

**Overview**

This collection includes two API requests designed to test the Star Wars API (SWAPI) — specifically the /people endpoint.
The goal was to create a small but realistic example of API test automation logic in Postman, demonstrating how to validate both a list endpoint and an individual resource dynamically.

**What’s Included**
Collection 1 – GET /people

Request:
https://swapi.dev/api/people/

Purpose:
Validate the structure and data returned by the /people endpoint.

**1. API Request 1 – GET /people/**

**Request:**
https://swapi.dev/api/people/

**Test coverage:**

1. Verifies the HTTP status code is 200 OK
2. Checks that the response body has valid structure (count, next, previous, results)
3. Confirms results is a non-empty array
4. Validates that each character object includes essential keys like:
  name, height, mass, gender, films, vehicles, starships, and url
5. Generates a random character from the list and stores:
personId and personName as collection variables for use in the next request

**2️. API Request 2 – GET /people/{{personId}}**

**Request:**
https://swapi.dev/api/people/{{personId}}

**Purpose:**
Dynamically fetch and validate details of a randomly selected character from the first request.

**Test coverage:**

1. Verifies the response status code (200 OK)
2. Asserts the character’s name matches the personName variable from the previous call
3. Checks for key attributes: birth_year, gender, and films
4. Ensures the films array is not empty

**How to Run the Tests:**

1. Import the collection into Postman.
2. Go to Postman → Import → select the .json collection file or use the provided link.
3. Run the collection:
4. Open Collection Runner → select the collection → click Run.
5. Both requests will execute in sequence — the first sets the variables, the second uses them.

**View results:**

In the Test Results panel, you’ll see detailed pass/fail outcomes for each validation.

**Expected Behavior**

1. Both requests should return HTTP 200 responses.
2. The first test will print results of structural checks.
3. The second test will verify that the randomly selected character matches correctly between both calls.
4. If the SWAPI service is operational, all tests should pass successfully.

**Tools & Concepts Demonstrated**

1. Postman for API automation
2. JavaScript test scripting via the Postman pm API
3.Use of collection-level variables for dynamic chaining between requests
4.Response validation, data type checks, and array structure assertions
