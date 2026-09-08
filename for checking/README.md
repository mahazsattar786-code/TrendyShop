# Trendy Shop

A database-backed ecommerce storefront for Pakistan with COD checkout, stock-safe ordering, individual discounts, global sales, and a private admin area.

## Setup

Requires Node.js 22.5+ because the server uses Node's built-in `node:sqlite` module.

```bash
cd "for checking"
cp .env.example .env
# edit .env and set a strong ADMIN_PASSWORD and SESSION_SECRET
node server.js
```

Open `http://localhost:8787`. The SQLite database is created at `data/trendyshop.sqlite` on first start. The first run creates two sample products so the storefront is not empty; all future catalogue, order, and sale data is stored in SQLite.

## Admin

Open `/admin`. Credentials come from `ADMIN_EMAIL` and `ADMIN_PASSWORD`. Admin product and settings mutations use a signed server token; no password is shipped to the browser.

## API smoke checks

```bash
curl http://localhost:8787/api/health
curl http://localhost:8787/api/bootstrap
```

Orders are created through `POST /api/orders`. The server recalculates the applicable discount from the original price, checks stock inside a SQLite `BEGIN IMMEDIATE` transaction, inserts order items, and updates `stock` and `sold` atomically. Product price and totals sent by a browser are never trusted.
