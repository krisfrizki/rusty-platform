# VOLUME 4

## Objective

Mengubah backennd yang sudah kuta bangun menjadi platform yang benar-benar bisa digunakan.

Output akhir :

```
Rusty Account Frontend berjalan

Register berjalan

Login berjalan

Organization Management berjalan

Deployment berjalan

SSL berjalan

Backup berjalan

Monitoring dasar berjalan
```

# EPIC 10

# RUSTY ACCOUNT FRONTEND

## Goal

Membangun portal utama seluruh ekosistem Rusty Amigos

## Kenapa Penting?

Karena nanti :

```
account.rustyamigos.com
```

akan menjadi gerbang masuk seluruh produk

## Task 10.1

## Bootstrap Next.js

Objective :
Membuat forntend foundation.

Action :

```
cd frontend
```

Buat Aplikasi :

```
npx create-next-app@latest rusty-account
```

Pilihan :

```
TypeScript     : Yes
ESLint         : Yes
Tailwind       : Yes
App Router     : Yes
src directory  : Yes
```

Checklist :

```
☐ Next.js berhasil dibuat
☐ npm run dev berhasil
☐ halaman default tampil
```

## Task 10.2

## Frontend FOlder Structure

Target :

```
frontend/rusty-account

src

├── app
├── components
├── features
├── hooks
├── lib
├── services
├── stores
├── types
└── utils
```

Kenapa?
Karena nanti aplikasi akan berkembang

Checklist :

```
☐ Struktur dibuat
☐ Tidak ada folder random
```

## TAsk 10.3

## Design System Foundation

Buat :

```
src/components/ui
```

Komponen awal :

```
Button
Input
Card
Modal
Badge
Table
```

Checklist :

```
☐ Button dibuat
☐ Input dibuat
☐ Card dibuat
```

## Task 10.4

## Authentication Pages

Halaman :

```
/login

/register

/forgot-password
```

Checklist :

```
☐ Login page
☐ Register page
☐ Forgot password page
```

## Task 10.5

## Dashboard Layout

Buat :

```
/dashboard
```

Layout :

```
Sidebar

Topbar

Content Area
```

Checklist :

```
☐ Layout responsive
```

## Task 10.6

## Organization Pages

Halaman :

```
/organizations

/organizations/create

/organizations/settings
```

Checklist :

```
☐ List organization
☐ Create organization
☐ Organization settings
```

## Task 10.7

## Invitation Pages

Halaman :

```
/invitations

/members
```

Checklist :

```
☐ Invite member
☐ Member list
```

# EPIC 10 COMPLETE

## Output

```
Rusty Account UI berjalan
```

# EPIC 11

# VPS DEPLOYMENT

## Goal

Membuat Rusty Platform online.

## Task 11.1

## VPS Previsioning

Provider yang direkomendasikan

- Hetzner
- Contabo
- DIgitalOcean

Spesifikasi awal :

```
2 vCPU

4 GB RAM

80 GB SSD
```

Checklist :

```
☐ VPS dibeli
☐ OS Ubuntu terinstall
```

## Task 11.2

## Server Hardening

Install :

```
ufw
fail2ban
```

Konfigurasi :

```
SSH Only
Disable Root Login
```

Checklist :

```
☐ Root login dimatikan
☐ Firewall aktif
```

## Task 11.3

## Docker Installation

Install :

```
Docker
Docker Compose
```

Checklist :

```
☐ Docker aktif
☐ Compose aktif
```

## Task 11.4

## PostgreSQL Deployment

Container :

```
postgres
```

Volume :

```
postgres_data
```

Checklist :

```
☐ Data persistent
```

## Task 11.5

## API Deployment

Container :

```
rusty-api
```

Checklist :

```
☐ API hidup
☒ Panic
☒ Error startup
```

Semua harus bersih

## Task 11.6

## Frontend Deployment

Container :

```
rusty-account
```

Checklist :

```
☐ Frontend hidup
```

## Task 11.7

## Nginx Reverse Proxy

Domain :

```
account.rustyamigos.com
```

Routing :

```
80
↓
443
↓
Frontend
```

Checklist :

```
☐ Routing berhasil
```

## Task 11.8

## SSL

Gunakan :

```
Let's Encrypt
```

Checklist :

```
☐ HTTPS aktif
```

# EPIC 11 COMPLETE

## Output

```
Rusty Account Online
```

# EPIC 12

# OBSERVABILITY FOUNDATIONN

## Goal

Mengetahui kondisi sistem sebelum pelanggan mengeluh.

## Task 12.1

## Request Logging

Semua request dicatat

Log :

```
Method

Path

Status

Duration
```

Checklist :

```
☐ Logging aktif
```

## Task 12.2

## Error Logging

Catat :

```
panic

database error

unexpected error
```

Checklist :

```
☐ Error log aktif
```

## Task 12.3

## Health Endpoint

Endpoint :

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
☐ Health endpoint aktif
```

## Task 12.4

## Readiness Endpoint

Endpoint :

```
GET /ready
```

Verifikasi :

```
Database

Config

Dependencies
```

Checklist :

```
☐ Readiness aktif
```

# EPIC 13

# BACKUP & RECOVERY

Ini bagian yang hampir semua developer pemula lupa

## Goal

Data tidak hilag ketika server mati

## Task 13.1

## Database Backup

Buat script :

```
pg_dump
```

Frekuensi :

```
Harian
```

Checklist :

```
☐ Backup otomatis
```

## Task 13.2

## Backup Retention

Simpan :

```
7 harian

4 mingguan

3 bulanan
```

Checklist :

```
☐ Retention berjalan
```

## Task 13.3

## Recovery Test

Simulasi :

```
Database hilang
```

Restore.

Checklist :

```
☐ Restore berhasil
```

# EPIC 14

# PHASE 1 HARDENING

## Memastikan fondasi cukup kuat untuk menjadi basis Attendix

## Task 14.1

## API Review

Review :

```
Naming

Folder

DTO

Repository

Service
```

Checklist :

```
☐ Konsisten
```

## Task 14.2

## Security Review

Periksa :

```
JWT

Password Hash

CORS

SQL Injection

XSS
```

CHecklist :

```
☐ Aman
```

## Task 14.3

## Performance Baseline

Uji :

```
Register

Login

Create Organization
```

Target :

```
< 300 ms
```

untuk local environtment

Checklist :

```
☐ Baseline dicatat
```

## Task 14.4

## Technical Debt Review

Buat :

```
docs/tech-debt.md
```

isi :

```
Known Issues

Future Improvements

Refactor Candidates
```

Checklist :

```
☐ Technical debt terdokumentasi
```
