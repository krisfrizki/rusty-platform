# PHASE 2

# ATTENDIX MVP

## Goal

Membuat produk Attendix pertama yang bisa digunakan perusahaan sungguhan

## Output akhir

```
Employee Management

Attendance

Shift Management

Leave Management

Dashboard

Organization Integration

Role Permission Integration
```

## Yang belum dibangun

```
Payroll

Recruitment

Performance Review

Training

Asset Management

Mobile Apps
```

# EPIC 15

# ATTENDIX DOMAIN FOUNDATION

## Goal

Menambahkan domain Attendix ke platform.

## Entity Utama

```
Employee

Shift

Attendance

Leave

Holiday
```

## Task 15.1

## Attendix Database Design

Schema :

```
attendix
```

Tabel :

```
employees

shifts

employee_shifts

attendances

leave_types

leave_requests

holidays
```

Checklist :

```
☐ ERD selesai
☐ Relasi selesai
☐ Naming final
```

## Task 15.2

## Employee Table

Entity :

```
Employee
```

Kolom minimum :

```sql
id

organization_id

branch_id

employee_number

full_name

email

phone

position

join_date

status

created_at

updated_at

deleted_at
```

Status :

```
active

inactive
```

Checklist :

```
☐ Migration dibuat
☐ Repository dibuat
☐ Service dibuat
```

## Task 15.3

## Shift Table

Kolom :

```sql
id

organization_id

name

start_time

end_time
```

Contoh :

```
Pagi

Siang

Malam
```

Checklist :

```
☐ Shift entity selesai
```

## Task 15.4

## Attendance Table

Kolom :

```sql
id

employee_id

clock_in

clock_out

status

notes
```

Status :

```
present

late

absent
```

Checklist :

```
☐ Attendance entity selesai
```

## Task 15.5

## Leave Request Table

Kolom :

```sql
id

employee_id

leave_type_id

start_date

end_date

status

reason
```

Status :

```
pending

approved

rejected
```

Checklist :

```
☐ Leave entity selesai
```

# EPIC 16

# EMPLOYE MANAGEMENT

## Goal

Perusahaan dapat mengelola karyawan

## Task 16.1

## Employee CRUD API

Endpoint :

```
GET /employees

GET /employees/{id}

POST /employees

PUT /employees/{id}

DELETE /employees/{id}
```

Checklist :

```
☐ CRUD selesai
```

## Task 16.2

## Employee Validation

Validasi :

```
Email unique

Employee number unique
```

Checklist :

```
☐ Validation berjalan
```

## Task 16.3

## Employee Search

Filter :

```
Name

Department

Status
```

Checklist :

```
☐ Search berjalan
```

# EPIC 17

# SHIFT MANAGEMENT

## Goal

Mengatur jam kerja

## Task 17.1

## Shift CRUD

Endpoint :

```
GET /shifts

POST /shifts

PUT /shifts/{id}

DELETE /shifts/{id}
```

Checklist :

```
☐ Shift CRUD selesai
```

## Task 17.2

## Employee Shift Assignment

Enpoint :

```
POST /employee-shifts
```

Flow :

```
Employee

↓

Assign Shift

↓

Saved
```

Checklist :

```
☐ Assignment berjalan
```

# EPIC 18

# ATTENDANCE MANAGEMENT

## Goal

Mencatat kehadiran.

## Task 18.1

## Manual Check in

Endpoint :

```
POST /attendance/check-in
```

CHecklist :

```
☐ Check in berjalan
```

## Task 18.2

## Manual Check Out

Endpoint :

```
POST /attendance/check-out
```

Checklist :

```
☐ Check out berjalan
```

## Task 18.3

## Attendance History

Endpoint :

```
GET /attendance
```

Filter :

```
Date

Employee
```

Checklist :

```
☐ History berjalan
```

# EPIC 19

# LEAVE MANAGEMENT

## Goal

Mengelola cuti.

## Task 19.1

## Leave Request

Endpoint :

```
POST /leave-requests
```

Checklist :

```
☐ Leave request berjalan
```

## Task 19.2

## Leave Approval

Endpoint :

```
POST /leave-requests/{id}/approve
```

Checklist :

```
☐ Approval berjalan
```

## Task 19.3

## Leave Rejection

Endpoint :

```
POST /leave-requests/{id}/reject
```

Checklist :

```
☐ Reject berjalan
```

# EPIC 20

# ATTENDIX FRONTEND

## Goal

Membuat UI yang bisa dipakai customer

Halaman :

```
Dashboard

Employees

Shifts

Attendance

Leave Requests

Settings
```

Checklist :

```
☐ Semua halaman tersedia
```

# EPIC 21

# ATTENDIX MVP DEPLOYMENT

## Goal

Attendix Online.

Domain :

```
attendix.rustyamigos.com
```

Checklist :

```
☐ Deployment berhasil
☐ HTTPS aktif
☐ Backup aktif
```

## PHASE 2 COMPLETION CRITERIA

```
☑ Employee Management

☑ Shift Management

☑ Attendance

☑ Leave

☑ Dashboard

☑ Deploy Production
```

## Output Phase 2

Pada akhir fase ini Rusty Amigos akan memiliki :

```
Rusty Account

Attendix MVP
```

Yang sudah bisa mulai :

- dipresentasikan ke calon customer
- digunakan perusahaan kecil
- diuji di dunia nyata
- dan yang paling penting, menghasilkan feedback nyata

Note :

```
Sebagai Lead Architect, setelah Phase 2 selesai aku tidak akan langsung membangun Flexora. Kita akan masuk ke Phase 3: Customer Validation & Product-Market Fit, karena sebelum menambah produk baru, kita harus memastikan Attendix benar-benar menyelesaikan masalah pelanggan dan memiliki arah yang jelas berdasarkan penggunaan nyata. Itu justru fase yang paling menentukan masa depan Rusty Amigos.
```
