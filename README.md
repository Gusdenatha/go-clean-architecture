# Go REST API Template

Template REST API menggunakan Golang dan Gin.

## Requirements

- [Go](https://go.dev/dl/)
- [Git](https://git-scm.com/)

## Setup

**1. Install dependencies**

```bash
go mod download
```

**3. Run application**

```bash
go run ./cmd/server
```

## Test API

```http
GET http://localhost:8080/health
```

## Run Tests

```bash
go test ./...
go vet ./...
```
