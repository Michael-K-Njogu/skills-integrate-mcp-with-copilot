# Mergington High School Activities API

A FastAPI application that allows students to view, sign up for, and unregister from extracurricular activities at Mergington High School. Includes a web UI and user authentication.

## Features

- Web UI served at the root URL
- View all available extracurricular activities
- Create an account and log in
- Sign up for activities (authentication required)
- Unregister from activities (authentication required)

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - Web UI: http://localhost:8000
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

### Activities

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up for an activity (authentication required)                   |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister from an activity (authentication required)           |

### Authentication

| Method | Endpoint                                     | Description                        |
| ------ | -------------------------------------------- | ---------------------------------- |
| POST   | `/auth/signup?email=...&password=...`        | Create a new account               |
| POST   | `/auth/login?email=...&password=...`         | Log in and receive a session cookie |
| POST   | `/auth/logout`                               | Log out and clear the session cookie |
| GET    | `/auth/me`                                   | Get the currently logged-in user   |

## Available Activities

The application comes pre-loaded with the following activities:

- **Chess Club** — Fridays, 3:30 PM - 5:00 PM (max 12 participants)
- **Programming Class** — Tuesdays and Thursdays, 3:30 PM - 4:30 PM (max 20 participants)
- **Gym Class** — Mondays, Wednesdays, Fridays, 2:00 PM - 3:00 PM (max 30 participants)
- **Soccer Team** — Tuesdays and Thursdays, 4:00 PM - 5:30 PM (max 22 participants)
- **Basketball Team** — Wednesdays and Fridays, 3:30 PM - 5:00 PM (max 15 participants)
- **Art Club** — Thursdays, 3:30 PM - 5:00 PM (max 15 participants)
- **Drama Club** — Mondays and Wednesdays, 4:00 PM - 5:30 PM (max 20 participants)
- **Math Club** — Tuesdays, 3:30 PM - 4:30 PM (max 10 participants)
- **Debate Team** — Fridays, 4:00 PM - 5:30 PM (max 12 participants)
- **Manga Maniacs** — Tuesdays, 8:00 PM (max 20 participants)

## Data Model

The application uses a simple in-memory data model:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Users** - Uses email as identifier:
   - Password

All data is stored in memory, which means data will be reset when the server restarts.
