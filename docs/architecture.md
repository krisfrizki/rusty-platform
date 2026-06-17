# SOFTWARE ARCHITECTURE

## FRONTEND

```
Frontend

├── Rusty Website
├── Rusty Account
├── Attendix
└── Flexora
```

Masing-masing frontend terpisah

## BACKEND

```
Backend

├── Auth Module
├── Organization Module
├── Billing Module
├── Notification Module
├── Attendix Module
└── Flexora Module
```

(Modular Monolith)

- 1 Repository
- 1 Deployment

# DATABASE

```
PostgreSQL

├── rusty_auth
├── attendix
├── flexora
├── billing
└── analytics
```

1 PostgreSQL Server, tetapi domain dipisah
