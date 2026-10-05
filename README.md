# Resumely — AI Resume ATS Analyzer

Resumely is a full-stack AI-powered Resume ATS Analyzer that evaluates resumes against ATS-oriented criteria and provides actionable feedback.

This project was developed as a hands-on project during the 3-Day Employability Enhancement Workshop conducted by MyAnatomy, held from 22nd–24th September 2026.

## Live Demo

[Try Resumely](https://code-sandbox.myanatomy.in/capstone-project-preview/6ab249d2d65dcd19aab50abe/80bf930d-518a-499e-b857-d613b92dcf52)

The live demo is hosted through the MyAnatomy Sandbox environment.

## Features

- User registration and login
- JWT-based authentication
- Secure password hashing using bcrypt
- Resume upload and text input
- PDF, DOCX, and TXT resume support
- Resume file size validation
- Optional job description input
- AI-powered resume analysis using Google Gemini
- ATS score from 0–100
- Resume verdict and summary
- Resume strengths and improvement suggestions
- Matched and missing keywords
- Section-wise resume scoring
- Analysis history for authenticated users
- MongoDB-based data persistence
- Cloudinary-based file storage
- Input validation
- API rate limiting
- Security headers using Helmet
- CORS configuration
- AI response validation

## How It Works

User
|
v
React Frontend
|
| Resume + Job Description
v
Express.js Backend
|
+-- Authentication
+-- File Processing
+-- Input Validation
|
v
Google Gemini API
|
| AI-generated ATS analysis
v
Validated Analysis
|
+-- ATS Score
+-- Verdict
+-- Strengths
+-- Improvements
+-- Keywords
+-- Section Scores
|
v
Results Dashboard
|
v
MongoDB

## Tech Stack

### Frontend

- React
- Redux Toolkit
- React Redux
- React Router
- JavaScript
- CSS

### Backend

- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT
- bcryptjs
- Multer

### AI and Cloud Services

- Google Gemini API
- Cloudinary

### File Processing

- pdf-parse
- Mammoth

### Security

- Helmet
- CORS
- Express Rate Limit
- JWT Authentication
- Input Validation

## Project Structure

Resume-ATS-main/
|
|-- backEnd/
|   |-- config/
|   |-- middleware/
|   |-- models/
|   |-- routes/
|   |-- scripts/
|   |-- services/
|   |-- utils/
|   |-- index.js
|   |-- package.json
|
|-- frontEnd/
|   |-- public/
|   |-- src/
|   |   |-- components/
|   |   |-- constants/
|   |   |-- services/
|   |   |-- store/
|   |   |-- App.jsx
|   |   |-- index.js
|   |   |-- styles.css
|   |-- package.json
|
|-- .gitignore

## Gemini AI Integration

Google Gemini is used to analyze resume content and generate a structured ATS evaluation.

The analysis can provide:

- Overall ATS score
- Resume verdict
- Resume summary
- Strengths
- Improvement suggestions
- Matched keywords
- Missing keywords
- Section-wise scores
- Section-specific feedback

When a job description is provided, the application also evaluates the alignment between the resume and the target role.

The backend validates the AI-generated response before returning the result to the frontend.

## Resume Processing

Users can either upload a resume or provide resume text directly.

Supported formats:

- PDF
- DOCX
- TXT

Uploaded files are processed on the backend before being analyzed by Gemini.

- PDF files are processed using pdf-parse
- DOCX files are processed using Mammoth
- TXT files are read directly

## Authentication

The application uses JWT-based authentication and bcrypt password hashing.

Users can:

1. Create an account
2. Sign in
3. Analyze resumes
4. View their saved analyses

Protected routes require authentication.

## Database

MongoDB is used for application data storage, with Mongoose providing the database models and interaction layer.

The application stores information related to:

- Users
- Resume analyses
- Resume text
- Job descriptions
- ATS scores
- AI-generated analysis
- Analysis timestamps

## Cloud Storage

Cloudinary is used for resume file storage where configured.

Uploaded resume files can be stored as private assets with associated metadata.

## Security

The backend implements multiple security measures, including:

- JWT authentication
- bcrypt password hashing
- Helmet security headers
- CORS restrictions
- API rate limiting
- Authentication rate limiting
- File validation
- Input validation
- AI response validation

Sensitive credentials are stored using environment variables and are excluded from the Git repository.

## Environment Variables

Create a .env file inside the backEnd directory.

Example:

PORT=4000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=your_gemini_model
CLIENT_ORIGIN=http://localhost:3000

CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

Do not commit .env files, API keys, database credentials, JWT secrets, or Cloudinary credentials to GitHub.

## Running Locally

### 1. Clone the Repository

git clone https://github.com/Ekaspreet-Kaur/ai-resume-ats-analyzer.git

cd ai-resume-ats-analyzer

### 2. Install Backend Dependencies

cd backEnd

npm install

Configure the required environment variables in the .env file.

Start the backend:

npm run dev

### 3. Install Frontend Dependencies

Open another terminal:

cd frontEnd

npm install

Start the frontend:

npm run dev

## API Endpoints

### Authentication

POST /api/auth/signup
POST /api/auth/login
POST /api/auth/signin

### Resume Analysis

POST /api/analyze

### Analysis History

GET /api/analyses
GET /api/analyses/:id

Protected endpoints require authentication.

## Example Analysis

A typical analysis can contain:

{
  "score": 82,
  "verdict": "Strong",
  "summary": "The resume demonstrates relevant technical experience.",
  "strengths": [
    "Clear technical skills",
    "Relevant project experience"
  ],
  "improvements": [
    "Add measurable achievements",
    "Improve keyword alignment"
  ],
  "keywords": {
    "matched": [
      "React",
      "Node.js",
      "MongoDB"
    ],
    "missing": [
      "Docker"
    ]
  },
  "sections": [
    {
      "name": "Skills",
      "score": 88,
      "note": "Strong technical coverage."
    }
  ]
}

## Workshop Context

This project was developed during the 3-Day Employability Enhancement Workshop by MyAnatomy, held from 22nd–24th September 2026.

The workshop provided hands-on exposure to Full Stack Development with Gemini AI and involved developing a practical AI-powered application.

## Author

Ekaspreet Kaur

B.Tech Computer Science and Engineering

GitHub: https://github.com/Ekaspreet-Kaur

## Disclaimer

This project was developed as part of the MyAnatomy Employability Enhancement Workshop and is published for portfolio and learning purposes with permission to publish the workshop project.

## License

No separate open-source license has been added to this repository.

Please refer to the applicable workshop/project terms before redistributing or commercially using the project.
