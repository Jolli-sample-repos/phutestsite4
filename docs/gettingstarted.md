---
title: "gettingstarted"
---

**Last Updated:** 11/14/2025

---

# Getting Started with the Books API

Welcome to the Books API! This guide will help you get up and running with a simple Express.js REST API for managing a collection of books.

## Overview

The Books API is a lightweight RESTful API built with Express.js that provides full CRUD (Create, Read, Update, Delete) operations for managing a book collection. It uses an in-memory database, making it perfect for learning, prototyping, and testing.

### Key Features

- **Full CRUD Operations**: Create, read, update, and delete books
- **Search Functionality**: Search books by title or author
- **RESTful Design**: Clean and intuitive API endpoints
- **JSON Responses**: All responses are in JSON format
- **Error Handling**: Comprehensive error handling and validation
- **CORS Enabled**: Ready for cross-origin requests

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (version 14 or higher)
- **npm** (comes with Node.js)

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/jolliai/example-express-js.git
cd example-express-js
```

### 2. Install Dependencies

```bash
npm install
```

This will install the following packages:
- `express` - Web framework for Node.js
- `cors` - Enable Cross-Origin Resource Sharing
- `body-parser` - Parse incoming request bodies
- `nodemon` (dev dependency) - Auto-restart server during development

## Running the Server

### Start in Production Mode

```bash
npm start
```

### Start in Development Mode

For development with auto-reload on file changes:

```bash
npm run dev
```

The server will start on `http://localhost:3000` by default. You should see:

```
🚀 Server is running on http://localhost:3000
📚 Try http://localhost:3000/api/books to see all books
✨ Have a wonderful day!
```

## API Endpoints

### Root Endpoint

