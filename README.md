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

url-shortener-go/
├── cmd/
│   └── server/
│       └── main.go            # Entry point for the application
├── pkg/
│   ├── api/
│   │   ├── handler.go         # HTTP handler functions
│   │   └── routes.go          # API route definitions
│   ├── storage/
│   │   ├── storage.go         # Interface for database operations
│   │   └── sqlite/
│   │       └── sqlite.go      # SQLite-specific implementation
│   ├── shortener/
│   │   └── shortener.go       # Logic for generating and managing short URLs
├── internal/
│   └── config/
│       └── config.go          # Application configuration management
├── db/
│   └── migrations/
│       └── 001_init.sql       # SQL file for database schema
├── go.mod                      # Go module file
├── go.sum                      # Go dependency file
├── README.md                   # Project documentation
└── urlshortener.db             # SQLite database file (created automatically)




### How It Works

1. **Shortening a URL**: 
    - The user sends a `POST` request to the `/shorten` endpoint with the original URL.
    - The service generates a unique shortcode using base62 encoding and stores it in the database.

2. **Redirecting**:
    - The user accesses the short URL.
    - The service looks up the original URL from the database using the shortcode and redirects the user.

### Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request for improvements or features.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### Contact

- **Author**: Albert Ndege
- **GitHub**: [https://github.com/ndegealbert])
