# URL Shortener in Go

![Go](https://img.shields.io/badge/Go-1.19-blue)
![License](https://img.shields.io/badge/license-MIT-green)

A simple and efficient URL shortener service built using Go. This service allows users to shorten long URLs and redirect using the generated short codes.

## Features

- Generate short URLs for long links.
- Redirect to the original URL using the short code.
- Lightweight and easy to deploy.
- Built with `net/http` and `gorilla/mux` for request handling.
- SQLite database for storage.

## Getting Started

### Prerequisites

- [Go](https://golang.org/dl/) (version 1.19 or higher)
- SQLite3 (or any other database of your choice)

### Installation

1. **Clone the repository**
    ```bash
    git clone https://github.com/yourusername/url-shortener-go.git
    cd url-shortener-go
    ```

2. **Install dependencies**
    ```bash
    go mod tidy
    ```

3. **Run the application**
    ```bash
    go run main.go
    ```

4. **Access the service**
    - The service will be available at `http://localhost:8080`.

### API Endpoints

- **POST /shorten**
    - **Description**: Shorten a given URL.
    - **Request Body**: 
      ```json
      {
          "url": "https://www.example.com"
      }
      ```
    - **Response**:
      ```json
      {
          "short_url": "http://localhost:8080/abc123"
      }
      ```

- **GET /{shortCode}**
    - **Description**: Redirects to the original URL.
    - **Example**: Access `http://localhost:8080/abc123` and it will redirect to `https://www.example.com`.

### Project Structure

