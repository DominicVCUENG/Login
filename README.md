# Login Service API

This Flask application provides a simple login service API that manages user authentication and session management using server-side sessions.

## Technologies Used

- Python
- Flask
- Flask-CORS

## Setup

1. Clone the repository:

```
git clone <repository_url>
cd <repository_name>
```
   
2. Install dependencies:

```
pip install -r requirements.txt
```

3. Set up the environment:
Ensure you have a `.env` file or environment variables set up with a `SECRET_KEY`. Example:

```
SECRET_KEY=your_secret_key
```

4. Run the application:
   
```
python app.py
```

5. The application will run on `http://localhost:5000` by default.

## Endpoints

### Login a user

- **POST** `/login`

Logs in a user by creating a session. Requires a JSON payload with a `username` field.

**Request**
```
{
    "username": "exampleUser"
}
```

**Response**
```
{
    "message": "Login successful",
    "username": "exampleUser"
}
```

### Check session status

- **GET** `/check_session`

Checks if a user is logged in by verifying the session.

**Response (logged in)**
```
{
    "logged_in": true,
    "username": "exampleUser"
}
```

**Response (not logged in)**
```
{
    "logged_in": false"
}
```

### Logout a user

- **POST** `/logout`

Logs out the current user by clearing the session.

**Response**
```
{
    "message": "Logged out successfully
}
```

## Example Usage

### Log in a user

```python
import requests

data = {
    "username": "exampleUser"
}
response = requests.post('http://localhost:5000/login', json=data)
print(response.json())
```

### Check if a user is logged in

```python
import requests

response = requests.get('http://localhost:5000/check_session')
print(response.json())
```

### Log out a user

```python
import requests

response = requests.post('http://localhost:5000/logout')
print(response.json())
```

## Session Management

The API uses secure, server-side sessions with cookies. Ensure your browser or client is configured to handle cookies properly. Use the `credentials: 'include'` option when making requests from the frontend.