# Go REST API Template

Template REST API menggunakan Golang dan Gin.

## Requirements

- [Go](https://go.dev/dl/)
- [Git](https://git-scm.com/)

## Setup

**1. Clone repository**

```bash
git clone https://github.com/USERNAME/go-backend-template.git
cd go-backend-template
```

**2. Install dependencies**

```bash
go mod download
```

**3. Setup environment**

Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

Linux/macOS:

```bash
cp .env.example .env
```

**4. Run application**

```bash
go run ./cmd/server
```

## Test API

Jika server berjalan pada port `8080`, akses endpoint berikut melalui browser atau Postman:

```http
GET http://localhost:8080/health
```

## Run Tests

```bash
go test ./...
go vet ./...
```
