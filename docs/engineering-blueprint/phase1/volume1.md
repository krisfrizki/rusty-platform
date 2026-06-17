# VOLUME 1

# HASIL AKHIR VOLUME 1 :

```
rusty-platform

├── backend
├── frontend
├── docs
├── infra
├── scripts
└── .github
```

Dan :

```
Dokumentasi selesai
Struktur project final
Backend bootstrap selesai
```

# EPIC 1

# PROJECT INITIALIZATION

## Tujuan

Menciptakan workspace utama yang akan menjadi rumah seluruh produk Rusty Amigos.

## Kenapa ini penting?

karena 90% masalah software besar muncul bukan dari coding

tetapi dari :

```
struktur project
standar tim
arsitektur
```

yang berubah-ubah

## Task 1.1

## Membuat Repository

Objective :

```
Membuat repository utama
```

Action

```
Buka github
```

klik :

```
New Repository
```

isi :

```
Repository Name

rusty-platform
```

visibility :

```
Private
```

Checklist :

```
☐ Repository dibuat
☐ README dibuat
☐ .gitignore dibuat
☐ License dikosongkan dulu
```

Definition of done :

```
Repository dapat di-clone.
```

## Task 1.2

## Clone Repository

Action

```
git clone https://github.com/<username>/rusty-platform.git
```

Masuk :

```
cd rusty-platform
```

Buka VSCode :

```
code .
```

Checklist :

```
☐ Repository berhasil di clone
☐ VSCode berhasil dibuka
```

Definition of Done :

```
workspace terbuka
```

## Task 1.3

## Root Directory Structure

Objective :

```
Membuat struktur project global
```

Action :

```
backend
frontend
docs
infra
scripts
.github
```

Struktur :

```
rusty-platform

├── backend
├── frontend
├── docs
├── infra
├── scripts
└── .github
```

Penjelasan :

Backend

```
semua kode Go
```

Frontend

```
semua aplikasi NextJS
```

Docs

```
Dokumentasi
```

Infra

```
Docker
Nginx
Deployment
```

Scripts

```
automation
```

.github

```
Github actions
```

Checklist :

```
☐ Semua folder dibuat
☐ Tidak ada folder tambahan
```

Definition of Done

```
Root project final
```

## Task 1.4

## Git Strategy

Objective :

```
Mencegah kekacauan source control
```

buat :

```
docs/git-strategy.md
```

isi :

```
main
develop
feature/*
```

Rule :

main

```
production

tidak boleh coding langsung
```

develop

```
Development Branch
```

feature

```
Feature branch
```

contoh :

```
feature/auth-login

feature/auth-register

feature/organization-create
```

Checklist :

```
☐ Dokumen dibuat
☐ Rule ditulis
```

Definition of Done :

```
Branch strategy terdokumentasi.
```

## Task 1.5

## Initial Commit

Action

```
git add .
```

```
git commit -m "chore: initialize project structure"
```

```
git push
```

checklist :

```
☐ Commit berhasil
☐ Push berhasil
```

# EPIC 1 COMPLETED

## Output :

```
Repository siap digunakan.
```

# EPIC 2

# DOCUMENTATION & STANDARDS

## Tujuan

Semua keputusan proyek harus tertulis,
bukan berada di kepala developer

## Task 2.1

## Vision Document

Buat :

```
docs/vision.md
```

isi :

Apa itu Rusty Amigos

```
Multi Product SaaS Ecosystem
```

Produk saat ini

```
Rusty Account
Attendix
Flexora
```

Produk masa depan

```
CRM
Project Management
Future SaaS
```

Checklist :

```
☐ Visi perusahaan ditulis
☐ Visi produk ditulis
☐ Future vision ditulis
```

## Task 2.2

## Roadmap Document

buat :

```
docs/roadmap.md
```

isi :

