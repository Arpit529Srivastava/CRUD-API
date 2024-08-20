# CRUD API with Go and Gin

## Overview

This project features a simple CRUD API built using Go and the Gin framework. It manages a collection of books, allowing users to:

- Retrieve all books
- Create new books
- Get details of a specific book by ID
- Checkout and return books

## Features

- **Retrieve All Books**: Get a list of all books in the collection.
- **Create a New Book**: Add a new book to the collection.
- **Get Book by ID**: Retrieve details of a specific book by its ID.
- **Checkout a Book**: Decrease the quantity of a book when it is checked out.
- **Return a Book**: Increase the quantity of a book when it is returned.

## Endpoints

### Retrieve All Books

- **Method**: `GET`
- **Endpoint**: `/books`
- **Description**: Returns a list of all books.
- **Response**:
  - **Status**: `200 OK`
  - **Body**: JSON array of book objects.

### Create a New Book

- **Method**: `POST`
- **Endpoint**: `/books`
- **Description**: Adds a new book to the collection.
- **Request Body**:
  ```json
  {
    "id": "string",
    "title": "string",
    "author": "string",
    "quantity": integer
  }
  ```
- **Response**:
  -**Status**: `201 Created`
  -**Body**: `The newly created book object.`
  
### Get Book by ID
- **Method**: `GET`
- **Endpoint**: `/book/:id`
- **Description**: Retrieves a book by its ID.
- **URL Parameter**:
  - `id` (string): The ID of the book.
- **Response**:
  - **Status**: 200 OK (if found)
  - **Status**: 404 Not Found (if not found)
  - **Body**: The book object (if found).

### Checkout a Book
- **Method**: `PATCH`
- **Endpoint**: `/checkout`
- **Description**: Checks out a book by decreasing its quantity.
- **Query Parameter**:
  - `id` (string): The ID of the book.
- **Response**:
  - **Status**: 200 OK (if successful)
  - **Status**: 400 Bad Request (if the book is not available or query parameter is missing)
  - **Status**: 404 Not Found (if the book is not found)
  - **Body**: The updated book object.

### Return a Book
- **Method**: `PATCH`
- **Endpoint**: `/return`
- **Description**: Returns a book by increasing its quantity.
- **Query Parameter**:
  - `id` (string): The ID of the book.
- **Response**:
  - **Status**: 200 OK (if successful)
  - **Status**: 400 Bad Request (if query parameter is missing)
  - **Status**: 404 Not Found (if the book is not found)
  - **Body**: The updated book object.
## Clone the Repository

To get started with this project, clone the repository using:

```bash
git clone https://github.com/Arpit529Srivastava/CRUD-API.git
cd your-repo
``` 

## Setup

Before running the application, make sure to tidy up your Go modules by running:

```bash
go mod tidy
```
## Get All Books
```bash
curl http://localhost:8080/books
```
## Return a Book
To return a book with ID 2, run:
```bash
curl -X PATCH "http://localhost:8080/return?id=2"
```
## Checkout a Book
To checkout a book with ID 2, run:
```bash
curl -X PATCH "http://localhost:8080/checkout?id=2"
```
