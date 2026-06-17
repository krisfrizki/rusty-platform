# DATABASE SCHEMA

# Struktur Utama Database

A. Users & Auth

B. Projects & Membership

C. Roles & Permissions

D. Trial & Subscription

E. Payment

F. Progress Management

G. Document, Budgeting, Team Activity

## A. Users & Auth

1. users

```sql
id UUID PRIMARY KEY
email TEXT UNIQUE NOT NULL
password_hash TEXT
google_id TEXT
created_at TIMESTAMP DEFAULT now()
updated_at TIMESTAMP
```

2. user_flags

```sql
id UUID PRIMARY KEY
user_id UUID REFERENCES users(id)
has_used_trial BOOLEAN DEFAULT FALSE
```

## B. Projects & Memebership

1. projects

```sql
id UUID PRIMARY KEY
name TEXT NOT NULL
project_code TEXT UNIQUE
owner_id UUID REFERENCES users(id)
created_at TIMESTAMP DEFAULT now()
```

2. project_members

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
user_id UUID REFERENCES users(id)
role_id UUID
joined_at TIMESTAMP DEFAULT now()
```

3. project_join_requests

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
user_id UUID REFERENCES users(id)
status TEXT -- pending, approved, rejected
created_at TIMESTAMP DEFAULT now()
```

## C. Role & Permission System

1. roles

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
name TEXT -- contoh: A, B, C
job_title TEXT -- contoh: Site Manager
is_leader BOOLEAN DEFAULT FALSE
```

2. permission

```sql
id UUID PRIMARY KEY
name TEXT UNIQUE
```

    Contoh isi:

    manage_project
    manage_billing
    manage_document
    manage_progress

3. role_permissions

```sql
id UUID PRIMARY KEY
role_id UUID REFERENCES roles(id)
permission_id UUID REFERENCES permissions(id)
```

## D. Trial System

1. project_trials

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
is_trial BOOLEAN DEFAULT TRUE
trial_start TIMESTAMP
trial_end TIMESTAMP
```

## E. Subscription System

1. subscriptions

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
feature_name TEXT
is_active BOOLEAN
start_date TIMESTAMP
end_date TIMESTAMP
```

2. feature_list (optional tapi recommended)

```sql
id UUID PRIMARY KEY
name TEXT UNIQUE
price INTEGER
```

## F. Payment System

1. transactions

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
user_id UUID REFERENCES users(id)
amount INTEGER
status TEXT -- pending, paid, failed, expired
payment_gateway_id TEXT
created_at TIMESTAMP DEFAULT now()
```

2. transaction_item

```sql
id UUID PRIMARY KEY
transaction_id UUID REFERENCES transactions(id)
feature_name TEXT
price INTEGER
duration INTEGER -- dalam bulan
```

3. payment_logs (optional tapi penting)

```sql
id UUID PRIMARY KEY
transaction_id UUID
payload JSONB
created_at TIMESTAMP DEFAULT now()
```

simpan webhook dari Midtrans

## G. Progress Management

1. work_items

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
name TEXT
weight NUMERIC -- bobot %
price INTEGER
start_date DATE
end_date DATE
created_at TIMESTAMP DEFAULT now()
```

2. work_item_assignments

```sql
id UUID PRIMARY KEY
work_item_id UUID REFERENCES work_items(id)
user_id UUID REFERENCES users(id)
is_pic BOOLEAN DEFAULT FALSE
```

3. work_logs

```sql
id UUID PRIMARY KEY
work_item_id UUID REFERENCES work_items(id)
user_id UUID REFERENCES users(id)
start_time TIMESTAMP
end_time TIMESTAMP
progress_added NUMERIC
description TEXT
created_at TIMESTAMP DEFAULT now()
```

## H. Document System

1. documents

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
title TEXT
created_by UUID REFERENCES users(id)
created_at TIMESTAMP DEFAULT now()
```

2. document_versions

```sql
id UUID PRIMARY KEY
document_id UUID REFERENCES documents(id)
file_url TEXT
version_number INTEGER
uploaded_by UUID REFERENCES users(id)
created_at TIMESTAMP DEFAULT now()
```

3. document_cc

```sql
id UUID PRIMARY KEY
document_version_id UUID REFERENCES document_versions(id)
user_id UUID REFERENCES users(id)
```

## I. Budgeting System

1. budget_items

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
name TEXT
amount INTEGER
created_at TIMESTAMP DEFAULT now()
```

2. expenses

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
description TEXT
amount INTEGER
receipt_url TEXT
created_by UUID REFERENCES users(id)
created_at TIMESTAMP DEFAULT now()
```

## J. Team Acticity System

1. activity_logs

```sql
id UUID PRIMARY KEY
project_id UUID REFERENCES projects(id)
work_item_id UUID REFERENCES work_items(id)
started_by UUID REFERENCES users(id)
start_time TIMESTAMP
end_time TIMESTAMP
description TEXT
created_at TIMESTAMP DEFAULT now()
```

2. activity_participants

```sql
id UUID PRIMARY KEY
activity_id UUID REFERENCES activity_logs(id)
user_id UUID REFERENCES users(id)
```

### notes :

Saat user akses fitur:  
 1. cek trial  
 2. jika trial aktif → allow semua  
 3. jika tidak:  
 cek subscription  
 4. jika aktif → allow  
 5. jika tidak → reject

Idexing (wajib untuk performance)

```
CREATE INDEX idx_project_members_project_id ON project_members(project_id);
CREATE INDEX idx_work_items_project_id ON work_items(project_id);
CREATE INDEX idx_transactions_project_id ON transactions(project_id);
```

Relasi besar (simplified)

```
users
  ↓
projects
  ↓
project_members
  ↓
roles → permissions

projects → trials
projects → subscriptions
projects → transactions

projects → work_items → work_logs
projects → documents → versions
projects → budget_items → expenses
projects → activity_logs
```
