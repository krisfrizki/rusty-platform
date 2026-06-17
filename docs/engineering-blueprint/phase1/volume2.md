# VOLUME 2

## Objective

Pada akhir volume 2 :

```
Docker berjalan
PostgreSQL berjalan
Migration berjalan
Config berjalan
Logger berjalan
Database connection berjalan
Health Check berjalan
```

belum ada :

```
Login
Register
User
Organization
Attendix
Flexora
```

# EPIC 4

# Infrastructure Foundation

## Goal :

Menyiapkan local development environtment yang akan identik dengan environtment production

## Kenapa penting?

Banyak startup gagal karena :

```
jalan di laptop
gagal di server
```

Kita ingin :

```
jalan di laptop
jalan di staging
jalan di production
```

dengan konfigurasi yang hampir sama

## Task 4.1

## Docker Foundation

Objective :
Semua service dijalankan melalui docker

Action

Masuk

```
cd infra
```

Buat

```
infra/

docker/

├── docker-compose.yml
├── postgres/
└── api/
```

Checklist

```
☐ Folder docker dibuat
☐ Folder postgres dibuat
☐ Folder api dibuat
```

Definition of Done

```
Struktur docker tersedia.
```

## Task 4.2

## Docker Compose

Buat :

```
infra/docker/docker-compose.yml
```

Service pertama :

```
postgres
```

Belum perlu :

```
redis
rabbitmq
minio
```

karena belum dipakai

Checklist

```
☐ docker-compose dibuat
☐ postgres service dibuat
```

## Task 4.3

## Environment Variable Strategy

Objective

```
Mencegah hardcoded configuration.
```

Buat :

```
backend/

.env.example
.env.local
```

isi :

```
APP_NAME=rusty-platform

APP_ENV=local

APP_PORT=8080

DB_HOST=localhost
DB_PORT=5432
DB_NAME=rusty_platform
DB_USER=postgres
DB_PASSWORD=password
```

Checklist

```
☐ .env.example dibuat
☐ variable dasar dibuat
```

## Task 4.4

## Git Ignore

Tambahkan :

```
.env
.env.local
```

Checklist :

```
☐ Secret tidak ikut ke repository
```

## Task 4.5

## Docker Startup Validation

Jalankan :

```
docker compose up -d
```

Verifikasi :

```
docker ps
```

Checklist :

```
☐ Container postgres hidup
☐ Tidak ada error
```

# EPIC 4 COMPLETE

## Output

```
Docker hidup
PostgreSQL hidup
```

# EPIC 5

# DATABASE FOUDATION

## Goal

Mambangunn fondasi database Rusty Amigos

## Kenapa penting?

database hampir mustahil di refactor setelah :

```
100 customer
10000 data
```

Jadi desain domain harus bennar sejak awal

## Task 5.1

## PostgresSQL Naming Strategy

buat dokumen :

```
docs/database-strategy.md
```

isi :

```
PostgreSQL

Schema:

auth
organization
billing
attendix
flexora
notification
analytics
```

Checklist

```
☐ Semua schema ditentukan
```

## Task 5.2

## Create Database

Masuk PostgreSQL

Buat:

```sql
CREATE DATABASE rusty_platform;
```

Checklist :

```
☐ Database berhasil dibuat
```

## Task 5.3

## Create Schemas

Jalankan :

```
CREATE SCHEMA auth;

CREATE SCHEMA organization;

CREATE SCHEMA billing;

CREATE SCHEMA attendix;

CREATE SCHEMA flexora;

CREATE SCHEMA notification;

CREATE SCHEMA analytics;
```

Checklist :

```
☐ Semua schema berhasil dibuat
```

## Task 5.4

## Database Convention

Buat :

```
docs/database-convention.md
```

Rule :

Table

```
snake_case
plural
```

Contoh :

```
users
organizations
subscriptions
```

Column

```
snake_case
```

Contoh :

```
created_at
updated_at
deleted_at
```

Primary key

Semua :

```
uuid
```

Checklist :

```
☐ Convention terdokumentasi
```

## Task 5.5

## UUID Strategy

Objective

```
Tidak menggunakan integer ID.
```

Kenapa?

Karena nanti :

```
Attendix
Flexora
Billing
```

akan saling terhubung

UUID lebih aman