```
Phase 1 Foundation

Phase 2 Attendix MVP

Phase 3 Validation

Phase 4 Billing

Phase 5 Flexora Foundation

Phase 6 Notification

Phase 7 Analytics

Phase 8 Mobile

Phase 9 Expansion

Phase 10 Ecosystem
```

checklist :

```
☐ Semua phase ditulis
☐ Goal setiap phase ditulis
```

## Task 2.3

## Architecture Document

buat :

```
docs/architecture.md
```

isi :

Frontend

```
Rusty Website

Rusty Account

Attendix

Flexora
```

Backend

```
Auth

Organization

Billing

Notification

Attendix

Flexora
```

Database

```
auth

organization

billing

attendix

flexora

analytics
```

Checklist :

```
☐ Frontend architecture ditulis
☐ Backend architecture ditulis
☐ Database architecture ditulis
```

## Task 2.4

## Coding Convention

Buat :

```
docs/conventions.md
```

isi :

Database

```
snake_case
```

API

```
/api/v1
```

Go Package

```
lowercase
```

Struct

```
type User struct
```

Checklist :

```
☐ Naming convention ditulis
☐ API convention ditulis
☐ Database convention ditulis
```

## Task 2.5

## ADR (Architecture Decision Record)

Buat :

```
docs/adr
```

Lalu :

```
001-go.md

002-postgresql.md

003-modular-monolith.md
```

contoh :

```
Kenapa memilih Go

Kenapa memilih PostgreSQL

Kenapa memilih Modular Monolith
```

Checklist :

```
☐ ADR dibuat
☐ Alasan keputusan ditulis
```

# EPIC 2 COMPLETE

## Output :

```
Semua keputusan penting terdokumentasi.
```

# EPIC 3

# BACKEND BOOTSTRAP

## Tujuan :

1. Menyiapkan Backend Go
2. Belum membuat Auth
3. Belum membuat User
4. Belum membuat Login

## Task 3.1

## Initialize Backend Module

masuk :

```
cd backend
```

jalankan :

```
go mod init github.com/<username>/rusty-platform
```

Checklist :

```
☐ go.mod muncul
☐ module name benar
```

Definition of Done

```
go.mod berhasil dibuat
```

## Task 3.2

## Backend Directory Structure

Buat :

```
backend

├── cmd
├── internal
├── shared
├── migrations
├── tests
└── configs
```

Checklist :

```
☐ Semua folder dibuat
```

## Task 3.3

## API Entry Point

Buat :

```
backend/cmd/api
```

File :

```
main.go
```

isi sementara :

```Go
package main

import "fmt"

func main() {
    fmt.Println("Rusty Platform API")
}
```

Checklist :

```
☐ main.go dibuat
☐ go run berhasil
```

## Task 3.4

## Internal Module Structure

Buat :

```
auth
organization
billing
notification
attendix
flexora
```

Di dalam masing-masing :

```
domain
repository
service
handler
dto
routes
```

Contoh :

```
internal/auth

├── domain
├── repository
├── service
├── handler
├── dto
└── routes
```

Checklist :

```
☐ Semua module dibuat
☐ Struktur sama
```

## Task 3.5

## Shared Structure

Buat :

```
shared

├── config
├── database
├── logger
├── middleware
├── errors
└── response
```

Checklist :

```
☐ Shared structure dibuat
```

## Task 3.6

## Dependency Installation

install :

```
go get github.com/jackc/pgx/v5
go get github.com/pressly/goose/v3
go get github.com/golang-jwt/jwt/v5
go get golang.org/x/crypto/argon2
```

Checklist :

```
☐ Dependency berhasil di install
☐ go.mod terupdate
```

# VOLUME 1 COMPLETION CRITERIA

```
☐ Repository siap
☐ Dokumentasi siap
☐ ADR siap
☐ Go module siap
☐ Backend structure siap
☐ Shared structure siap
☐ Internal module siap
☐ Semua commit ke Github
```
