## Tutorials_booking_app


### Base URL
- The base URL for the API is `http://localhost:3001` unless you configure it differently.

### Endpoints

#### 1. Match Tutors
- **Endpoint:** `POST /match`
- **Description:** Matches tutors based on student preferences.
- **Request Payload:**
  ```json
  {
    "subject": "maths",
    "grade": 10,
    "classes": [
      {
        "duration": 1,
        "prefTime": [
          { "day": "monday", "slots": [14, 15] },
          { "day": "wednesday", "slots": [16, 17] }
        ]
      },
      // Additional class preferences...
    ]
  }
  ```
- **Response:**
  ```json
  {
    "matchedTutors": [
      { "tutor": { "name": "John Doe", "subject": "maths", "grades": [10], "availability": [...] }, "fitScore": 75 },
      // Additional matched tutors...
    ]
  }
  ```

#### 2. Generate Student Preferences using GPT
- **Endpoint:** `POST /ai`
- **Description:** Uses GPT to generate student preferences based on user input.
- **Request Payload:**
  ```json
  {
    "message": "Generate student preferences for a math class."
  }
  ```
- **Response:**
  ```json
  {
    "matchedTutors": [
      { "tutor": { "name": "Jane Doe", "subject": "maths", "grades": [10], "availability": [...] }, "fitScore": 80 },
      // Additional matched tutors...
    ]
  }
  ```

#### 3. Add to Favorites
- **Endpoint:** `POST /addToFav`
- **Description:** Adds a tutor to the student's favorites.
- **Request Payload:**
  ```json
  {
    "studentName": "Alice",
    "tutorName": "John Doe",
    "fitScore": 75
  }
  ```
- **Response:**
  ```json
  {
    "studentName": "Alice",
    "tutorName": "John Doe",
    "fitScore": 75,
    "_id": "5f25d18aa08be327882bf84e",
    "__v": 0
  }
  ```

### Data Models

#### Tutor Model
- Represents information about a tutor.
  ```json
  {
    "name": "John Doe",
    "subject": "maths",
    "grades": [10],
    "availability": [
      { "day": "monday", "slots": [14, 15] },
      { "day": "wednesday", "slots": [16, 17] }
    ]
  }
  ```

#### Student Preferences Model
- Represents student preferences for matching tutors.
  ```json
  {
    "subject": "maths",
    "grade": 10,
    "classes": [
      {
        "duration": 1,
        "prefTime": [
          { "day": "monday", "slots": [14, 15] },
          { "day": "wednesday", "slots": [16, 17] }
        ]
      }
    ]
  }
  ```

#### Favorite Tutor Model
- Represents a tutor added to a student's favorites.
  ```json
  {
    "studentName": "Alice",
    "tutorName": "John Doe",
    "fitScore": 75
  }
  ```

### Errors
- If an error occurs, the API will respond with an appropriate status code and an error message.

### Notes
- Make sure to replace the base URL with the actual URL where the API is hosted.
- Always check the API documentation for any updates or changes.

This documentation provides a high-level overview of the available endpoints, their purposes, and example requests and responses. Ensure to include additional details as needed, such as authentication requirements or specific error messages.
