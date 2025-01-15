# Todo Application API with React Frontend

## Overview

This project is a full-stack Todo Application consisting of a **Node.js backend** and a **React frontend**. The backend handles user authentication (via JWT), CRUD operations for todos, and file uploads. The frontend is built with React and allows users to interact with the API to manage their tasks.

## Features

### Backend (Node.js)

- **User Authentication**
  - User signup with email and password.
  - User login with email and password.
  - JWT authentication for protected routes.
  - Account deletion with the removal of todos and associated images.
  - Token refresh for session management.
- **Todo Management**
  - Add a new todo (with an image).
  - Get all todos for a user.
  - Update todo details such as title, description, and completion status.
  - Delete todos and associated images.

### Frontend (React)

- **Signup / Login** pages for user authentication.
- **Todo Dashboard** to view, add, update, and delete todos.
- **Image Upload** for adding images to todos.

## Setup

### Prerequisites

- Node.js and npm installed.
- MongoDB installed and running locally or using a cloud MongoDB service like MongoDB Atlas.
- React and related tools installed for the frontend.

### Backend Setup

1. Clone the backend repository:

   ```bash
   git clone <repository_url>
   cd <repository_folder>
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Set up environment variables:

   Create a `.env` file in the root directory of the project and add the following values:

   ```env
   PORT=8000
   MONGO_URL=mongodb://127.0.0.1/my_database
   JWT_SECRET=todoapp
   JWT_EXPIRATION_TIME=12h
   ```

   - **PORT**: The port on which the backend will run (default is 8000).
   - **MONGO_URL**: The connection string for your MongoDB database.
   - **JWT_SECRET**: The secret key for signing JWT tokens.
   - **JWT_EXPIRATION_TIME**: The expiration time for the JWT token.

4. Start the server:

   ```bash
   npm start
   ```

   The backend will run on port `8000` by default.

### Frontend Setup

1. Clone the frontend repository (React app):

   ```bash
   git clone <frontend_repository_url>
   cd <frontend_folder>
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Set up environment variables:

   Create a `.env` file in the root of the frontend project and add the following:

   ```env
   REACT_APP_API_URL=http://localhost:8000/api
   ```

   This points the frontend to the backend API URL.

4. Start the React development server:

   ```bash
   npm start
   ```

   The React app will run on `http://localhost:3000`.

## API Endpoints

### Authentication Endpoints

#### 1. **Signup User**

- **URL**: `/api/signup`
- **Method**: `POST`
- **Body**:
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
  }
  ```

#### 2. **Login User**

- **URL**: `/api/login`
- **Method**: `POST`
- **Body**:
  ```json
  {
    "email": "john@example.com",
    "password": "password123"
  }
  ```

#### 3. **Delete User Account**

- **URL**: `/api/delete-account`
- **Method**: `DELETE`
- **Body**:
  ```json
  {
    "token": "<jwt_token>"
  }
  ```

#### 4. **Refresh Token**

- **URL**: `/api/refresh`
- **Method**: `POST`
- **Body**:
  ```json
  {
    "token": "<jwt_token>"
  }
  ```

### Todo Endpoints

#### 1. **Add Todo**

- **URL**: `/api/todo`
- **Method**: `POST`
- **Headers**:
  - `Authorization: Bearer <jwt_token>`
- **Body**:
  ```json
  {
    "title": "Buy groceries",
    "description": "Milk, eggs, bread, etc.",
    "image": "image_file" // Optional
  }
  ```

#### 2. **Get Todos**

- **URL**: `/api/todo`
- **Method**: `GET`
- **Headers**:
  - `Authorization: Bearer <jwt_token>`

#### 3. **Update Todo**

- **URL**: `/api/todo/:id`
- **Method**: `PUT`
- **Headers**:
  - `Authorization: Bearer <jwt_token>`
- **Body**:
  ```json
  {
    "title": "Updated title",
    "description": "Updated description",
    "completed": true,
    "image": "new_image_file" // Optional
  }
  ```

#### 4. **Delete Todo**

- **URL**: `/api/todo/:id`
- **Method**: `DELETE`
- **Headers**:
  - `Authorization: Bearer <jwt_token>`

## Running the Application

### Backend:

1. Follow the **Backend Setup** section to get the backend running.
2. Test the API using Postman or your preferred API testing tool.

### Frontend:

1. Follow the **Frontend Setup** section to get the React application running.
2. Access the React app at `http://localhost:3000` in your browser.
