# Trip Manager API

## Overview

The Trip Manager API is a Go-based backend service designed to manage trips efficiently. This project leverages Docker for containerization and provides a straightforward API for trip management tasks.

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/pansani/trip-manager-api-go.git
    cd trip-manager-api-go
    ```

2. Build the Docker image:
    ```sh
    docker build -t trip-manager-api .
    ```

3. Run the service using Docker Compose:
    ```sh
    docker-compose up
    ```

## Configuration

Ensure you have an `.env` file in the root directory with the following environment variables:

```env
DATABASE_HOST=<your-database-host>
DATABASE_PORT=<your-database-port>
DATABASE_NAME=<your-database-name>
DATABASE_USER=<your-database-user>
DATABASE_PASSWORD=<your-database-password>
```

## Usage

To start the server:
```sh
go run cmd/journey/main.go
```

API endpoints will be accessible at `http://localhost:8080`.

## Project Structure

- `cmd/journey`: Contains the main application entry point.
- `internal`: Contains core application logic and internal packages.
- `Dockerfile`: Defines the Docker image configuration.
- `compose.yml`: Docker Compose configuration for setting up the application environment.
- `gen.go`: Code generation tool for various tasks.
- `go.mod` and `go.sum`: Dependency management files.

## API Endpoints

### Authentication
- `POST /login`: Authenticates a user and returns a token.

### Users
- `GET /users`: Retrieves a list of all users.
- `POST /users`: Creates a new user.
- `GET /users/{id}`: Retrieves a user by ID.
- `PUT /users/{id}`: Updates a user by ID.
- `DELETE /users/{id}`: Deletes a user by ID.

### Trips
- `GET /trips`: Retrieves a list of all trips.
- `POST /trips`: Creates a new trip.
- `GET /trips/{id}`: Retrieves a trip by ID.
- `PUT /trips/{id}`: Updates a trip by ID.
- `DELETE /trips/{id}`: Deletes a trip by ID.
