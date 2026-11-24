# Go Clean Architecture REST API Boilerplate

Boilerplate backend REST API menggunakan bahasa pemrograman **Go (Golang)** yang menerapkan prinsip **Clean Architecture (Uncle Bob)** dan didukung oleh **Gin Gonic** serta ORM **GORM (Auto Migrate)** dengan database **PostgreSQL**.

Repository ini dirancang sebagai fondasi (*starter template*) modular yang mudah dikembangkan, mudah diuji (*testable*), dan memiliki pemisahan tanggung jawab yang jelas (*separation of concerns*).

---

## 🚀 Tech Stack

* **Language**: Go (v1.21+)
* **Web Framework**: [Gin Gonic](https://github.com/gin-gonic/gin)
* **ORM**: [GORM](https://gorm.io/)
* **Database Driver**: [PostgreSQL (gorm.io/driver/postgres)](https://github.com/go-gorm/postgres)
* **Environment Loader**: [Godotenv](https://github.com/joho/godotenv)
* **Database Migration**: GORM Auto Migrate

---

## 📁 Struktur Direktori

```text
go-clean-architecture/
├── cmd/
│   └── server/
│       └── main.go                 # Entry point aplikasi (wiring/dependency injection)
├── docs/                           # Dokumentasi API (Swagger / OpenAPI / Postman)
├── internal/                       # Private application code
│   ├── config/                     # Load environment variables (.env)
│   ├── domain/                     # Core Business: Entity/Model GORM & Contract Interfaces
│   ├── service/                    # Business Logic / Use Cases
│   ├── repository/                 # Data Access Layer (Query GORM)
│   └── delivery/                   # Presentation Layer
│       └── http/
│           ├── dto/                # Request & Response body validation
│           ├── handler/            # Controller / HTTP Handlers
│           ├── middleware/         # Middleware (Auth, CORS, Logger)
│           └── router/             # Definisi endpoint & route grouping
├── pkg/                            # Reusable / Public library
│   ├── database/                   # Koneksi DB & helper GORM AutoMigrate
│   ├── response/                   # Standarisasi JSON response API
│   └── utils/                      # Helper umum (hashing, JWT, string helper)
├── .env.example                    # Template konfigurasi environment
├── .gitignore
├── go.mod
├── go.sum
└── README.md
```

---

1. **Router & Middleware**: Menerima request HTTP dan menyaring otentikasi/CORS.
2. **Handler**: Mengurai parameter, payload JSON, dan memvalidasinya via **DTO**.
3. **Service**: Menjalankan aturan bisnis (*business logic*).
4. **Repository**: Melakukan operasi database (CRUD) menggunakan **GORM**.
5. **Domain**: Berperan sebagai entitas data dan jembatan kontrak *interface* antar layer.

---

## 🛠️ Panduan Memulai (Getting Started)

### 1. Prasyarat
* Go 1.21 atau versi yang lebih baru terpasang di komputer.
* Database PostgreSQL yang sedang berjalan.

### 2. Salin Konfigurasi Environment
Salin file `.env.example` menjadi `.env`:
```bash
cp .env.example .env
```
Sesuaikan kredensial database di dalam file `.env`:
```env
APP_PORT=8080
APP_ENV=development

DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=your_password
DB_NAME=clean_arch_db
DB_SSLMODE=disable
```

### 3. Unduh Dependensi
```bash
go mod tidy
```

### 4. Menjalankan Aplikasi
```bash
go run ./cmd/server/main.go
```

Aplikasi akan berjalan di `http://localhost:8080`.  
Cek kesehatan server melalui endpoint: `GET http://localhost:8080/health`.

---
