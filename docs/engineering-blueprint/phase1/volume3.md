# VOLUME 3

## Objective

Membangun platform inti yang akan dipakai semua produk Rusty Amigos

Output akhir volume 3 :

```
User bisa register

User bisa login

User bisa logout

User bisa membuat organisasi

User bisa mengundang anggota

User bisa menerima undangan

Role berjalan

Permission berjalan

JWT berjalan

Refresh Token berjalan
```

## EPIC 7

## AUTH MODULE

## Goal

Membangunn identitas tunnggal seluruh ekosistem

## Gambaran besar

Nanti :

```
Attendix
Flexora
Future Product
```

Semua menggunakan :

```
Rusty Account
```

Contoh :

```
user@company.com
        │
        ▼
Rusty Account
        │
        ├── Attendix
        ├── Flexora
        └── Future Apps
```

## Auth Domain

Enitity utama :

```
User
Session
RefreshToken
Role
Permission
```

## Task 7.1

## User Table

Objective :

```
Menyimpan identitas pengguna
```

Buat migration :

```
migrations/auth
```

Tabel :

```
auth.users
```

Kolom :

```sql
id UUID PRIMARY KEY

email VARCHAR(255) UNIQUE

password_hash TEXT

email_verified BOOLEAN

status VARCHAR(50)

last_login_at TIMESTAMP

created_at TIMESTAMP

updated_at TIMESTAMP

deleted_at TIMESTAMP
```

status :

```
active
inactive
suspended
```

Checklist :

```
☐ Migration dibuat
☐ Table dibuat
☐ Unique email dibuat
```

## Task 7.2

## Refresh Token Table

Tabel :

```
auth.refresh_tokens
```

Kolom :

```sql
id UUID

user_id UUID

token_hash TEXT

expires_at TIMESTAMP

revoked_at TIMESTAMP

created_at TIMESTAMP
```

Kenapa?
Karena JWT tidak bisa dicabut.
Refresh token bisa.

Checklist :

```
☐ FK ke users
☐ Index dibuat
```

## Task 7.3

## Session Table

Tabel :

```
auth.sessions
```

Kolom :

```sql
id UUID

user_id UUID

ip_address

user_agent

last_activity_at

created_at
```

Tujuan :

Melihat :

```
User login dari mana
```

Checklist :

```
☐ Session table dibuat
```

## Task 7.4

## User Repository

Folder :

```
internal/auth/repository
```

interface :

```Go
type UserRepository interface {
    Create(...)
    FindByEmail(...)
    FindByID(...)
    Update(...)
}
```

Checklist :

```
☐ Interface dibuat
☐ Implementation dibuat
```

## Task 7.5

## Register Service

Folder :

```
internal/auth/service
```

Flow :

```
Request
↓
Validate
↓
Check Email
↓
Hash Password
↓
Create User
↓
Response
```

Checklist :

```
☐ Email validation
☐ Duplicate email check
☐ Password hashing
```

## Task 7.6

## Login Service

Flow :

```
Email
Password
↓
Find User
↓
Verify Password
↓
Generate JWT
↓
Generate Refresh Token
↓
Save Refresh Token
↓
Return Token
```

Checklist :

```
☐ Login berjalan
☐ JWT dibuat
☐ Refresh token dibuat
```

## Task 7.7

## JWT Service

Folder :

```
shared/auth
```

Fungsi :

```Go
GenerateAccessToken()

ValidateAccessToken()
```

Claim :

```json
{
  "sub": "user_id",
  "email": "user@email.com"
}
```

Checklist :

```
☐ JWT valid
☐ Expired support
```

## Task 7.8

## Auth API

Endpoint :

```
POST /api/v1/auth/register

POST /api/v1/auth/login

POST /api/v1/auth/logout

POST /api/v1/auth/refresh

GET /api/v1/auth/me
```

Checklist :

```
☐ Semua endpoint berjalan
```

# EPIC 7 COMPLETE

## Output :

```
User bisa login
User bisa register
```

# EPIC 8

# ORGANIZATION MODULE

## Goal

Mendukung multi-tenant.

kenapa?
karena target kita :

```
1 akun
bisa mengelola
banyak perusahaan
```

Contoh :

```
Kris

├── PT Maju Jaya
├── PT Rusty Indonesia
└── Toko Sejahtera
```