**GET /**

Returns a welcome message and list of available endpoints.

```bash
curl http://localhost:3000/
```

Response:
```json
{
  "message": "Welcome to the Books API",
  "endpoints": {
    "GET /api/books": "Get all books",
    "GET /api/books/:id": "Get a book by ID",
    "POST /api/books": "Create a new book",
    "PUT /api/books/:id": "Update a book",
    "DELETE /api/books/:id": "Delete a book",
    "GET /api/books/search": "Search books by query parameter"
  }
}
```

### Get All Books

**GET /api/books**

Retrieves all books in the collection.

```bash
curl http://localhost:3000/api/books
```

Response:
```json
{
  "success": true,
  "count": 3,
  "data": [
    {
      "id": 1,
      "title": "The Great Gatsby",
      "author": "F. Scott Fitzgerald",
      "year": 1925,
      "isbn": "978-0-7432-7356-5"
    },
    {
      "id": 2,
      "title": "1984",
      "author": "George Orwell",
      "year": 1949,
      "isbn": "978-0-452-28423-4"
    },
    {
      "id": 3,
      "title": "To Kill a Mockingbird",
      "author": "Harper Lee",
      "year": 1960,
      "isbn": "978-0-06-112008-4"
    }
  ]
}
```

### Get Book by ID

**GET /api/books/:id**

Retrieves a specific book by its ID.

```bash
curl http://localhost:3000/api/books/1
```

Response:
```json
{
  "success": true,
  "data": {
    "id": 1,
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "year": 1925,
    "isbn": "978-0-7432-7356-5"
  }
}
```

### Search Books

**GET /api/books/search?q=&#123;query&#125;**

Search for books by title or author.

```bash
curl "http://localhost:3000/api/books/search?q=orwell"
```

Response:
```json
{
  "success": true,
  "query": "orwell",
  "count": 1,
  "data": [
    {
      "id": 2,
      "title": "1984",
      "author": "George Orwell",
      "year": 1949,
      "isbn": "978-0-452-28423-4"
    }
  ]
}
```

### Create a New Book

**POST /api/books**

Creates a new book in the collection.

**Required fields:**
- `title` (string)
- `author` (string)

**Optional fields:**
- `year` (number)
- `isbn` (string)

```bash
curl -X POST http://localhost:3000/api/books \
  -H "Content-Type: application/json" \
  -d '{
    "title": "The Catcher in the Rye",
    "author": "J.D. Salinger",
    "year": 1951,
    "isbn": "978-0-316-76948-0"
  }'
```

Response:
```json
{
  "success": true,
  "message": "Book created successfully",
  "data": {
    "id": 4,
    "title": "The Catcher in the Rye",
    "author": "J.D. Salinger",
    "year": 1951,
    "isbn": "978-0-316-76948-0"
  }
}
```

### Update a Book

**PUT /api/books/:id**

Updates an existing book. Only provided fields will be updated.

```bash
curl -X PUT http://localhost:3000/api/books/1 \
  -H "Content-Type: application/json" \
  -d '{
    "year": 1926
  }'
```

Response:
```json
{
  "success": true,
  "message": "Book updated successfully",
  "data": {
    "id": 1,
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "year": 1926,
    "isbn": "978-0-7432-7356-5"
  }
}
```

### Delete a Book

**DELETE /api/books/:id**

Deletes a book from the collection.

```bash
curl -X DELETE http://localhost:3000/api/books/1
```

Response:
```json
{
  "success": true,
  "message": "Book deleted successfully",
  "data": {
    "id": 1,
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "year": 1925,
    "isbn": "978-0-7432-7356-5"
  }
}
```

## Testing the API

The project includes a comprehensive test suite that you can run to verify all endpoints are working correctly.

### Run Tests

First, make sure the server is running:

```bash
npm start
```

Then, in a separate terminal, run the tests:

```bash
npm test
```

The test script will:
1. Test the root endpoint
2. Get all books
3. Get a specific book by ID
4. Test error handling for non-existent books
5. Create a new book
6. Update a book
7. Search for books
8. Test validation with missing fields
9. Delete a book
10. Verify the deletion

## Error Handling

The API includes comprehensive error handling:

### 404 - Not Found

When a book doesn't exist:

```json
{
  "success": false,
  "message": "Book with ID 999 not found"
}
```

### 400 - Bad Request

When required fields are missing:

```json
{
  "success": false,
  "message": "Title and author are required fields"
}
```

When search query is missing:

```json
{
  "success": false,
  "message": "Search query parameter \"q\" is required"
}
```

### 404 - Endpoint Not Found

When accessing an invalid endpoint:

```json
{
  "success": false,
  "message": "Endpoint not found"
}
```

### 500 - Server Error

When an unexpected error occurs:

```json
{
  "success": false,
  "message": "Something went wrong!",
  "error": "Error details here"
}
```

## Project Structure

```
example-express-js/
├── server.js           # Main application file with all routes
├── test-api.js         # Test suite for API endpoints
├── package.json        # Project dependencies and scripts
├── package-lock.json   # Locked dependency versions
└── README.md          # Project documentation
```

## Configuration

### Port Configuration

By default, the server runs on port 3000. You can change this by setting the `PORT` environment variable:

```bash
PORT=8080 npm start
```

### CORS Configuration

CORS is enabled by default for all origins. To restrict origins, modify the CORS configuration in `server.js`:

```javascript
app.use(cors({
  origin: 'https://yourdomain.com'
}));
```

## Next Steps

Now that you have the Books API running, here are some ideas to extend it:

1. **Add Database Integration**: Replace the in-memory storage with MongoDB, PostgreSQL, or another database
2. **Add Authentication**: Implement JWT-based authentication to secure endpoints
3. **Add Pagination**: Implement pagination for the GET /api/books endpoint
4. **Add Filtering**: Add query parameters to filter books by year, author, etc.
5. **Add Validation**: Use a library like Joi or express-validator for more robust validation
6. **Add Documentation**: Generate API documentation using Swagger/OpenAPI
7. **Add Rate Limiting**: Implement rate limiting to prevent abuse
8. **Add Logging**: Add request logging with Morgan or Winston

## Troubleshooting

### Server won't start

**Problem**: Port 3000 is already in use

**Solution**: Either stop the process using port 3000 or use a different port:
```bash
PORT=3001 npm start
```

### Tests fail

**Problem**: Server is not running

**Solution**: Make sure the server is running before executing tests:
```bash
npm start
# In another terminal:
npm test
```

### Cannot POST/PUT data

**Problem**: Missing Content-Type header

**Solution**: Always include the Content-Type header when sending JSON:
```bash
-H "Content-Type: application/json"
```

## Important Notes

- This is a super important API
- Books are life
- Remember to hydrate

## Support

For issues, questions, or contributions, please visit the [GitHub repository](https://github.com/jolliai/example-express-js).

Happy coding! 🚀📚