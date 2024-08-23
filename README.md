# Postman API Testing Framework for Reqres End Points

## Overview

This project involves creating an API testing framework using Postman for the Reqres API. The framework is designed to handle various basic scenarios, including user management operations and authentication processes. The framework is integrated with GitHub Actions for automated execution of the test cases.

## Test Scenarios

The following API endpoints and scenarios were tested:

### User Management
- **List Users**: Verifies the retrieval of a paginated list of users.
- **Single User**: Confirms the retrieval of a single user's data by ID.
- **Single User Not Found**: Validates the response when a user with a non-existent ID is requested.
- **Create User**: Tests the creation of a new user and verifies the returned data.
- **Update User (PUT)**: Checks the full update of an existing user's data.
- **Update User (PATCH)**: Validates the partial update of an existing user's data.
- **Delete User**: Ensures the user is successfully deleted and that the appropriate response is returned.

### Resource Management
- **List <resource>**: Tests the retrieval of a paginated list of resources.
- **Single <resource>**: Confirms the retrieval of a single resource's data by ID.
- **Single <resource> Not Found**: Validates the response when a resource with a non-existent ID is requested.

### Authentication
- **Register - Successful**: Tests successful user registration and the return of a token.
- **Register - Unsuccessful**: Validates the response when registration is attempted without the required fields.
- **Login - Successful**: Confirms successful login and token retrieval.
- **Login - Unsuccessful**: Ensures the correct error message is returned for an unsuccessful login attempt.

### Special Scenarios
- **Delayed Response**: Simulates scenarios with delayed API responses to test the handling of timeouts and loading states.

## Project Setup

To run this project locally:

1. Clone the repository.
2. Import the Postman collection into your Postman app.
3. Run the collection manually or use the included GitHub Actions workflow for automated testing.

## Automated Testing with GitHub Actions

The project is integrated with GitHub Actions to automate the execution of the test cases. The tests run on each commit to the repository, ensuring that any changes do not break existing functionality.

## How to Use

1. Clone the repository to your local machine.
2. Import the Postman collection from the `collections` folder.
3. Run the collection in Postman or set up a GitHub Actions workflow to automate the process.

## Sample Script
```js
pm.test("Response status code is 200", function () {
  pm.expect(pm.response.code).to.equal(200);
});


pm.test("Response time is less than 600ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(600);
});


pm.test("Validate the response schema", function () {
    const responseData = pm.response.json();
    
    pm.expect(responseData).to.be.an('object');
    pm.expect(responseData).to.have.property('name');
    pm.expect(responseData).to.have.property('job');
    pm.expect(responseData).to.have.property('updatedAt');
});

```

## Report in HTML
![image](https://github.com/user-attachments/assets/d8d5ad14-0124-4e96-93f1-404e1fa031e1)


## Conclusion

This API testing framework provides a robust foundation for testing the Reqres API, ensuring that all critical endpoints are thoroughly validated.