## Organization Domain

Entity :

```
Organization

Member

Invitation

Branch

Department
```

## Task 8.1

## Organization Table

Tabel :

```
organization.organizations
```

Kolom :

```sql
id UUID

name

slug

owner_id

created_at

updated_at

deleted_at
```

Checklist :

```
☐ Table dibuat
☐ Slug unique
```

## Task 8.2

## Organization Members

Tabel :

```
organization.organization_members
```

Kolom :

```sql
id UUID

organization_id

user_id

status

joined_at
```

Status :

```
active
inactive
```

Checklist :

```
☐ FK dibuat
☐ Index dibuat
```

## Task 8.3

## Organization Invitation

Tabel :

```
organization.invitations
```

Kolom :

```sql
id UUID

organization_id

email

invited_by

status

expires_at

created_at
```

Status :

```
pending
accepted
expired
cancelled
```

Checklist :

```
☐ Invitation table dibuat
```

## Task 8.4

## Create Organization

Endpoint :

```
POST /api/v1/organizations
```

Flow :

```
User Login
↓
Create Organization
↓
Become Owner
↓
Create Membership
```

Checklist :

```
☐ Organization berhasil dibuat
```

## Task 8.5

## Invite Member

Enpoint :

```
POST /api/v1/organizations/{id}/invite
```

Flow :

```
Owner
↓
Invite Email
↓
Create Invitation
↓
Send Notification (placeholder)
```

Checklist :

```
☐ Invitation berhasil dibuat
```

## Task 8.6

## Accept Invitation

Endpoint :

```
POST /api/v1/invitations/accept
```

Flow :

```
User Login
↓
Accept
↓
Membership Created
```

Checklist :

```
☐ Membership dibuat
```

# EPIC 8 COMPLETE

## Output

```
Multi Tenant berjalan
```

# EPIC 9

# ROLE BASED ACCESS CONTROL (RBAC)

Ini pondasi semua domain.
Attendix akan memakai ini.
Felxora akan memakai ini.

## RBAC domain.

Entity :

```
Role

Permission

RolePermission

MemberRole
```

## Task 9.1

## Roles Table

Tabel :

```
auth.roles
```

Kolom :

```sql
id UUID

name

description

created_at
```

Contoh :

```
Owner
Admin
Manager
Employee
```

## Task 9.2

## Permission Table

Tabel :

```
auth.permissions
```

Contoh :

```
employee.read

employee.create

employee.update

employee.delete
```

Checklist :

```
☐ Permissions dibuat
```

## Task 9.3

## Role Permission

Tabel :

```
auth.role_permissions
```

Relasi :

```
Role
↔
Permission
```

Checklist :

```
☐ Mapping berjalan
```

## Task 9.4

## Member Roles

Tabel :

```
organization.member_roles
```

Relasi :

```
Organization Member
↔
Role
```

Checklist :

```
☐ Member role berjalan
```

## Task 9.5

## Permission Middleware

Buat Middleware :

```
RequirePermission(...)
```

Contoh :

```go
RequirePermission(
 "employee.create",
)
```

Checklist :

```
☐ Middleware berjalan
```

# VOLUME 3 COMPLETION CRITERIA

Semua harus hijau :

```
☐ Register
☐ Login
☐ Logout
☐ Refresh Token
☐ JWT
☐ Create Organization
☐ Invite Member
☐ Accept Invitation
☐ Role
☐ Permission
☐ Permission Middleware
```

# Hasil Akhir Volume 3

Pada titik inni Rusty Amigos memiliki sesuatu yag sangat berharga :

```
Rusty Account
```

dan seluruh produk di masa depan akan berdiri diatasnya :

```
Rusty Account
        │
        ├── Attendix
        ├── Flexora
        ├── CRM
        ├── Project Management
        └── Future Products
```

Note :

```
Sebagai Lead Architect, aku bahkan tidak akan mengizinkan pembangunan Attendix sebelum Volume 3 selesai dan stabil. Karena Auth + Organization + RBAC adalah fondasi seluruh ekosistem Rusty Amigos. Setelah Volume 3 selesai, barulah kita masuk ke Volume 4 : Rusty Account Frontend + Deployment + HArdening, yang akan menutup seluruh fase 1
```
