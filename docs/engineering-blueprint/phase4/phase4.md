# PHASE 4

# BILLING & SUBSCRIPTION PLATFORM

## Objective

Membangun sistem monetisasi yang akan dipakai
Bukan hanya Attendix
Tapi juga :

```
Attendix

Flexora

Future CRM

Future Products
```

Semua memakai billing yang sama

## Output Akhir

```
Subscription

Plan

Invoice

Payment

Usage Tracking

Billing Portal
```

# EPIC 28

# BILLING DOMAIN FOUNDATION

## Goal

Membuat fondasi billing universal

## Domain

```
Plan

Subscription

Invoice

Payment

Usage

Coupon
```

## Task 28.1

## Billing Schema

Schema :

```
billing
```

Tabel :

```
plans

subscriptions

subscription_items

invoices

invoice_items

payments

usage_records

coupons
```

Checklist :

```
☐ ERD dibuat
☐ Naming final
☐ Migration dibuat
```

## Task 28.2

## Plans Table

Tabel :

```
billing.plans
```

Kolom :

```sql
id UUID

name

code

price

currency

billing_cycle

is_active

created_at

updated_at
```

Contoh :

```
FREE

STARTER

BUSINESS
```

Checklist :

```
☐ Plan table selesai
```

## Task 28.3

## Subscriptions Table

Tabel :

```
billing.subscriptions
```

Kolom :

```sql
id UUID

organization_id

plan_id

status

started_at

expired_at

created_at
```

Status :

```
active

expired

cancelled

trialing
```

Checklist :

```
☐ Subscription selesai
```

## Task 28.4

## Invoices Table

Tabel :

```
billing.invoices
```

Kolom :

```sql
id UUID

organization_id

invoice_number

subtotal

tax

total

status

issued_at

due_date
```

Status :

```
draft

pending

paid

overdue

cancelled
```

Checklist :

```
☐ Invoice selesai
```

# EPIC 29

# PAYMENT INTEGRATION

## Goal

Menerima pembayaran dari customer

## Strategi Awal

Karena target awal indonesia.
Integrasi :
Midtrans

Kenapa?
Karena mendukung :

```
QRIS

Virtual Account

Bank Transfer

E-Wallet
```

## Task 29.1

## Payment Gateway Adapter

Folder :

```
internal/billing/payment
```

Innterface :

```go
type PaymentProvider interface {
    CreateTransaction()
    VerifyPayment()
}
```

Checklist :

```
☐ Interface dibuat
```

## Task 29.2

## Midtrans Integration

Flow :

```
Create Invoice

↓

Create Payment

↓

Redirect Customer

↓

Payment Success

↓

Webhook

↓

Update Invoice
```

Checklist :

```
☐ Payment berhasil
☐ Webhook berhasil
```

## Task 29.3

## Payment Webhook

Endpoint :

```
POST /api/v1/billing/webhooks/midtrans
```

Checklist :

```
☐ Signature validation
☐ Update invoice
```

# EPIC 30

# SUBSCRIPTION MANAGEMENT

## Goal

Mengatur lifecycle subscription.

## Task 30.1

## Upgrade Plan

Endpoint :

```
POST /subscriptions/upgrade
```

Checklist :

```
☐ Upgrade berhasil
```

## Task 30.2

## Downgrade Plan

Endpoint :

```
POST /subscriptions/downgrade
```

CHecklist :

```
☐ Downgrade berhasil
```

## Task 30.3

## Trial System

Default :

```
14 Hari
```

Checklist :

```
☐ Trial berjalan
```

## Task 30.4

## Subscription Expiration

Job :

```
Daily Scheduler
```

Flow :

```
Check Subscription

↓

Expired

↓

Limit Access
```

Checklist :

```
☐ Expiration berjalan
```

# EPIC 31

# USAGE TRACKING

## Goal

Pricing berbasis penggunaan

## Task 31.1

## Usage Records

Table :

```
billing.usage_records
```

Contoh :

```
Employee Count

Attendance Count

Storage Usage
```

Checklist :

```
☐ Usage tracking berjalan
```

## Task 31.2

## Monthly Aggregation

Job :

```
Monthly Usage Summary
```

Checklist :

```
☐ Aggregation berjalan
```

# EPIC 32

# BILLING PORTAL

## Goal

Customer dapat mengelola langganan sendiri

## Halaman

```
Current Plan

Invoices

Payment History

Upgrade Plan

Usage
```

Checklist :

```
☐ Semua halaman tersedia
```

# EPIC 33

# BILLINNG AUTOMATION

## Goal

Mengurangi pekerjaan manual

## Task 33.1

## Invoice Generator

Job :

```
Generate Monthly Invoice
```

Checklist :

```
☐ Invoice otomatis
```

## Task 33.2

## Reminder System

Reminder :

```
7 hari sebelum jatuh tempo

3 hari sebelum jatuh tempo

Hari H
```

Checklist :

```
☐ Reminder berjalan
```

## Task 33.3

## Failed Payment Handling

Flow :

```
Failed

↓

Retry

↓

Notify Customer
```

Checklist :

```
☐ Retry berjalan
```

# EPIC 34

# BILLING SECURITY

## Task 34.1

## Financial Audit Log

Table :

```
analytics.audit_logs
```

Catat :

```
Invoice Created

Invoice Paid

Subscription Changed
```

Checklist :

```
☐ Audit log berjalan
```

## Task 34.2

## Permission Review

Permission baru :

```
billing.read

billing.manage

billing.pay
```

Checklist :

```
☐ RBAC billing selesai
```

## Phase 4 Completion Criteria

```
☑ Plans

☑ Subscriptions

☑ Invoices

☑ Payments

☑ Billing Portal

☑ Usage Tracking

☑ Payment Automation
```

## Output Phase 4

Pada akhir fase ini Rusty Amigos memiliki :

```
Rusty Account

Attendix

Billing Platform
```

Dan ini adalah titik yang sangat penting karena sekarang :

```
Customer bisa daftar

Customer bisa menggunakan Attendix

Customer bisa membayar

Customer bisa upgrade
```

tanpa campur tangan manual
