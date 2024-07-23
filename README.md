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
go run cmd/journey/journey.go
```

API endpoints will be accessible at `http://localhost:8080`.

## Project Structure

- `cmd/journey`: Contains the main application entry point.
- `internal`: Contains core application logic and internal packages.
- `Dockerfile`: Defines the Docker image configuration.
- `compose.yml`: Docker Compose configuration for setting up the application environment.
- `gen.go`: Code generation tool for various tasks.
- `go.mod` and `go.sum`: Dependency management files.

# Trips API

## Endpoints

### Create a New Trip
**POST /trips**

**Description:** Create a new trip.

**Request Body:**
- `destination`: string, required, minimum length 4
- `emails_to_invite`: array of emails, required
- `ends_at`: datetime, required
- `owner_email`: email, required
- `owner_name`: string, required
- `starts_at`: datetime, required

### Get Trip Details
**GET /trips/{tripId}**

**Description:** Get trip details by ID.

### Update a Trip
**PUT /trips/{tripId}**

**Description:** Update a trip by ID.

**Request Body:**
- `destination`: string, required, minimum length 4
- `ends_at`: datetime, required
- `starts_at`: datetime, required

### Get Activities for a Trip
**GET /trips/{tripId}/activities**

**Description:** Get activities for a trip by ID.

### Create an Activity for a Trip
**POST /trips/{tripId}/activities**

**Description:** Create an activity for a trip.

**Request Body:**
- `occurs_at`: datetime, required
- `title`: string, required

### Confirm a Trip
**GET /trips/{tripId}/confirm**

**Description:** Confirm a trip and send email invitations.

### Invite Someone to a Trip
**POST /trips/{tripId}/invites**

**Description:** Invite someone to the trip.

**Request Body:**
- `email`: email, required

### Get Links for a Trip
**GET /trips/{tripId}/links**

**Description:** Get links for a trip by ID.

### Create a Link for a Trip
**POST /trips/{tripId}/links**

**Description:** Create a link for a trip.

**Request Body:**
- `title`: string, required
- `url`: string, required, must be a valid URL

### Get Participants for a Trip
**GET /trips/{tripId}/participants**

**Description:** Get participants for a trip by ID.

# Participants API

## Endpoints

### Confirm a Participant
**PATCH /participants/{participantId}/confirm**

**Description:** Confirms a participant on a trip.
