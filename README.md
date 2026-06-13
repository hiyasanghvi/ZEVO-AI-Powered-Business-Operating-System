# ZEVO - Business Management OS

ZEVO is a full-stack business management MVP for owners who need one place to manage businesses, income, expenses, customers, employees, bills, reminders, checklists, khata, inventory, notifications, analytics, invoice previews, and smart assistant suggestions.

## Tech Stack

- Frontend: React, Vite, Tailwind CSS, React Router, Recharts, Framer Motion, React Icons
- Backend: Node.js, Express, MySQL, JWT, bcryptjs, express-validator
- Architecture: routes, controllers, services, repositories, middlewares, validators

## Main Features

- Authentication with JWT login, register, protected profile, and role support
- Business ownership checks so users can only access their own business data
- Business, income, expense, customer, employee, bill, reminder, checklist, notification, khata, inventory, analytics, invoice, and AI assistant modules
- Dashboard with stats, charts, quick actions, and business switching
- Customer khata with credit, debit, and running balance summaries
- Inventory with add, edit, delete, SKU, quantity, and low-stock alerts
- Notification center with persistent mark-read, mark-all-read, and delete actions
- Invoice preview with print/save-as-PDF flow and downloadable invoice HTML
- Rule-based AI assistant suggestions from analytics, reminders, and inventory signals

## Project Structure

```text
client/
  src/
    components/
    context/
    hooks/
    layouts/
    pages/
    routes/
    services/
server/
  src/
    controllers/
    middlewares/
    repositories/
    routes/
    services/
    validators/
database/
  schema.sql
```

## Setup

Install dependencies:

```bash
cd server
npm install

cd ../client
npm install
```

Create `server/.env`:

```env
PORT=5000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=zevo_db
JWT_SECRET=replace_with_a_long_secret
```

Import the database schema:

```bash
mysql -u root -p < database/schema.sql
```

Run the backend:

```bash
cd server
npm run dev
```

Run the frontend:

```bash
cd client
npm run dev
```

Frontend runs on Vite, usually `http://localhost:5173`. Backend runs on `http://localhost:5000` by default.

## Important API Areas

- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/auth/profile`
- `GET /api/dashboard/:businessId`
- `GET /api/analytics/:businessId`
- `GET /api/khata/business/:businessId`
- `GET /api/invoices/:billId/pdf-data`
- `GET /api/inventory/:businessId`
- `GET /api/ai-assistant/:businessId/suggestions`
- `GET /api/notifications/me`
- `PATCH /api/notifications/:id/read`
- `PATCH /api/notifications/read-all`
- `DELETE /api/notifications/:id`

## Frontend Pages

- `/dashboard`
- `/businesses`
- `/income`
- `/expenses`
- `/customers`
- `/employees`
- `/bills`
- `/reminders`
- `/checklists`
- `/analytics`
- `/khata`
- `/notifications`
- `/invoice-pdf`
- `/inventory`
- `/ai-assistant`

## Current Notes

The app is designed as a demoable SaaS MVP. Most modules are connected through the shared Axios API layer in `client/src/services/module.service.js`, and the backend follows the same layered pattern for maintainability.

For invoice PDF, use the `Print / Save PDF` action in the browser print dialog. The download action saves a clean invoice HTML file that can be opened or printed later.
