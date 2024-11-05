# React + Flask Web Scraper with OpenAI Integration

This project is a full-stack web application that uses React for the frontend and Flask for the backend. The app allows users to submit a URL, scrapes the content, generates questions based on the content using OpenAI's GPT API, and categorizes users based on their answers.
![image](https://github.com/user-attachments/assets/108919fa-a40f-4450-8c9d-c0fd0ab26d59)
![image](https://github.com/user-attachments/assets/ed62e099-e7f1-469a-8192-ec54ff6b043b)


## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Testing](#testing)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Features

- Scrapes content from a provided URL.
- Uses OpenAI GPT API to generate dynamic questions based on content.
- Presents questions to the user and categorizes them based on answers.
- Mock responses available for testing without consuming OpenAI quota.

## Tech Stack

- **Frontend**: React, Axios
- **Backend**: Flask, Flask-CORS, BeautifulSoup, OpenAI API
- **Libraries**: Python, Node.js
- **Third-Party Services**: OpenAI GPT API

## Setup Instructions

### Prerequisites

- Python 3.x
- Node.js and npm
- OpenAI API key

### Backend Setup (Flask)

1. Clone the repository and navigate to the `flask-backend` directory:
   ```bash
   git clone <repo_url>
   cd react-flask-app/flask-backend
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the `flask-backend` directory and add your OpenAI API key:
   ```plaintext
   OPENAI_API_KEY=your_openai_api_key
   ```

5. Start the Flask server:
   ```bash
   python app.py
   ```

### Frontend Setup (React)

1. Navigate to the `react-frontend` directory:
   ```bash
   cd ../react-frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the React development server:
   ```bash
   npm start
   ```

The React app should now be running at `http://localhost:3000`, and the Flask API server should be running at `http://localhost:5000`.

## Usage

1. Open the React app in your browser at `http://localhost:3000`.
2. Enter a URL in the input field and submit.
3. The backend will scrape the content, generate questions, and display them in the app.
4. Select answers to the questions and submit to view your categorized result.

### Example Screenshots
![image](https://github.com/user-attachments/assets/3787926c-4938-41c0-81ff-706d3883a442)
![image](https://github.com/user-attachments/assets/1049446b-fcaf-467a-9e6d-6aa3decb7c31)



## Project Structure

```plaintext
react-flask-app/
├── flask-backend/
│   ├── app.py              # Flask API setup and route handlers
│   ├── requirements.txt    # Python dependencies for Flask
│   ├── .env                # Environment variables (not in repo)
│   └── venv/               # Virtual environment (not in repo)
├── react-frontend/
│   ├── src/
│   │   ├── App.js          # Main React component
│   │   └── index.js        # Entry point for React
│   ├── package.json        # Node dependencies for React
└── README.md               # Project documentation
```

## API Documentation

### POST /generate-questions
- **Description**: Accepts a URL, scrapes content, and returns generated questions.
- **Request Body**:
  ```json
  {
    "url": "https://example.com"
  }
  ```
- **Response**:
  ```json
  {
    "questions": [
      {
        "question": "What is your primary interest?",
        "options": ["Technology", "Science", "Literature"]
      }
    ]
  }
  ```

### POST /categorize
- **Description**: Accepts user responses and returns a category.
- **Request Body**:
  ```json
  {
    "user_response": "Science, Hands-on Practice"
  }
  ```
- **Response**:
  ```json
  {
    "category": "You are a hands-on science enthusiast."
  }
  ```

## Testing

### Mock Testing
For testing without consuming OpenAI API quota, mock the `analyze_with_chatgpt` function in `app.py` as follows:

```python
def analyze_with_chatgpt(content):
    return {
        "questions": [
            {
                "question": "Sample question?",
                "options": ["Option A", "Option B", "Option C"]
            }
        ]
    }
```

This setup allows testing of the frontend without relying on the OpenAI API.

## Troubleshooting

### CORS Issues
If you see a CORS error in the console, ensure `flask-cors` is installed, and `CORS(app)` is in your `app.py` file.

### OpenAI Quota Errors
If you see "quota exceeded" errors, verify your OpenAI account plan and usage on the [OpenAI Usage Page](https://platform.openai.com/account/usage).

## Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit (`git commit -m 'Add feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request.


