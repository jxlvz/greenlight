# GreenlightAPI

GreenlightAPI is a JSON API written in Go for managing movie information.

It is built step by step by following the _Let’s Go Further_ book by Alex Edwards, as a practical and advanced way to learn how to develop professional, production-ready APIs with Go.

## Features

- Idiomatic, flexible project structure
- JSON responses with robust error handling
- Strong request parsing and validation
- SQL migrations for database schema management
- Database operations with timeouts and connection pooling
- Advanced resource actions (e.g., partial updates with optimistic concurrency control)
- Filtering, sorting, and pagination
- Full-text search with PostgreSQL
- Structured JSON logging
- Per-client rate limiting
- Safe background task execution
- Graceful shutdown with completion of in-flight tasks
- Email sending with embedded templates
- Secure user activation and password reset flows
- Authentication with bearer tokens and JWTs
- Permission-based authorization
- CORS support for JavaScript frontends
- Exposed application metrics (memory usage, DB pool stats, response counts, etc.)
- Automated builds, audits, and versioned binaries
- Deployment on Linux servers (e.g. DigitalOcean) with systemd service management
