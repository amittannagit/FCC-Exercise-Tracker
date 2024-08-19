# Exercise Tracker

This is an Exercise Tracker project built as part of the [freeCodeCamp Back End Development and APIs Certification](https://www.freecodecamp.org/learn/back-end-development-and-apis/back-end-development-and-apis-projects/exercise-tracker).

## Project Overview

The Exercise Tracker is a microservice that allows users to log exercise sessions and track their activity over time. The service provides endpoints to create users, log exercises, and retrieve exercise logs.

### Features

- **Create Users**: Register new users with a unique username.
- **Log Exercises**: Record exercise sessions, including the description, duration, and date.
- **Retrieve Logs**: Retrieve a user's exercise logs, with options to filter by date and limit the number of results.

## API Endpoints

### POST `/api/users`

- **Description**: Creates a new user with a unique username.
- **Request Body**:
  ```json
  {
    "username": "john_doe"
  }
  ```
- **Example Response**:
  ```json
  {
    "username": "john_doe",
    "_id": "5f8f8c44b54764421b7156a2"
  }
  ```

### GET `/api/users`

- **Description**: Retrieves an array of all registered users.
- **Example Response**:
  ```json
  [
    { "username": "john_doe", "_id": "5f8f8c44b54764421b7156a2" },
    { "username": "jane_doe", "_id": "5f8f8c44b54764421b7156a3" }
  ]
  ```

### POST `/api/users/:_id/exercises`

- **Description**: Logs an exercise for the user with the specified ID.
- **Request Body**:
  ```json
  {
    "description": "Running",
    "duration": 30,
    "date": "2024-08-20"
  }
  ```
- **Example Response**:
  ```json
  {
    "username": "john_doe",
    "description": "Running",
    "duration": 30,
    "date": "Tue Aug 20 2024",
    "_id": "5f8f8c44b54764421b7156a2"
  }
  ```

### GET `/api/users/:_id/logs`

- **Description**: Retrieves the exercise log for the user with the specified ID. Supports query parameters `from`, `to`, and `limit` to filter the logs.
- **Example Request**:
  ```bash
  curl "http://localhost:3000/api/users/5f8f8c44b54764421b7156a2/logs?from=2024-08-01&to=2024-08-20&limit=5"
  ```
- **Example Response**:
  ```json
  {
    "username": "john_doe",
    "count": 1,
    "_id": "5f8f8c44b54764421b7156a2",
    "log": [
      {
        "description": "Running",
        "duration": 30,
        "date": "Tue Aug 20 2024"
      }
    ]
  }
  ```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v12 or higher)
- [npm](https://www.npmjs.com/) (comes with Node.js)
- [MongoDB](https://www.mongodb.com/) (local or cloud-based)

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/amittannagit/FCC-Exercise-Tracker.git
    ```

2. Navigate to the project directory:

    ```bash
    cd FCC-Exercise-Tracker
    ```

3. Install dependencies:

    ```bash
    npm install
    ```

4. Set up environment variables:

    Create a `.env` file in the root of the project and add your MongoDB connection string:

    ```
    MONGO_URI=your_mongo_db_connection_string
    ```

5. Start the application:

    ```bash
    npm start
    ```

    The server will start and listen on port 3000 or the port specified in the environment variable `PORT`.

## Testing

To test the endpoints, you can use tools like [Postman](https://www.postman.com/) or `curl`.

## Deployment

For deploying the application, you can use services like [Heroku](https://www.heroku.com/), [Vercel](https://vercel.com/), or any cloud provider that supports Node.js applications. Ensure to set the `PORT` environment variable if deploying, and configure your MongoDB URI accordingly.

## Contributing

Feel free to open issues or submit pull requests to contribute to the project. Follow the standard GitHub workflow for contributing.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