Rule :

```sql
id UUID PRIMARY KEY
```

Checklist :

```
☐ UUID strategy ditulis
```

## Task 5.6

## Soft Delete Strategy

rule :

Semua entity bisnis memiliki :

```sql
deleted_at TIMESTAMP NULL
```

kecuali :

```
audit_logs
```

Checklist :

```
☐ Soft delete policy dibuat
```

## Task 5.7

## Audit Strategy

Rule :

```
Semua perubahann penting wajib dicatat
```

Nanti akan ada :

```
analytics.audit_logs
```

Checklist :

```
☐ Audit policy dibuat
```

# EPIC 5 COMPLETE

## Output

```
Database Strategy Final
Schema Final
Convention Final
```

# EPIC 6

# SHARED INFRASTRUCTURE

## Goal

```
Membangun komponen yang akan digunakan semua module.
```

Contoh :

```
Auth
Organization
Attendix
Flexora
```

Semuanya menggunakan :

```
config
logger
database
response
```

yang sama

## Task 6.1

## Config Module

Buat :

```
shared/config
```

File :

```
config.go
```

Objective :

Load :

```env
APP_ENV
APP_PORT

DB_HOST
DB_PORT
DB_NAME
DB_USER
DB_PASSWORD
```

Checklist :

```
☐ Config dapat dibaca
```

## Task 6.2

## Logger Module

Buat :

```
shared/logger
```

Library yang di rekomendasikan :

```
log/slog
```

(karena Go modern)

Checklist

```
☐ Logger berhasil dibuat
```

## Task 6.3

## Database Connection Module

Buat :

```
shared/database
```

File :

```
postgres.go
```

Objective :

Membuat :

```
func NewPostgres(...)
```

Checklist :

```
☐ PostgreSQL dapat terkoneksi
```

## Task 6.4

## Health Check Endpoint

Buat :

```
GET /health
```

Response :

```json
{
  "status": "ok"
}
```

Checklist :

```
☐ Endpoint berjalan
```

## Task 6.5

## Standard API Response

Buat :

```
shared/response
```

Success :

```json
{
  "success": true,
  "data": {}
}
```

Error :

```json
{
  "success": false,
  "message": "something went wrong"
}
```

Checklist :

```
☐ Standard response dibuat
```

## Task 6.6

## Error Package

Buat :

```
shared/errors
```

Contoh :

```Go
var ErrUserNotFound
var ErrUnauthorized
var ErrForbidden
```

Checklist :

```
☐ Error standard dibuat
```

## Task 6.7

## Middleware Structure

Buat :

```
shared/middleware
```

Kosong dulu.
Belum implementasi.

Struktur :

```
auth.go
logging.go
cors.go
recovery.go
```

Checklist :

```
☐ Struktur middleware dibuat
```

## Task 6.8

## Application Bootstrap

Saat :

```
go run cmd/api/main.go
```

Harus terjadi :

```
Load Config
↓
Initialize Logger
↓
Connect PostgreSQL
↓
Register Routes
↓
Start Server
```

Checklist :

```
☐ Bootstrap berjalan
☐ Tidak panic
☐ Database connect
☐ Health endpoint hidup
```

# VOLUME 2 COMPLETION CRITERIA

Sebelum masuk Auth Module, semuanya harus hijau :

```
☐ Docker berjalan
☐ PostgreSQL berjalan
☐ Database dibuat
☐ Schema dibuat
☐ Config berjalan
☐ Logger berjalan
☐ Database connection berjalan
☐ Health endpoint berjalan
☐ Standard response berjalan
☐ Error package berjalan
☐ Bootstrap berjalan
```

# Output Akhir Volume 2

Struktur proyek akan menjadi :

```
rusty-platform

├── backend
│   ├── cmd
│   ├── internal
│   ├── shared
│   ├── migrations
│   ├── tests
│   └── configs
│
├── frontend
│
├── docs
│
├── infra
│   └── docker
│
└── scripts
```

Dan yang penting :

```
Setelah Volume 2 selesai, kita sudah memiliki platform teknis yang stabil untuk mulai membangun fitur pertama yang nyata: Rusty Account (Auth + Organization + RBAC), yang akan menjadi isi utama Engineering Blueprint Phase 1 Volume 3.
```
