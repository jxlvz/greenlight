# Greenlight API

Greenlight API is a robust JSON API built in Go for managing movie information. It's designed with a focus on idiomatic Go practices, project structure, and production-ready features, guided by the principles outlined in Alex Edwards' "Let’s Go Further" book.

## Features

This API provides a comprehensive set of features for managing movie data, including:

- **Idiomatic Project Structure:** A clean, flexible, and scalable project organization.
- **JSON API:** Delivers JSON responses with comprehensive and user-friendly error handling.
- **Request Parsing & Validation:** Strong validation for incoming request data.
- **Database Migrations:** SQL migrations for robust database schema management.
- **Database Operations:** Efficient and safe database interactions with timeouts and connection pooling.
- **Resource Actions:** Advanced resource manipulation, including partial updates and optimistic concurrency control.
- **Filtering, Sorting & Pagination:** Powerful mechanisms for querying and retrieving data subsets.
- **Full-Text Search:** Leverages PostgreSQL's full-text search capabilities.
- **Structured Logging:** Implements structured JSON logging for better observability.
- **Rate Limiting:** Per-client rate limiting to ensure fair usage and prevent abuse.
- **Background Tasks:** Safe execution of background tasks with completion guarantees.
- **Graceful Shutdown:** Ensures in-flight tasks are completed before server termination.
- **Email Integration:** Sends emails using embedded templates and supports activation/password reset flows.
- **Authentication & Authorization:** Secure bearer token authentication, JWT support, and permission-based authorization.
- **CORS Support:** Configurable CORS headers for seamless integration with JavaScript frontends.
- **Application Metrics:** Exposes key application metrics (memory usage, DB pool stats, response counts) via `/debug/vars`.
- **Automated Builds & Audits:** Facilitates automated builds, quality control checks, and versioned binaries.

## Project Structure

The project follows a clean architecture, separating concerns into distinct packages:

- `cmd/api`: The main application executable, containing HTTP handlers, middleware, server logic, and configuration.
- `internal/data`: Core data models, database interactions (Movies, Users, Tokens, Permissions), and validation logic.
- `internal/mailer`: Email sending functionality with templating.
- `internal/vcs`: Version information retrieval using Go build info.
- `migrations`: Database migration scripts.
- `vendor`: Managed third-party dependencies.

## Getting Started

### Prerequisites

- Go (version specified in `go.mod` or `modules.txt`, typically a recent stable version)
- PostgreSQL database

### Local Development Setup

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/jxlvz/greenlight
    cd greenlight
    ```

2.  **Set up the database:**

    - Ensure PostgreSQL is running.
    - Create a database (e.g., `greenlight` or `pqgotest` as used in `pq` examples).
    - Set the `GREENLIGHT_DB_DSN` environment variable or pass the DSN via the `-db-dsn` flag to the `cmd/api` executable. The DSN should be in the format: `postgres://user:password@host:port/dbname?sslmode=disable`.

    _Example using environment variable:_

    ```bash
    export GREENLIGHT_DB_DSN="postgres://user:password@localhost:5432/greenlight?sslmode=disable"
    ```

3.  **Apply database migrations:**

    ```bash
    make db/migrations/up
    ```

    _(You will be prompted to confirm before applying migrations.)_

4.  **Run the API server:**
    ```bash
    make run/api
    ```
    The API will typically start on `http://localhost:4000`.

## Makefile Commands

The project includes a `Makefile` for common development tasks:

- `make help`: Displays available commands.
- `make db/psql`: Connects to the database using `psql`.
- `make db/migrations/new name="migration_name"`: Creates a new SQL migration file.
- `make db/migrations/up`: Applies all pending database migrations.
- `make tidy`: Formats Go files, tidies module dependencies, verifies, and vendors them.
- `make audit`: Runs code quality checks (vetting, staticcheck, race detection in tests).
- `make build/api`: Builds the `cmd/api` application for the current OS.

## Versioning

The application version is managed automatically using Git information. The `-version` flag can be used to display the current build version.

```bash
go run ./cmd/api -version
```
