# PHASE 6

# BUSINESS IDENTITY PLATFORM

Ini menurutku harus dibangun lebih dulu.

Kenapa?

Karena :

```
Business Profile
```

akan menjadi :

```
LinkedIn Profile
```

versi bisnis

Dan ini bisa digunakan oleh semua user bahkan sebelum fitur premium

## Output Phase 6

Setelah selesai :

```
User dapat membuat bisnis

User dapat membuat halaman bisnis

User dapat menampilkan produk

User dapat menampilkan jasa

User dapat membangun tim
```

# EPIC 41

# BUSINESS PROFILE

## Goal

Setiap bisnis memiliki identitas digital

## Task 41.1

## Business Entity

Tabel :

```
flexora.businesses
```

Kolom :

```sql
id UUID

business_code

slug

name

description

industry

phone

email

website

logo_url

cover_url

created_by

created_at

updated_at
```

Checklist :

```
☐ Migration selesai
☐ Repository selesai
☐ Service selesai
```

## Task 41.2

## Business Slug

Contoh :

```
rusty-amigos
```

Public URL :

```
flexora.app/business/rusty-amigos
```

Checklist :

```
☐ Slug unique
☐ Slug validation
```

## Task 41.3

## Business Verification

Status :

```
pending

verified

rejected
```

Tujuan :

```
Verified Business
```

Checklist :

```
☐ Verification workflow selesai
```

# EPIC 42

# BUSINESS SHOWCASE

## Goal

Menampilkan produk dan jasa

## Task 42.1

## Products

Tabel :

```
flexora.products
```

Kolom :

```sql
id

business_id

name

description

price

image_url

is_published
```

Checklist :

```
☐ Product entity selesai
```

## Task 42.2

## Services

Tabel :

```
flexora.services
```

Kolom :

```sql
id

business_id

name

description

price

duration
```

Checklist :

```
☐ Service entity selesai
```

## Task 42.3

## Portfolio

Tabel :

```
flexora.portfolios
```

Tujuan :
Menampilkan hasil kerja

Checklist :

```
☐ Portfolio berjalan
```

# EPIC 43

# TEAM MANAGEMENT

Ini salah satu inti Flexora

## Filosofi

Satu akun,
Banyak bisnis

Contoh :

```
Udin

Owner
Rusty Amigos

Manager
ABC Coffee

Staff
XYZ Studio
```

## Task 43.1

## Business Membership

Tabel :

```
flexora.business_members
```

Kolom :

```sql
id

business_id

user_id

role_id

joined_at
```

Checklist :

```
☐ Membership berjalan
```

## Task 43.2

## Join Business Request

Tabel :

```
flexora.join_requests
```

Flow :

```
Input Business ID

↓

Request Join

↓

Approval

↓

Become Member
```

Checklist :

```
☐ Join request berjalan
```

## Task 43.3

## Custom Position

Ini penting
Karena disebutkan

```
Leader boleh menentukan nama jabatan sendiri
```

Contoh :

```
CEO

Head of Marketing

Supervisor

Barista

Designer

Captain
```

Tabel :

```
flexora.positions
```

Checklist :

```
☐ Position custom berjalan
```

# EPIC 44

# PUBLIC BUSINESS PAGE

## Goal

Semua bisnis punya halaman publik

URL :

```
flexora.app/business/{slug}
```

Halaman :

```
Logo

Cover

About

Products

Services

Portfolio

Team
```

Checklist :

```
☐ Public page online
```

# EPIC 45

# BUSINESS DASHBOARD

## Goal

Owner memiliki dashboard bisnis

Widget :

```
Profile Completion

Members

Products

Services

Portfolio Views
```

Checklist :

```
☐ Dashboard tersedia
```

# EPIC 46

# BUSINESS SEARCH

Ini bagian yang sangat penting.
karena akan menjadi growth engine

## Task 46.1

## Search Business

Cari :

```
Coffee Shop

Web Agency

Barbershop
```

Checklist :

```
☐ Search berjalan
```

## Task 46.2

## Industry Filter

Filter :

```
Restaurant

Agency

Consulting

Retail

Manufacturing
```

Checklist :

```
☐ Filter berjalan
```

# EPIC 47

# FLEXORA FREE PLAN

Ini yang membedakan Flexora dan ERP

Free features :

```
Business Profile

Public Business Page

Products Showcase

Services Showcase

Portfolio

Join Business

Member Management

Basic Dashboard
```

Batasan :

```
5 Member

10 Product

10 Service

10 Portfolio
```

Checklist :

```
☐ Free plan selesai
```

## Phase 6 Completion Criteria

```
☑ Business Profile

☑ Public Business Page

☑ Products Showcase

☑ Services Showcase

☑ Portfolio

☑ Membership

☑ Join Request

☑ Search Business

☑ Free Plan
```

## Output Phase 6

Pada akhir fase ini FLexora sudah bisa digunakan oleh :

```
Freelancer

UMKM

Agency

Coffee Shop

Startup

Konsultan
```

Bahkan tanpa membeli fitur premium.
Dan ini penting karena :

- Attendix mencari revenue
- Flexora mencari network effect
