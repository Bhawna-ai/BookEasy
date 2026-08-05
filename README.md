# BookEasy 🎯

BookEasy is a full-stack booking web app that simplifies appointment management for restaurants, spas, gyms, and salons. Customers can browse businesses and book services in a few clicks, while businesses can view and manage incoming bookings from a dashboard.

**Live demo:** [book-easy-mu.vercel.app](https://book-easy-mu.vercel.app/index.html)

---

## ✨ Features

- Browse services by category — restaurants, spas, gyms, and salons
- Book an appointment with customer details, date, time, and special requests
- Auto-generated unique booking reference for every booking
- Look up bookings by ID or by customer email
- Track booking status: `pending` → `confirmed` → `completed` / `cancelled`
- Business login and dashboard for managing bookings
- RESTful API built with Express.js
- Health check endpoint for backend monitoring

---

## 🧰 Tech Stack

| Layer      | Technology |
|------------|------------|
| Frontend   | HTML, CSS, JavaScript (vanilla) |
| Backend    | Node.js, Express.js |
| Database   | MongoDB (via Mongoose) |
| Tooling    | dotenv, cors, nodemon, pnpm |

---

## 📁 Project Structure

```
BookEasy/
├── backend/
│   ├── models/
│   │   └── Booking.js       # Mongoose schema for bookings
│   ├── server.js            # Express app & API routes
│   ├── package.json
│   └── .gitignore
├── frontend/
│   ├── index.html           # Landing page
│   ├── restaurants.html     # Restaurant listings
│   ├── spas.html            # Spa listings
│   ├── gyms.html            # Gym listings
│   ├── salons.html          # Salon listings
│   ├── booking.html / .js / .css   # Booking form & logic
│   ├── business-login.html / .css  # Business login
│   ├── dashboard.html / .css       # Business dashboard
│   └── style.css / services.css
└── pnpm-lock.yaml
```

---

## ⚙️ Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v16+
- [pnpm](https://pnpm.io/) (or npm/yarn)
- A MongoDB database — [MongoDB Atlas](https://www.mongodb.com/atlas) or a local instance

### 1. Clone the repository

```bash
git clone https://github.com/Bhawna-ai/BookEasy.git
cd BookEasy
```

### 2. Install backend dependencies

```bash
cd backend
pnpm install   # or npm install
```

### 3. Configure environment variables

Create a `.env` file inside `backend/`:

```env
MONGO_URI=your_mongodb_connection_string
PORT=3000
```

### 4. Run the backend server

```bash
pnpm start     # production
pnpm dev       # development, with nodemon auto-reload
```

The API will be available at `http://localhost:3000/api`.

### 5. Run the frontend

The `frontend/` folder is static HTML/CSS/JS. Open `frontend/index.html` directly in a browser, or serve it with any static file server (e.g. the VS Code "Live Server" extension). By default the frontend is configured to call a deployed API — update the `API_BASE_URL` constant in `frontend/booking.js` to point at your local backend (`http://localhost:3000/api`) if you want to test end-to-end locally.

---

## 🔌 API Reference

Base URL: `/api`

| Method | Endpoint                          | Description                          |
|--------|------------------------------------|---------------------------------------|
| GET    | `/health`                          | Health check for the backend          |
| GET    | `/bookings`                        | Get all bookings                      |
| GET    | `/bookings/:id`                    | Get a single booking by ID            |
| POST   | `/bookings`                        | Create a new booking                  |
| PATCH  | `/bookings/:id/status`             | Update a booking's status             |
| DELETE | `/bookings/:id`                    | Delete a booking                      |
| GET    | `/bookings/customer/:email`        | Get all bookings for a customer email |

### Booking object

```json
{
  "customerName": "Jane Doe",
  "customerEmail": "jane@example.com",
  "customerPhone": "9999999999",
  "serviceType": "spa",
  "businessName": "Serenity Spa",
  "businessLocation": "Downtown",
  "serviceDetails": "Deep tissue massage",
  "bookingDate": "2026-08-10",
  "bookingTime": "14:00",
  "numberOfGuests": 1,
  "specialRequests": "Near window",
  "status": "pending",
  "bookingReference": "SPA-LX3K9F-A1B2"
}
```

`serviceType` must be one of `restaurant`, `spa`, `gym`, `salon`. `status` must be one of `pending`, `confirmed`, `cancelled`, `completed`. `bookingReference` is generated automatically on creation.

---

## 🚀 Deployment

- **Frontend:** deployed on [Vercel](https://vercel.com)
- **Backend:** deployed on [Render](https://render.com)

---

## 🤝 Contributing

Contributions are welcome! Fork the repo, create a feature branch, and open a pull request.

```bash
git checkout -b feature/your-feature
git commit -m "Add your feature"
git push origin feature/your-feature
```

## 📄 License

ISC
